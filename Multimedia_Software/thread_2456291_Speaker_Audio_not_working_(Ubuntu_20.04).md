---
title: "Speaker Audio not working (Ubuntu 20.04)"
date: 2021-01-08
forum: Multimedia Software
---

### Post by adv8 on 2021-01-08
Hey guys,

I'm having a problem, where my speakers work in windows 10 (I have both wd10 and ubuntu dual booted) but don't work in Ubuntu 20.04. I have to plug in wired headphones to hear anything. I know the hardware works , because I can hear perfectly in Windows. I tried everything from installing audio software to modifying config files. Nothing works. I tried everything the internet has to offer but nothing works. No bluetooth devices are connected, nothing. What is the issue here? Do I need to update something?

Thanks in advance,

Advait

---

### Post by simon-webb on 2021-01-19
Hi Advait.

You probably don't need to update anything: the fact that you're able to hear audio through the headphones suggests that the kernel has the necessary drivers to make use of your audio hardware, so I think it's probably just that the mixer is not set to the correct output. Have you had a poke around in the audio mixer settings? I've had a few systems (especially when there are lots of outputs, like wired headphones, surround speakers via receiver/HDMI, and bluetooth outputs as well) where pulseaudio hasn't been clever enough to figure out which output I'm using. If you've tried all the output devices in the list (and do try all of them, starting with the most likely ones but trying all the others too...because again, the fact that your headphones work shows that your audio hardware is successfully sending audio to that output, so ought to be able to send it to others), another thing you could try is alsamixer to fiddle with the outputs and levels before they get to pulseaudio. The reason this might work is that it's actually possible you have multiple physical audio devices: for example, your speakers might be connected to something like "HDA NVidia" (audio hardware in your video card, if the sound's going to the speakers through a cable plugged into that card), while the headphones might be using something like "HDA Intel" if you've plugged them into a 3.5mm jack that connects directly to your motherboard.

---

