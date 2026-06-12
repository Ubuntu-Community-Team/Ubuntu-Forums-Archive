---
title: "Video Card or Driver Problem"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by LuckyStrike502 on 2007-11-05
I am a first time Linux user, and I just uninstalled Windows and installed Ubuntu 7.10 (Gutsy) on my older HP Pavilion 7850. I have had a couple issues.

I kept my NVIDIA GeForce FX 5500 PCI video card installed while doing this, hoping it would recognize it and install the drivers, but it automatically recognized my Intel onboard video. I could not get past the Splash screen with the GeForce FX 5500. It stops and goes to a black screen right before loading the desktop. However, it loaded up just fine when I removed the GeForce FX 5500, and use the onboard video. I went into the BIOS to see if I could disable the onboard video, but I can't. There's only an option for onboard 512K and onboard 1MB. No option to disable it. Well, I exited BIOS and now I'm having a problem getting back to the Ubuntu desktop. After the progress bar completely loads on the Splash screen, it goes to a page with some text and flashes a few times, then before the desktop is supposed to load it just has a bunch of lines going up and down on the screen and I can't see anything but those lines. I have no idea what happened because I was able to run Ubuntu perfectly fine before with the onboard video. Now I can't get it loaded to install the drivers I need for my NVIDIA card. Could this actually be a problem with my onboard video? Oh, to to be more clearly about these lines, it kind of resembles a "snowy" screen, except it's a bunch of lines. I even tried to run in recovery mode with no luck. Someone told me it sounded like the refresh rate and/or resolution for the monitor is incorrect, and that there is an option I can specify at boot time to have the system boot using a generic VGA driver. But, they don't know what the VGA boot time option is. If anyone can help me with this issue, I would greatly appreciate it. Thanks in advance.

Jason

---

### Post by dabl on 2007-11-05
Is there any chance there's a "enable/disable" jumper on the motherboard for that onboard video chip?  You might be able to find out on the HP site, by searching on your Pavilion model.  :)

---

### Post by LuckyStrike502 on 2007-11-05
Hello dabl, and thanks for the reply.

Unfortunately, there is not an enable/disable jumper on this motherboard. Any other ideas?

---

### Post by ddrichardson on 2007-11-05
After booting can you use CTRL-ALT-F2 to open a terminal and try:```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
Coincidently some nvidia cards seem not to want to work without the noapic option sepcified at boot time. You say you got a black screen - is it like a blank screen or a black screen?

---

### Post by LuckyStrike502 on 2007-11-05
It's a black screen. I'm reinstalling Gutsy right now just to see if that will help, because I had no problem getting to the desktop when I first installed it. It's almost finished. I'll let you know if I can access the desktop after the reinstall.

---

### Post by LuckyStrike502 on 2007-11-05
Okay, the reinstall worked. I can now get to the desktop. Anyone have any recommendations on installing an NVIDIA GeForce FX 5500 PCI video card? As I said, I'm new to Linux, so I don't want to do this incorrectly. Any advice would be great! Thanks.

---

### Post by acron1 on 2007-11-05
The enable/disable option may be in the BIOS. Go in (may be f2 or del) on boot-up and look for it.

---

### Post by LuckyStrike502 on 2007-11-05
As I said in my first post, there is no option to disable the onboard video. There is only an option for onboard 512K and onboard 1MB. Therefore, when I start up Ubuntu, it recognizes my onboard video no matter what. Even when using my NVIDIA card, it won't make it past the Splash screen after the progress bar loads completely. It'll just go to a black screen. Does anyone know of any good tutorials for help installing an NVIDIA video card?

---

### Post by la1234uk on 2007-11-05
Hi, I read your post, have you tried to remove any monitor or other connections from the on board card...?

(If there is no monitor connected on the onboard card, and a monitor on your external  NVIDIA maybe the motherboard automatically switch the on-board card to disable.)

Greg Ruo

---

### Post by LuckyStrike502 on 2007-11-05
Yes, I have tried that already. When I tried that, it only made it to the Splash screen until the progress bar loaded completely. Then I got a black screen.

---

### Post by vafred on 2007-11-05
I tried also to install a Nvidia GeForce 8600 and when I connect it to the PCeX card and select in the bios to first look for the PCeX when I restart the computer my monitor stays asleep and never comes out of sleep.

When I remove the card and set the bios to look for the onboard card and connect the monitor to the onboard everything is OK again.

Any Ideas?

---

### Post by la1234uk on 2007-11-06
... well, if you made it to the splash screen, it means Ubuntu knows how to drive Nvidia and knows to how avoid the onboard card.

So it is probably a problem of Ubuntu initial approach with the driver, at a certain point it gives wrong instructions to your Nvidia and she goes off, or crashes.

It is strange because Nvida cards should work fine.

Do you have another partition with XP or something ?

If you do, have you tried to change the status of your Nvida, for example disable it, and then fire Ubuntu again? (You never know that Ubuntu is confused by a fancy setting of the card).

Another thing you could try is to experiment with Ubuntu distribution, try with an older one or with Ubuntu studio.

Cheers,

Greg Ruo

---

### Post by dabl on 2007-11-06
> **LuckyStrike502 said:**
> 

Anyone have any recommendations on installing an NVIDIA GeForce FX 5500 PCI video card? 



I personally like the Envy script installer for installing the proprietary driver.  I found the "Restricted Driver Manager" to have a weird little bug, at least wrt my 7900GS card. Here's the Envy link:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want to download and install the file "envy_0.9.8-0ubuntu10_all.deb" which is about halfway down the page.  :)

---

