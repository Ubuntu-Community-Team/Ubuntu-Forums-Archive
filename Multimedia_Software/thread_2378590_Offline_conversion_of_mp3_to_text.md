---
title: "Offline conversion of mp3 to text"
date: 2017-11-24
forum: Multimedia Software
---

### Post by oygle on 2017-11-24
I have hundreds of MP3 files that are from an online teaching course. There are very strict rules in regards to copyright,etc. In short, these files cannot be uploaded and are for personal use only, offline.

I would like to convert the audio to text, for additional personal training and education, research,etc. In summary, a transcription of all the audio files.

Everything I have looked at is either uploading the file to a site for conversion, or tools like Google API and similar, that require to process the file contents on their site. Yet the requirements to do this is all offline.

Are there any tools or software that I can run offline to convert the audio to text ? On a linux computer, not Windows,etc.

---

### Post by Yellow Pasque on 2017-11-25
Have you tried using 'transcriber'? (Install libsox-fmt-mp3 for mp3 support)

---

### Post by oygle on 2017-11-25
> **Temüjin said:**
> Have you tried using 'transcriber'? (Install libsox-fmt-mp3 for mp3 support)

Thanks, but it doesn't provide any automatted transcription. From file:///usr/share/tcltk/transcriber/doc/en/user.html - > Type in the transcription; it will automatically appear in the text editor and in the segmentation under the signal

---

### Post by Yellow Pasque on 2017-11-25
Oh, sorry. I was shooting in the dark.

---

### Post by oygle on 2017-11-25
> **Temüjin said:**
> Oh, sorry. I was shooting in the dark.

No worries. the word 'transcribe' can mean manual or automatted.  :)

---

### Post by oygle on 2017-12-01
I have found some software at [https://pypi.python.org/pypi/SpeechRecognition/](https://pypi.python.org/pypi/SpeechRecognition/) , which seems promising.

Discussion in regards to python versions at [https://ubuntuforums.org/showthread.php?t=2379169](https://ubuntuforums.org/showthread.php?t=2379169)

---

### Post by oygle on 2018-01-15
Well, a month or so later and trialling different tools. The bottom line is that Google/Youtube is definitely the most accurate. However, there is nothing pertaining to that, that is available offline. They require that you upload files to their cloud servers. IBM are the same, and the offline tools that did work okay, didn't provide the accuracy needed.

Mozilla have a project called [DeepSpeech]("https://github.com/mozilla/DeepSpeech"), yet nothing there for offline. There is also the [Kaldi Speech recognition]("http://kaldi-asr.org/")

Have recently discovered 2 tools which are both based on the Mozilla DeepSpeech engine and are a local web server:

* A testing server for a speech to text service based on mozilla deepspeech - [https://github.com/MainRo/deepspeech-server](https://github.com/MainRo/deepspeech-server)
* Mozilla deepspeech server implemented in django - [https://github.com/ashwan1/django-deepspeech-server](https://github.com/ashwan1/django-deepspeech-server)

hth

---

### Post by protivinsky on 2018-02-25
Thanks for the update, I was just searching for exactly the same. I would prefer an offline solution, but it is not crucial for me, so I guess I will go with Google.

---

### Post by oygle on 2018-02-25
DeepSpeech is only alpha and not ready for any serious transcribing yet. Kaldi will do offline transcribing, however if you want to use it, you need to be prepared for compiling just to install it, and then there are no models to do some testing. There are quite a few models to download from the Kaldi site, and then you have to build them.

Whilst it sounds like a lot of work to even test Kaldi, the website has plenty of documentation and there is a kaldi-help group on Google - [https://groups.google.com/forum/#!forum/kaldi-help](https://groups.google.com/forum/#!forum/kaldi-help)

I was given an i5 laptop with 4 Gb ram and 500Gb HDD, and whilst it is not that powerful, I use that for all the speech recognition compiling, building and testing. I have often seen the CPU at 100%, most of the ram being used and swap also. So these speech recognition engines are very resource hungry.

---

### Post by mobius+ on 2018-02-27
Thanks guys for this thread...I didnt even know, that there are speech conversion tools for free out there. I have also some audio files recorded from some courses....gonna try to convert them too but I think the quality is bad to recognize it. Anyways thanks for this topic...maybe it will save me a lot of time.

---

### Post by oygle on 2018-02-27
> **mobius+ said:**
> Thanks guys for this thread...I didnt even know, that there are speech conversion tools for free out there.

There is also [CMUSphinx Open Source Speech Recognition]("https://cmusphinx.github.io/")

> **mobius+ said:**
>  I have also some audio files recorded from some courses....gonna try to convert them too but I think the quality is bad to recognize it. Anyways thanks for this topic...maybe it will save me a lot of time.

When I was testing a few audios, I noticed a small audio wouldn't even result in any transcription. It was the audio volume. So I used ffmpeg to increase the volume, by a decibel factor. I've come across a great tool for tweaking those audios where the quality is poor. Lots of 'noise' in some audios we have and as well as making it difficult to listen to, the transcription will have a higher "WER" (Word Error Rate) if there is poor quality. The tool is available via Synaptic and is called [Audacity]("https://www.audacityteam.org/")

---

