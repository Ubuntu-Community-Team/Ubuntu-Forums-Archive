---
title: "skippiung audio/video when mouse NOT moving"
date: 2013-08-07
forum: Multimedia Software
---

### Post by feardotcom on 2013-08-07
So i have a very weird problem. The sound/video skips when the mouse is not moving, e.g. constantly move the mouse the video and audio plays fine absolutely no issues. I'm running 13.04. I've been struggling with this issue for like 2 months. I have tried installing the drivers for my mouse. Razer mouse. It does not fix my issue. The issue still persists even after the mouse has been unplugged. I thought maybe the video drivers were the problem as my video and audio is run through hdmi, so i upgraded to nvidia 313, and no luck. I tried running audio through analog with a pair of headphones and still no luck. I did not have any issues with this prior to 13.04.

---

### Post by feardotcom on 2013-08-07
Ok, so i decided to get on askubuntu.com to ask my question and it came up with someone who had the same problem. The solution to this problem is to uninstall pulse audio. But, when you do this the hdmi audio output stops working. So i had to run a cable from my audio jack on the pc to the rca jack on my reciever, which is a bit of a pain, but it works. 

This guide worked for me [http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/](http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/)

---

