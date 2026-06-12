---
title: "Sound get choppy and cuts out in full-screen games"
date: 2009-11-14
forum: Multimedia Software
---

### Post by d1ng3r on 2009-11-14
I am runny Karmic on an x64 machine

The sounds works perfectly in gnome, but when I run full screen applications like openarena or ufo alien invasion the sound is very choppy and then it cuts out completely. When I try to exit the game the system does not respond and I need to kill the game

---

### Post by wil on 2009-12-01
I have the same problem and I am unable to find a solution to this.

---

### Post by cikson on 2009-12-03
Same here with Battle for Wesnoth, America's Army, Nexuiz, World of Padman

---

### Post by NoJoso on 2010-01-13
I am also having this problem. I was able to get the sound to work temporarily by refreshing the drivers as described here:  [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

The command is:
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

After running this command you'll need to reboot. It has mostly worked but i sometimes the problem comes again... i don't know what triggers it. 

Any ideas??

---

### Post by NoJoso on 2010-01-14
found solution posted by: the user lessmemorelove in [this]("http://ubuntuforums.org/showthread.php?t=1306592") thread solved it for me.

I really only followed step four:
4. use synaptic and make sure you have libsdl1.2debian-pulseaudio installed

and i was able to play may full screen games with sound and exit without killing the process.

---

### Post by cikson on 2010-03-03
Thanks this works, except Java applications like Puzzle Pirates.

> **NoJoso said:**
> found solution posted by: the user lessmemorelove in [this]("http://ubuntuforums.org/showthread.php?t=1306592") thread solved it for me.

I really only followed step four:
4. use synaptic and make sure you have libsdl1.2debian-pulseaudio installed

and i was able to play may full screen games with sound and exit without killing the process.

---

