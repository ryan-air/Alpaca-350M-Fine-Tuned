# Alpaca-350M-Fine-Tuned
Professional work-related project

In this project, I have provided code and a Colaboratory notebook that facilitates the fine-tuning process of an Alpaca 350M parameter model originally developed at [Stanford University](https://crfm.stanford.edu/2023/03/13/alpaca.html). The particular [model](https://huggingface.co/RootYuan/opt-350m-alpaca) that is being fine-tuned has around 350 million parameters, which is one of the smaller Alpaca models (smaller than my previous fine-tuned model). 

The model uses low-rank adaptation [LoRA](https://huggingface.co/docs/peft/task_guides/token-classification-lora#:~:text=Low%2DRank%20Adaptation%20(LoRA),that%20are%20trained%20and%20updated.) to run with fewer computational resources and training parameters. We use [bitsandbytes](https://huggingface.co/blog/4bit-transformers-bitsandbytes) to set up and run in an 8-bit format so it can be used on colaboratory. Furthermore, the [PEFT](https://huggingface.co/blog/peft) library from HuggingFace was used for fine-tuning the model. 

Hyper Parameters:
1) MICRO_BATCH_SIZE = 4  (4 works with a smaller GPU)
2) BATCH_SIZE = 32
3) GRADIENT_ACCUMULATION_STEPS = BATCH_SIZE // MICRO_BATCH_SIZE
4) EPOCHS = 2  (Stanford's Alpaca uses 3)
5) LEARNING_RATE = 2e-5  (Stanford's Alpaca uses 2e-5)
6) CUTOFF_LEN = 256  (Stanford's Alpaca uses 512, but 256 accounts for 96% of the data and runs far quicker)
7) LORA_R = 4
8) LORA_ALPHA = 16
9) LORA_DROPOUT = 0.05

Credit for Original Model: [Qiyuan Ge](https://huggingface.co/RootYuan)

Fine-Tuned Model: [RyanAir/Alpaca-350M-Fine-Tuned](https://huggingface.co/RyanAir/Alpaca-350M-Fine-Tuned) (HuggingFace)

