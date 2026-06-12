---
title: "Audio on USB Live 2 freezes mouse / keyboard on NUC"
date: 2015-03-19
forum: Multimedia Software
---

### Post by axe87 on 2015-03-19
I have a hauppage USB Live 2 USB video capture stick which I had working on my old Ubuntu box. Having moved to a NUC (D54250WYKH) it seems as though the audio device causes the NUC to freeze. I am/was running Ubuntu 14.10 on both boxes.
 
I can stream video with programs such as qv4l2 but as soon as I try and adjust the audio even by clicking on the device in Sound Settings my system freezes. The only way out is to power off and reboot. The only indication of an error is the following message:

ALSA lib pcm_dmix.c:961:(snd_pcm_dmix_open) The dmix plugin supports only playback stream

alsa: Cannot open capture device dmix:CARD=Cx231xxAudio,DEV=0: Invalid argument

I get a similar message when I use my WebCam but this doesn't cause the machine to freeze.

I'd really like to get this fixed so that I can finish digitizing my home VHS videos.

It seems like the following question is referring to the same problem, but there's no indication of the poster's h/w, so I'm not sure if this is a NUC specific problem.

[http://askubuntu.com/questions/589347/ez-grabber-2-usb-2-0-video-capture-card-audio-video-together-cause-ubuntu](http://askubuntu.com/questions/589347/ez-grabber-2-usb-2-0-video-capture-card-audio-video-together-cause-ubuntu)

---

