# FIne-Tuning OpenAI's Whisper Model for Multilingual ASR

Whisper is a pre-trained model for automatic speech recognition (ASR) published in September 2022 by the authors Alec Radford et al. from OpenAI. Unlike many of its predecessors, such as [Wav2Vec 2.0](https://www.google.com/url?q=https%3A%2F%2Farxiv.org%2Fabs%2F2006.11477) , which are pre-trained on un-labelled audio data, Whisper is pre-trained on a vast quantity of labelled audio-transcription data, 680,000 hours to be precise. This is an order of magnitude more data than the un-labelled audio data used to train Wav2Vec 2.0 (60,000 hours). What is more, 117,000 hours of this pre-training data is multilingual ASR data. This results in checkpoints that can be applied to over 96 languages, many of which are considered low-resource.

When scaled to 680,000 hours of labelled pre-training data, Whisper models demonstrate a strong ability to generalise to many datasets and domains.

![whisper_architecture](https://github.com/notinrange/University-Living-Task2/assets/88238469/a5da4555-f7a6-45ca-95f7-d9d65b5e3cd6)

The Whisper architecture is a simple end-to-end approach, implemented as an encoder-decoder Transformer. Input audio is split into 30-second chunks, converted into a log-Mel spectrogram, and then passed into an encoder. A decoder is trained to predict the corresponding text caption, intermixed with special tokens that direct the single model to perform tasks such as language identification, phrase-level timestamps, multilingual speech transcription, and to-English speech translation.

## The name Whisper follows from the acronym “WSPSR”, which stands for “Web-scale Supervised Pre-training for Speech Recognition”.

![asr-details-desktop (1)](https://github.com/notinrange/University-Living-Task2/assets/88238469/699a6f4d-9225-401d-a560-a6b35307df30)

# Steps of Deployment

1. I used my hugging face API Token in Read mode by loging with my account.
2. Used common_voice multilingual speech to text [dataset](https://huggingface.co/datasets/legacy-datasets/common_voice) for analysis and Fine Tuniing Whisper Small model of OpenAI.

3. For preprocessing dataset I drop unecessary column from dataset.

4. After that I defined data_collator function for further preprocessing, For Evaluation I imported Word Error Rate Metric (WER).

5. Defining Training Configuration with parameters like learning_rate, max_steps which you can increase to improve performance of model, save_steps, eval_steps, push_to_hub.

6. Training Model with our common_voice train and test dataset, Defining Model kwags means arguments, pushing my Finetuned model to hugging face hub for futher development and, Defining pipeline of model and defining iface interface of speech to text model


[Link of Colab NOTEBOOK](https://colab.research.google.com/drive/1raY0GIXTAapyL1pxyg90O1wS_5VkcNFS?usp=sharing)
[Deployment Link](https://huggingface.co/spaces/notinrange/University_Living_Task2)
