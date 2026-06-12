---
title: "Changed Video Driver, Now Cant Boot"
date: 2009-04-04
forum: Multimedia Software
---

### Post by iheartubuntu on 2009-04-04
Last night I was 'tinkering' with my video drivers and downloaded ATI's latest driver for my video card (ATI Radeon X300) from their website and now the computer gets garbled video and lines on the screen after running through the system check on boot up. Its a mostly black screen with some bars and lines. Ive tried going into recovery menu and trying xfix, but it did nothing. Im not quite sure what to do next. Does anyone have any tips how I can restore to a different video driver? Thanks for any tips!

---

### Post by iheartubuntu on 2009-04-04
Can I boot into a LiveCD and somehow fix the laptop?

---

### Post by iheartubuntu on 2009-04-05
OK, just checked. Im able to bootup a liveCD no problem. I just need to figure out how I can reinstall an appropriate driver back onto my laptop.

---

### Post by iheartubuntu on 2009-04-05
I managed to rewrite my xorg.conf file to one that was working fine... but still the same prob. When booting into Ubuntu I get a mostly black screen. Please help :( I have no idea how to fix this.

---

### Post by iheartubuntu on 2009-04-05
--PROBLEM SOLVED--

I went here...

[http://ubuntuforums.org/showthread.php?t=1114048&highlight=reinstall+video+driver+terminal](http://ubuntuforums.org/showthread.php?t=1114048&highlight=reinstall+video+driver+terminal)

and followed the last post by "zika". I plugged in a hard wire connection and he gave some code that I tried out in recovery mode (at prompt)....

```
sudo apt-get update
sudo /usr/share/ati/fglrx_unistall.sh (I might made a typo here, do not have that file any more)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati
sudo apt-get remove --purge xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install --reinstall libgl1-mesa-glx
sudo apt-get install --reinstall libgl1-mesa-dri
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get upgrade
```

Worked fine, booted right into my laptop! Thank you so much!

---

