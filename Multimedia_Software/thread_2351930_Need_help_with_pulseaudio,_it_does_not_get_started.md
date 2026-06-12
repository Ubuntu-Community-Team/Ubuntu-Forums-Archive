---
title: "Need help with pulseaudio, it does not get started on login"
date: 2017-02-07
forum: Multimedia Software
---

### Post by bachtobach on 2017-02-07
I have a strange issue with pulseaudio - it does not get started when I login. I think I have narrowed down the problem (or perhaps just a symptom), it seems that ~/.pulse/client.conf gets overwritten with "autospawn = no". I don't know why this is happening, I have manually uncommented /etc/pulse/client.conf so autospawn is set to yes but something is changing this value in my local config. 

I'm a bit confused how pulseaudio is supposed to be started, I was at first under the impression it was a systemd service but after some research it seems that's not the case. So show KDE start pulseaudio automatically? 

How can I narrow down what is stopping pulseaudio from start and/or what is causing the ~/.pulse/client.conf to change? 
I have created a new user and logged in with that as a test and pulseaudio gets started, and have tried to narrow down anything in my normal user configs that might be causing this but I have not managed to find the problem. 
Any help at all would be greatly appreciated, this is driving me crazy and I have spent hours trying to solve it.

---

### Post by Autodave on 2017-02-08
Try going into Settings -> Session & Startup. Make sure that PulseAudio is ticked there.

---

