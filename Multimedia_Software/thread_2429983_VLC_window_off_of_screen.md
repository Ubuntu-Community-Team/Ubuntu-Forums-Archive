---
title: "VLC window off of screen"
date: 2019-10-25
forum: Multimedia Software
---

### Post by MoebusNet on 2019-10-25
Google hasn't been a friend for this one on Lubuntu 18.04 64-bit with updates. Hoping to fix this issue, I've tried to update to the most-current VLC, but seem to be able to only come up with VLC version 3.0.8-0ubuntu18.04.1 from the repositories even with backports & PPA master-daily enabled, so no changes there.

VLC's window extends off the left edge of my screen and cannot be repositioned further right to get it on screen. The window will go full-screen, but still is off the left edge of the screen. I read that UI-scaling was broken, but the fix doesn't seem to apply (no /etc/environment).

Any ideas?

---

### Post by uRock on 2019-10-25
Their website shows 3.0.8 being the current version. [https://www.videolan.org/vlc/index.html](https://www.videolan.org/vlc/index.html)

---

### Post by MoebusNet on 2019-10-25
Yeah, same website I checked but never found the current version number. Thank you for finding it. I just wanted to see if anyone else had the same issue and possibly a solution before I filed a bug report.

---

### Post by mc4man on 2019-10-26
If you wish a later vlc version then you'd need to install as a snap  but your issue seems local, either your hardware, drivers or config.
You could try a fresh config by deleting the ~/.config/vlc folder.

Otherwise,who knows, you haven't provided any info as to the hardware nor GPU or driver on affected machine.

---

### Post by MoebusNet on 2019-10-26
@mc4man - Thank you for the suggestion of deleting the  '~/.config/vlc' folder. If it'll help my system is:

System76 Serval Professional 7
2nd Generation Intel Core i7-2860QM Processor ( 8MB L3 Cache, 2.50GHz ) 
32 GB Dual Channel DDR3 SDRAM at 1600MHz - 4 X 8GB
Nvidia GeForce GTX 560M Graphics with 1.5GB GDDR5 Video Memory 
nvidia-driver-390
Lubuntu 18.04 64-bit+current updates
VLC version 3.0.8-0ubuntu18.04.1

I don't really need a newer version of VLC; it's just that last year they were testing a release candidate for 4.0.0 and i was curious if it had a fix for my issue.

I'll try deleting the ~/.config/vlc folder and report back. FWIW, I went ahead and filed a bug report on this issue; I can always close it out if it is indeed local to me.

---

### Post by MoebusNet on 2019-10-26
@mc4man - as you  suggested, deleting the '~/.config/vlc' folder and reopening VLC appears to have cured the issue. That was a solution that Google never found for me, so again, thank you. I've closed out the bug report I submitted as invalid and included what cured my problem on Launchpad. I'll show this thread as 'SOLVED'.

---

### Post by MoebusNet on 2019-10-28
@sneazzy - I can't promise that you and I have the same problem. If you believe that we do, here is what I did to solve it as mc4man suggested:

1) Open LXTerminal (in Lubuntu) and type ```
 sudo pcmanfm 
``` Of course replace 'pcmanfm' with the name of your file manager (ie, 'nautilus' for Ubuntu).

2) In your flie manager, click View>Hidden Files

3) Scroll down to the '.config' folder

4) Double-click the '.config' folder to open it

5) Scroll down to the 'vlc' folder

6) Right-click the 'vlc' folder

7) In the menu that pops up, Left-click 'Move to Trash'

8) Close your file manager

9) Close the LXTerminal window.

10) Reopen VLC; it should now reconfigure itself and work as designed.

If you still believe you have a bug here is how to report a bug: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

