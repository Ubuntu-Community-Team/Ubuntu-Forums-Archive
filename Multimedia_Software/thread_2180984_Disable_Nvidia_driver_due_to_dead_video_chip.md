---
title: "Disable Nvidia driver due to dead video chip"
date: 2013-10-15
forum: Multimedia Software
---

### Post by Deanobats on 2013-10-15
Hi there,
I've got a Dell D830 latitude laptop which worked fine as a dual boot with Ubuntu 13.04 and Windows 7. After a time, I developed a flickering screen and eventually nothing as the Nvidia Quadro NVS 140M  chip died (a common problem with this laptop). However, the laptop does appear to have an onboard intel chipset that would at least work the laptop screen if not an external monitor. Neither windows nor Ubuntu would boot after the video chip died, but I got into windows in safe mode, removed the Nvidia driver and the backup intel chipset kicked in and I have a functioning windows laptop again. BUT, still can't get into Ubuntu, get as far as the login and everything freezes. Is there a way in to Ubuntu to remove the Nvidia drivers so that I can use the Intel chipset? I don't know if it will support OpenGL or anything, so might have to use a fallback video option, but at least I could get Ubuntu back.

Ta!

p.s. If this question sounds like garbage I'm afraid it reflects my technical know-how!

---

### Post by papibe on 2013-10-15
Hi Deanobats.

You need a terminal or a text mode session first.

There are 2 options:
[LIST]
[*]boot into recovery mode, and then select a root prompt, or
[*]boot normally, wait a few seconds before the GUI crashes, then press Ctrl+Alt+F1 and login with your user.
[/LIST]
Once you have a prompt remove all the Nvidia packages by running:
```
sudo apt-get purge nvidia-*
```
Then remove the Xorg config file:
```
sudo rm -rf /etc/X11/xorg.conf
```
Then reboot:
```
sudo reboot
```
If the machine still tries to use the Nvidia chip, try getting into your BIOS and see if you can disable the Nvidia card there.

I hope it helps. Let us know how it goes.
Regards.

---

### Post by Deanobats on 2013-10-15
That sounds promising, I'll give it a go! I know I can't disable the chip in BIOS, so I cured it in Windows by disabling the Nvidia driver. I'll try this and let you know how it goes.

Wow, that worked, thanks so much for that! I seem to have lost Unity, but the Gnome desktop still functions. Brilliant!

---

### Post by papibe on 2013-10-15
Great! :D

Please mark the thread as SOLVED when you have chance ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Come here often and have fun.
Regards.

---

### Post by Deanobats on 2013-10-16
I got Unity back by opening a terminal and opening compiz by typing ccsm then enabling OpenGL, then the Unity plug-in. Not sure if I'm now running the Intel onboard graphics or the Nvidia chip but without the Nvidia driver issue, but I can get multiple monitors and everything is fine. It's a little slower than it was, but hey, it works!

---

