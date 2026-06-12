---
title: "Monitor out of Range after installing ATI Drivers"
date: 2013-01-22
forum: Multimedia Software
---

### Post by Szostak on 2013-01-22
Well, on every fresh install, it can be Ubuntu 11.04, 11.10, 12.04, 12.10; Kubuntu 12.04; Linux Mint 9 or 14 Cinnamon, when i install ATI proprietary drivers, and do a reboot (to get drivers working), on some versions it shows the Ubuntu or Linux Mint logo, and when it comes to load the MDM/LDM/GDM my monitor gets out of range.
The message showed is:
Monitor out of Range (frequency)
74.9kHz / 60Hz

However i can still use the tty1 (user text-mode, cli)

I tried all kinds of installation, versions, sources, ways, so i'm not installing the wrong way, as i tried all the ways that exist.

Please i really need an answer, this might be my 15th clean install! (though if i uninstall the drivers through tty1 and reboot, i can login through the graphical interface again).
My video card is HD 6770. I have tried both 32 and 64 bits OS.
I use a LCD 21.5" Monitor, it handles up to 1600x900 resolution (at least this is what i use in Windows 7). The image below is just an example of how its showed!

---

### Post by Bucky Ball on 2013-01-22
*Thread moved to **Multimedia & Video***

This is really a video driver issue as the installation appears to work fine without the ATI drivers installed. How are you installing them? Through 'Additional Drivers' or from a repository? ;)

Welcome to the forums and good luck.

---

### Post by Szostak on 2013-01-22
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video***

This is really a video driver issue as the installation appears to work fine without the ATI drivers installed. How are you installing them? Through 'Additional Drivers' or from a repository? ;)

Welcome to the forums and good luck.

Thank you Bucky!
Well, i've tried several ways, like:

through additional drivers, both fglrx and fglrx post release;

sudo apt-get install fglrx;

sudo chmod +X "catalyst-file-name".run (this is not exactly how i did, but it was one part of the tutorial to install those drivers you download from amd site, and you make .run files executable by running chmod +x);

after every install i did and also did not use aticonfig --initial in terminal.

i tried both installing and generating deb packages.
also tried through synaptics, ubuntu software center, muon package manager/software center, oh, and also tried from ppa's.

Any other method you tell me, i'll probably have tried.
As you said Bucky, the installations were all sucessful, it its a problem when i reboot.
I could install drivers easily, and through all these methods in my netbook C-60 APU, they run just fine :/, no problem at all.

Thanks for the attention everyone, and sorry, i thought it was in Installation thread, i thought Multimedia and Video, were for sound and graphics softwares or discussion :P.
Since this is a very weird problem, and sees to have no light!, could you try to approach this thread to any especialist in the forum Bucky? I don't mind waiting for answers, however if anyone could fix this problem, could even write a tutorial, who knows how many Gamers uninstalled linux for having this problem and not finding any fix but going back to M$?

---

### Post by Bucky Ball on 2013-01-22
The post release has never worked for me. It crashes everything. I only use the regular one.

---

### Post by Szostak on 2013-01-22
> **Bucky Ball said:**
> The post release has never worked for me. It crashes everything. I only use the regular one.

:/ i tried both, none of them worked, however both do well in my C-60.

---

### Post by Lightning Dragon on 2013-01-22
Hello,

Yes, it is the drivers. Please read this thread as the user had the same problem. Removing the drivers is the only way to fix these problems. 

[http://ubuntuforums.org/showthread.php?t=2107415&page=2](http://ubuntuforums.org/showthread.php?t=2107415&page=2)

Other words, it seems using an [adapter can fix the problem]("http://www.computerhope.com/forum/index.php?topic=110828.0") too. Also, you can try switching from your current monitor type. If you are on DVI, try using a VGA cord and vice-versa.

This is a very common error. A lot of people just cannot install their drivers, especially for ATI and NVIDIA, without encountering this problem. I have no idea why.

---

### Post by Szostak on 2013-01-23
> **Lightning Dragon said:**
> Hello,

Yes, it is the drivers. Please read this thread as the user had the same problem. Removing the drivers is the only way to fix these problems. 

[http://ubuntuforums.org/showthread.php?t=2107415&page=2](http://ubuntuforums.org/showthread.php?t=2107415&page=2)

Other words, it seems using an [adapter can fix the problem]("http://www.computerhope.com/forum/index.php?topic=110828.0") too. Also, you can try switching from your current monitor type. If you are on DVI, try using a VGA cord and vice-versa.

This is a very common error. A lot of people just cannot install their drivers, especially for ATI and NVIDIA, without encountering this problem. I have no idea why.

The first link wasn't much like my problem. I can still use Control + Alt + F1 or until F5 (text-mode user [CLI]).
The second link could be 70 or 80% like mine.
The Admin answered to the guy that this could be the resolution being set too high, and he could use GRUB recovery console, to enter and change video settings, i tried already running Ubuntu in recovery console, however i couldn't start a graphical interface, it was text mode, and i can already run text-mode when i face "Monitor is out of Range".
When he mentioned to Ubuntu Safe Graphics Mode, did he refer to recovery console, or "failsafe", or how can i use ubuntu safe graphics mode?

My monitor uses a VGA (Dsub) cord, and i do use a VGA to DVI adapter. I'll try tommorrow connecting my computer to my notebook screen, which has a VGA (Dsub) port.

Btw, Lightning Dragon, i found this yesterday:
[http://ubuntuforums.org/showpost.php?p=6999446&postcount=10](http://ubuntuforums.org/showpost.php?p=6999446&postcount=10)
We can edit xorg.conf using nano command, i tried once, but i guess it did set it wrong, or not the way it should, it seems too complicated, would need a guidance.

If changing the adapter do not work, could we work on this? Who knows it works?

Let's try the simple step first :P. Thanks for the attention for now!

---

### Post by Lightning Dragon on 2013-01-23
Hello,

I hope the cord switch works for you. When my DVI kept giving me "out of range" errors from my card, I switched to VGA and now it works. Sadly can't use DVI anymore, but then again my card won't work either so you might just get this to work.

Ubuntu safe graphics? I have never used  it, but Recovery mode seems to be working fine for you. It is supposed to drop you into the command line. Please see this link; [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) (you can also use the livecd)

Try using the adapter on the *computer* in question. If you currently have a VGA to DVI converter, then switch it around. Does your GPU (if you have one) offer more than one port, or does your motherboard?

How did you set up the xorg.conf? If you followed the steps on the links correctly only switching out the sizes/refresh rate to fit your monitor resolutions, then it should be configured correctly. Do you get any errors or reports? Check out the end of [this post]("http://ubuntuforums.org/showthread.php?t=83973") after "**[SIZE=3][SIZE=2]:!: Problems? [/SIZE][/SIZE]**[SIZE=2]**Things to try:**"[/SIZE].

If changing your monitor port type doesn't work I will be glad to continue to give you all I help I can.  (:

EDIT:

So I purposely went about giving myself this problem. And although I did not find a overall solution, I found one that wakes the monitor up when it goes out of signal in the CLI/TTY menu. If your monitor has an "auto detect" button on it, press it! It will bring the monitor back to live for about two minutes at a time. Use this if you are having issues in the CLI like screen all black or going to sleep.

---

### Post by Szostak on 2013-01-24
> **Lightning Dragon said:**
> Hello,

I hope the cord switch works for you. When my DVI kept giving me "out of range" errors from my card, I switched to VGA and now it works. Sadly can't use DVI anymore, but then again my card won't work either so you might just get this to work.

Ubuntu safe graphics? I have never used  it, but Recovery mode seems to be working fine for you. It is supposed to drop you into the command line. Please see this link; [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) (you can also use the livecd)

Try using the adapter on the *computer* in question. If you currently have a VGA to DVI converter, then switch it around. Does your GPU (if you have one) offer more than one port, or does your motherboard?

How did you set up the xorg.conf? If you followed the steps on the links correctly only switching out the sizes/refresh rate to fit your monitor resolutions, then it should be configured correctly. Do you get any errors or reports? Check out the end of [this post]("http://ubuntuforums.org/showthread.php?t=83973") after "**[SIZE=3][SIZE=2]:!: Problems? [/SIZE][/SIZE]**[SIZE=2]**Things to try:**"[/SIZE].

If changing your monitor port type doesn't work I will be glad to continue to give you all I help I can.  (:

So far as i'm kinda shorty in time, i'll do things slowly, perhaps faster depends on the time.

Well, this is my xrandr output:
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-1 disconnected (normal left inverted right x axis y axis)

```As you can see DVI-0 is my Adapter (my monitor is VGA) What is Screen 0: ? I'm quite sure this is my monitor.... and it handles up to 8192x8192.
I'll run others later


[COLOR=Red]Edit:[/COLOR]  Today i installed ati drivers, didn't reboot, set xrander (and i could use it just fine on the current session), then set them on xorg.conf , and finally reboot,  however it still happening. I'll try again, thought i still need to find a way take my HDMI cable off behind the living room TV (it's kinda stuck in a panel, else i'll try borrow from someone). 

Won't give up now :P, so far i've learn how to set the resolution, and i guess it'd be set on  xorg.conf too,  but frequency range problem didn't let me boot. 
So i'll still trying :P

@Lightning Dragon: I haven't such button, however i have "auto/set" which corrects/fix my image on Windows 7 (even remove that magnetic marks from the screen), thought i tried pressing it on the problem, and it didn't work :/.  I'll keep trying though :P

---

### Post by Szostak on 2013-01-24
Sorry for Posting again, but the last post was almost a book, therefore:

I did plug my HDMI cord into both my HD 6770 and my 27" TV, install ATI drivers, type sudo aticonfig --initial and then rebooted, at first it returned me the same Frequency out of range error, However after unplugging the DVI adapter (which was turned off already), it ran just fine.

I noticed that when i first turned on this Monitor, Gallium 0.4 did recognize it's resolution, very weird, might have to do with EDID, (mine dsub monitor seems to be broken on his EDID, since it's named as Generic PnP monitor, something like that).

Well. Then i guess this is solved :P thanks you for the attention Lightning Dragon and Bucky Ball :D.

Last question, if i buy either a VGA to HDMI cord or a VGA to HDMI adapter, would this error return, or it happens only to broken people using DVI adapters? Could it be my broken EDID? ( i heard some ways to fix it, maybe i should look into that).
Thanks

---

