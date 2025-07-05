# Run the Full DeepSeek-R1-0528 Model Locally with Ollama & Open Web UI

*Harness the full power of DeepSeek’s R1 reasoning model on your own hardware—even in a quantized form.*

DeepSeek-R1-0528 is a cutting-edge reasoning model that, in its raw form, demands a staggering **715 GB** of disk space—one of the largest open-source LLMs you can run today. Thanks to Unsloth’s advanced quantization (IQ1_S, a 1.78-bit scheme), you can shrink it down to **162 GB**—an 80 % reduction—making local experimentation far more approachable. In this guide, we’ll walk through:

1. Installing Ollama and Open Web UI  
2. Downloading and configuring the 1.78-bit quantized DeepSeek-R1-0528  
3. Running the model with GPU + CPU and, if needed, CPU-only  
4. Troubleshooting common hiccups  

---

## Why Quantize?

Quantization trades a bit of precision for dramatically smaller model files and lower memory footprints. For DeepSeek-R1-0528:

- **Original size:** 715 GB  
- **Quantized (IQ1_S):** 162 GB  
- **Speed on 24 GB GPU + 128 GB RAM:** ~5 tokens/sec  
- **CPU-only (64 GB RAM):** ~1 token/sec  

This lets you explore reasoning at scale even without an entire GPU cluster—though you’ll see slower performance on CPU alone.

---

## Step 0: Ensure Your System Is Ready

| Resource            | Minimum                        | Optimal                          |
|---------------------|--------------------------------|----------------------------------|
| **Disk**            | 200 GB free                    | 250 GB+                          |
| **RAM**             | 64 GB (CPU-only)               | 180 GB unified RAM + VRAM        |
| **GPU**             | 24 GB (RTX 4090, A6000)        | Multiple 24 GB cards             |
| **Network**         | Fast, stable internet          | —                                |

---

## Step 1: Install Ollama

Ollama runs LLMs locally via a simple server interface. On Ubuntu:

```bash
sudo apt-get update
sudo apt-get install pciutils -y
curl -fsSL https://ollama.com/install.sh | sh

# verify
ollama version


