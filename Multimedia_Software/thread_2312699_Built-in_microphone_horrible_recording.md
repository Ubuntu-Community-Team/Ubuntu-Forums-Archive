---
title: "Built-in microphone horrible recording"
date: 2016-02-06
forum: Multimedia Software
---

### Post by ma__ska on 2016-02-06
I've had Ubuntu 14.04 LTS 32-bit (GNOME) for a lot of time and it's been working fine, no problem at all (about this issue I'm gonna explain). Until a few weeks ago I've been recording myself playing the guitar using the built-in microphone of my laptop (Toshiba Satellite L850-1XN) and everything has been fine. But then I got an audio interface (Behringer Guitar link UCG102) to record the guitar directly and with good quality (and this works fine). But now when I want to record something with the built-in microphone it sounds really crappy (recorded test below) and is impossible to understand anything, which I mean it's not a noise reduction problem. 
I have tried reinstalling ALSA and installing other recording software, but it seems to do the same. Also, I've tried with Windows 7 and Zorin OS 9 and worked fine in both, so apparently it's not a hardware problem. 
If it's of any use, I followed this guide to set all the software needed and record succesfully: [LINK]("http://akshathabel.blogspot.in/2013/04/electric-guitars-on-ubuntu-1304.html")
Link to a sample I just recorded now: [LINK]("https://instaud.io/iOF")

Thank you very much, I'll be glad to answer any question needed. :D

---

### Post by ma__ska on 2016-02-06
OP replying just to close this thread.

Okay, so you know that usual thing that when you ask something, then you find your answer by yourself? Well I needed less than 5 minutes though I've been dealing with that for a long time.

To solve this I opened alsamixer in a terminal, press F4 and turn down the Internal Mic Boost and Mic Boost as well, both down to 0. I still don't know why it happened but there it was, so thread closed.

I hope it can be helpful to someone.

---

