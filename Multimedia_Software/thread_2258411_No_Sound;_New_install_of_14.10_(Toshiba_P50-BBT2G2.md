---
title: "No Sound; New install of 14.10 (Toshiba P50-BBT2G22)"
date: 2014-12-27
forum: Multimedia Software
---

### Post by taserian on 2014-12-27
I've installed Ubuntu 14.10 on a Toshiba Satellite P50-BBT2G22, but I can't get the sound to work. I've kept the Windows 8 partition alive for warranty purposes, and sound works perfectly there. Using "ubuntu-bug -s audio" in the Terminal, it said that PulseAudio was not configured to use the card I want output from (Built-In Audio - HDA Intel HDMI), but pavucontrol hasn't helped anyway (in pavucontrol, under Configuration tab, all options under Built-In Audio claim that they are unplugged [ 3 options say "Digital Stereo (HDMI) Output (unplugged)", 3 more options say "Digital Surround 5.1 (HDMI) output (unplugged)" and an "Off" option]).

Data on alsainfo and other files are at [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1404589]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1404589") . I submitted it as a bug a few days ago, but it hasn't had any action since then.

Going through the troubleshooting at [https://help.ubuntu.com/community/So...otingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

I came across this (during Step 3):

[FONT=courier new]!!ALSA Version
!!------------

Driver version: k3.16.0-29-generic
Library version: 1.0.28
Utilities version: 1.0.28[/FONT]

Is it a problem that they're not all the same?

---

