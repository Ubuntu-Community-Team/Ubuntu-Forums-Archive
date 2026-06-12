---
title: "Nvidia GeForce GT740m: System running in low graphics-mode"
date: 2013-09-13
forum: Multimedia Software
---

### Post by SchrodingerCat on 2013-09-13
Hi,
i just installed ubuntu and everything was working fine. After installining Nvidia Drivers (i have a [COLOR=#000000][FONT=Verdana]Nvidia [/FONT][/COLOR]**GeForce GT740m**[COLOR=#000000][FONT=Verdana] [/FONT][/COLOR])
i get a message when i boot the laptop "System running in low graphics-mode" and it seems to get stucked. 
Any help?
Thanks

---

### Post by SchrodingerCat on 2013-09-13
Hi,
i just got a new laptop and i have few problems. First i installed ubuntu and i intalled the Nvidia accelerator. After that i was not able to 
log in anymore because the screen was set on low quality. Then i installed ubuntu again. The problem now is that
when i start ubuntu..i have to insert the password but the screen is black..and if i dont  touch the pc for 5 minutes it goes in 
black scrren saying " timed out waiting for DP idle pattern and i can t log in anymore.
thanks

---

### Post by oldfred on 2013-09-13
Please do not start duplicate threads.  If issue is not video driver related then a sperate thread may be appropriate.
Threads merged.

Is this sytem a dual video system? Nvidia Optimus?

---

### Post by Mephisto Pheles on 2013-09-13
What version of the nvidia drivers are you on?

---

### Post by Bucky Ball on 2013-09-13
*Thread moved to **Multimedia & Video**.*

---

### Post by SchrodingerCat on 2013-09-13
Yes i have a dual video system with Intel and [COLOR=#000000][FONT=Verdana]Nvidia [/FONT][/COLOR]**GeForce GT740m **but i am not sure which drivers i am using...

---

### Post by oldfred on 2013-09-13
Some auto switch and some have settings in UEFI/BIOS to fix either Intel or nVidia as default.

Some get system to install with Intel and then use nVidia.

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

---

### Post by Yellow Pasque on 2013-09-13
Before tackling Bumblebee, it's probably best to uninstall whatever nvidia driver you installed and get your system back to a working state. Considering how many users have already borked their systems by installing nvidia drivers directly, there should be some pre-install note to that effect in the wiki. (Yes, I could edit it, but I hesitate to write wikis on hardware I don't own..)

---

