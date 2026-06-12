---
title: "No video with  GeForce 6800 GS"
date: 2006-03-01
forum: Multimedia &amp; Video
---

### Post by sanjeevdas on 2006-03-01
Tried out the breezy live CD today with my new system (both AMD64 and 32 bit versions). Couldn't get video to work. At first a blank screen and then a screen with blue vertical bars.

I have an eVGA GeForce 6800 GS (256MB) PCI-E.

Anyone have the same problem?

thx.

---

### Post by Aewheros on 2006-03-02
You need to install the nvidia drivers and configure xorg. When you see the messed up screen, switch to text mode (ctrl+alt+F1), login, and write the following commands.
```
sudo apt-get install nvidia-glx
sudo apt-get nvidia-settings
sudo nvidia-glx config enable
sudo dpkg-reconfigure xserver-xorg
```
If you don't know what to select/type in the configuration wizard just go by the default by pressing enter without changing anything. Then go back to graphical mode (ctrl+alt+F7) and restart it (ctrl+alt+backspace), or just reboot.

---

