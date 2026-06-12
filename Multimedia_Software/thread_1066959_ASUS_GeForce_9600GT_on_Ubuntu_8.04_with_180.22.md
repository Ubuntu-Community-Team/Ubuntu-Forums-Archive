---
title: "ASUS GeForce 9600GT on Ubuntu 8.04 with 180.22?"
date: 2009-02-11
forum: Multimedia Software
---

### Post by couzin2000 on 2009-02-11
[COLOR="Red"]**Please note:** this post is the same exact post I put into the NVNews forums. I'M asking on both fronts because this issue is time-sensitive. Thanks for understanding.[/COLOR]

I've just downloaded the 180.22 drivers yesterday from the Nvidia website. Just got this new card, and I want to take advantage of it. Here's what I did.

[LIST]
[*]Had a GigaByte 7300GS before, running nvidia drivers... ran smoothly for 1 whole year. no glitches.
[*]When I got the new card, I turned off the pc completely and swapped out the cards, before changing any software.
[*]booted back up, and got a corrupted screen (was completely off-center). Hit **CTRL-ALT-SHIFT-F1** to go into terminal mode.
[*]typed 
```
sudo sh NVIDIA-Linux-x86-180.22.pkg1.run
```
[*]Ran the installation without a glitch, and without GDM running (gnome display manager).
[*]Rebooted, and system automatically went into "safe mode" graphics. There was an X-windowed manager to select screen and graphics card. My monitor wasn't listed per se, but I chose the next best thing (instead of AL2216W db, I had to select AL2216W x). Then set the resolution to 1650 x 1080 x 24bit, widescreen.
[*]When I chose the graphics adapter, I had a choice between "**NVIDIA**" and "**nv - geforce, quadro, etc etc **". Both, when tested, do not work.
[*]When the boot-up into gnome is complete, I'm stuck with a 800x600 screen. (The system seems to default back to generic drivers.)
[*]Ran
```
nvidia-settings
```
[*]Upon startup of the nvidia settings app, it tells me I'm not running the proper drivers, and to run 'sudo nvidia-xconfig'
[*]Ran 
```
sudo nvidia-xconfig
``` It seemed to reconfig my xorg.conf automatically.
[*]Ran
```
sudo gedit /etc/X11/xorg.conf
```
[*]Edited the file to delete the lines under "Modules" except for the line with 'glx' in it (as per ubuntuforums.org here: [http://ubuntuforums.org/showpost.php?p=6680823&postcount=7]("http://ubuntuforums.org/showpost.php?p=6680823&postcount=7"))
[*]Upon reboot, got the safe-mode selector again... and I cannot get past that. Stuck in 800x600x24bit.
[/LIST]

Someone give me a clue as to what I should do next to make sure that, upon reboot, my Ubuntu will detect the proper driver and USE IT. Thanks!

---

### Post by Fire_Chief on 2009-02-11
If you're asking what driver to use, then select the NVIDIA one as that is the binary driver you just installed.
The safe mode is most likely due to the monitor not being configured properly. You may be able to use that close match monitor configuration you mentioned however it is not guaranteed.

---

### Post by couzin2000 on 2009-02-11
> **Fire_Chief said:**
> If you're asking what driver to use, then select the NVIDIA one as that is the binary driver you just installed.
The safe mode is most likely due to the monitor not being configured properly. You may be able to use that close match monitor configuration you mentioned however it is not guaranteed.

Well, I did select the NVIDIA driver, but I came back to the same point as stated above. Is there another way for the system to *not* bypass the new driver I just put in?

As far as the monitor, maybe I can try "default plug n'play monitor"... I'll see about that. But as I recall, it didn't change a thing. I'll post my **xorg.conf** contents here when I get home.

Anybody else?

---

### Post by Fire_Chief on 2009-02-11
Usually when a new Nvidia driver is installed, it overwrites or creates a new xorg.conf. Kind of a bummer but you may be able to resurrect the old xorg.conf and use it again.

---

### Post by couzin2000 on 2009-02-11
> **Fire_Chief said:**
> Usually when a new Nvidia driver is installed, it overwrites or creates a new xorg.conf. Kind of a bummer but you may be able to resurrect the old xorg.conf and use it again.

I may have a backed-up xorg.conf file somewhere, but I'm sure I *never* backed up the config I had 2 days ago... next idea. What are my next steps?

---

### Post by couzin2000 on 2009-02-11
bump... time sensitive, someone please help out here!

---

### Post by couzin2000 on 2009-02-11
So, I finally got some resoltuion going by deleting every single *linux-restricted-module* in the pc. I also deleted the nvidia-settings package... 

Now I have 1650x1080x24... but I can't see the proprietary module working, nor can I figure out how to see **which driver** I'm actually using currently. So I don't think it's working so far... anyone gotta clue?

---

### Post by couzin2000 on 2009-02-11
Never mind... Moved on from Hardy Heron to Interpid Ibex... installed 180.29 from a new repo. Works fine. Thx

---

