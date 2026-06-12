---
title: "Can't switch sound cards reliably"
date: 2008-06-01
forum: Multimedia Software
---

### Post by CRISM on 2008-06-01
I have two sound cards, an SBLive pci card and a built-in Mboard "card". Both have always worked fine, and I switch between them for different tasks. I recently changed to Hardy from Gutsy, and a strange problem has developed. I can no longer reliably switch! I have always used the command: sudo asoundconf set-default-card xxx and where xxx is the card I want to use. Now, the command doesn't always work. Seems to work for aplay, but not for Totem. When I double-click a sound file, totem (my default player) starts up, but the sound continues to come from Live even when I try to switch.

---

### Post by markbuntu on 2008-06-01
I had a similar problem and I solved it by getting asoundconf-gtk to select the alsa default sound card. 

I know it is just a gui for asoundconf but it seemed to make a difference because the first time I opened it it had pulseaudio listed as the default rather than one of my sound cards. Then I set all my sound options to alsa.
If you are going to use alsa as your default you should check if you have the following:

alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

---

### Post by rrob on 2010-01-12
I make script to switch it from command line.
Here [http://blog.robinpecha.cz/command-line-cli-switch-for-switching-default-sound-card-in-ubuntu-pulse-audio/](http://blog.robinpecha.cz/command-line-cli-switch-for-switching-default-sound-card-in-ubuntu-pulse-audio/)

---

