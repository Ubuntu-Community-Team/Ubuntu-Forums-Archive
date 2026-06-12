---
title: "Stream sound from Ubuntu Server to Windows"
date: 2010-06-20
forum: Multimedia Software
---

### Post by GraysonPeddie on 2010-06-20
Hi. I have configured PulseAudio with an MPD [system-wide](http://wiki.archlinux.org/index.php/PulseAudio#System-wide_daemon) as I want to run PulseAudio without an X-Window Server environment, as I'm going to let my netbook act as a "wireless speaker" for espeak to speak out; thus, minimizing the expense of getting a "whole-apartment audio equipment." This is something that I can figure this out unless I need help, as I have configured PulseAudio to act as a sender by having a separate RTP stream when I configure it in a VNC client.

Plus, I want my Windows Vista 64-Bit machine to receive the output from PulseAudio. I did download the [Windows version of PulseAudio from Cendio](http://www.cendio.com/pulseaudio/), but I have problems getting PulseAudio to work, even if I added load-module module-rtp-recv to default.pa in the PulseAudio directory that I installed in PulseAudio directory. I get error after error messages when I run pulseaudio.exe, so it looks to me that it's not going to work anyway, so I deleted the entire PulseAudio directory. It said something about entropy that I did not know anything about it.

So anyway, is there some sort of a server program that listens to PulseAudio output and then send that audio to the client? The server program in the Ubuntu Server (that I plan to use as a sender) must be able to run without an X-Window environment. Is this possible?

I tried to do a search when it comes to streaming audio from Linux to Windows, but the Google search result came up with "Streaming audio/sound from Windows to Linux" which did not turn out very well for me. :( As a result, I have no luck with doing a Google search for what I'm looking for.

In short, is there some kind of daemon that listens for audio and distribute the sound to Windows? It will be for my internal network only.

---

### Post by Pessulus on 2010-07-26
Same problem!

---

