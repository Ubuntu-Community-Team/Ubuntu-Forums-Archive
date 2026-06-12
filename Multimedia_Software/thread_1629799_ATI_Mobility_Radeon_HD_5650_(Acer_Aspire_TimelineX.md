---
title: "ATI Mobility Radeon HD 5650 (Acer Aspire TimelineX 4820TG) driver install problem"
date: 2010-11-24
forum: Multimedia Software
---

### Post by andy12345 on 2010-11-24
Hello,
I am currently using ubuntu(64 bit) on my 4820TG ([related thread]("http://ubuntuforums.org/showthread.php?t=1495123")). After installation, I got the addition drivers, there were 2 options present 1. my wifi card driver which I successfully got and is working. 2. my ati graphics card (so I guess by default its running on the onboard intel card?). It said "ATI/AMD proprietary FGLRX graphics drivers", I downloaded it and activated it.
After rebooting the desktop didn't show up and instead it directly booted into the terminal. After searching for a while I found a solution and ran the following commands
```
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo reboot
```
and Ta-Da my desktop was back, but the driver was again disabled, enabling again would cause it to go to terminal after reboot.
SO i guess the problem is in the driver or something?
What I have tried so far
--Searching, but didn't get any specific answers (I am new to linux/ubuntu and I hardly know what shell or kernel or anything else is, again pardon me for that, so its certainly no point to telling me to 'patch a script' or anything, unless of course you tell me how to patch first)
--Switching to discreet in BIOS and trying to enable the drivers and reboot.After reboot its gets stuck in the login like background window with some messages, forcing me to reboot and change back to switchable and the same cycle again.

Waiting for a solution (which could be followed easily..)

PS- sorry for my bad english.

---

### Post by jocko on 2010-11-24
ATI's linux driver (fglrx) does NOT support switchable graphics, will not work when switchable graphics is active, and will totally mess up the integrated intel graphics if you try to use it when the switchable graphics is activated in bios.
Either use only the discrete card with the fglrx driver or use the open source drivers (intel/i915 and radeon) with switchable graphics activated in the bios.

---

### Post by andy12345 on 2010-11-25
> **jocko said:**
> ATI's linux driver (fglrx) does NOT support switchable graphics, will not work when switchable graphics is active, and will totally mess up the integrated intel graphics if you try to use it when the switchable graphics is activated in bios.
Either use only the discrete card with the fglrx driver or use the open source drivers (intel/i915 and radeon) with switchable graphics activated in the bios.

As I said in my first post, I have also tried to switch to discreet through BIOS and try the drivers but ubuntu gets stuck at the loading screen with some messages like, checking battery state [ok] etc..

Your second solution to use the open source drivers "(intel/i915 and radeon) with switchable graphics activated in the bios", how to I get them through command line? can you tell the commands please?

---

### Post by jocko on 2010-11-25
The open source drivers are the drivers that were installed and activated by default before you installed ati's proprietary driver. Just uninstall fglrx (search for it in synaptics and mark for complete removal), then make sure you *don't* have a xorg.conf and reboot.

**Edit:** The commands would be:

```
sudo apt-get purge fglrx fglrx-amdcccle
sudo rm /etc/X11/xorg.conf
sudo reboot
```

---

### Post by andy12345 on 2010-11-26
> **jocko said:**
> The open source drivers are the drivers that were installed and activated by default before you installed ati's proprietary driver. Just uninstall fglrx (search for it in synaptics and mark for complete removal), then make sure you *don't* have a xorg.conf and reboot.

**Edit:** The commands would be:

```
sudo apt-get purge fglrx fglrx-amdcccle
sudo rm /etc/X11/xorg.conf
sudo reboot
```

Thank you I will try it out and post the results.
I did not try to install the ati drivers, but I want to use the intels card, the battery backup shown is low, which makes me guess that the ATI card is still active. How do I solve this issue?

---

### Post by andy12345 on 2010-11-26
I did not try to install the ati drivers, but I want to use the intels card, the battery backup shown is low, which makes me guess that the ATI card is still active. How do I solve this issue?

---

### Post by Yellow Pasque on 2010-11-26
You can't turn the ATI card off unless your BIOS allows it.

---

### Post by jocko on 2010-11-27
> **andy12345 said:**
> I did not try to install the ati drivers, but I want to use the intels card, the battery backup shown is low, which makes me guess that the ATI card is still active. How do I solve this issue?

> **Temüjin said:**
> You can't turn the ATI card off unless your BIOS allows it.
Actually, you *can* switch it off even if bios does not have that option, at least if you have a 2.6.35 or newer kernel.

I have a 3820TG with the same graphics situation, and I save pretty much battery life by turning off the radeon. This is how I did it:
```
gksudo gedit /etc/rc.local
```Add these lines before "exit 0" at the end of the file:
```
echo DIGD > /sys/kernel/debug/vgaswitcheroo
echo OFF > /sys/kernel/debug/vgaswitcheroo
```Then reboot and see the power consumption go down.
With the radeon off, powertop reports ~11-15W on idle with the screen brightness on the lowest possible setting (and between 4 and more than 6 hrs of battery life), with the radeon powered on (but not in use) it reports ~28W (and 2.5 hrs of battery life)...

One annoying problem is that there are a bunch of error messages about atombios when I turn off the computer, possibly causing the shutdown to take a few extra seconds, but I can live with that.

---

### Post by andy12345 on 2010-11-28
> **jocko said:**
> Actually, you *can* switch it off even if bios does not have that option, at least if you have a 2.6.35 or newer kernel.

I have a 3820TG with the same graphics situation, and I save pretty much battery life by turning off the radeon. This is how I did it:
```
gksudo gedit /etc/rc.local
```Add these lines before "exit 0" at the end of the file:
```
echo DIGD > /sys/kernel/debug/vgaswitcheroo
echo OFF > /sys/kernel/debug/vgaswitcheroo
```Then reboot and see the power consumption go down.
With the radeon off, powertop reports ~11-15W on idle with the screen brightness on the lowest possible setting (and between 4 and more than 6 hrs of battery life), with the radeon powered on (but not in use) it reports ~28W (and 2.5 hrs of battery life)...

One annoying problem is that there are a bunch of error messages about atombios when I turn off the computer, possibly causing the shutdown to take a few extra seconds, but I can live with that.

Thank you. I have tried it and will be testing now. All I don't want is the lap to heat up, it heats up pretty fast in idle mode too (only in ubuntu), so I hope this switching stops that problem.

PS-anyway to check which graphics card is active?

---

### Post by jocko on 2010-11-28
> **andy12345 said:**
> PS-anyway to check which graphics card is active?

First you need to know the BusID of the cards:
```
lspci | grep VGA
```
This will give you an output similar to this:
```
**[COLOR=Blue]00:02.0[/COLOR]** VGA compatible controller: **[COLOR=Blue]Intel[/COLOR]** Corporation Core Processor Integrated Graphics Controller (rev 18)
**[COLOR=Red]02:00.0[/COLOR]** VGA compatible controller: **[COLOR=Red]ATI[/COLOR]** Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)
```

To see the status of the switch for the cards:
```
cat /sys/kernel/debug/vgaswitcheroo/switch
```
The output will look something like this:
```
0: :[COLOR=Red]**Off:0000:02:00.0**[/COLOR]
1:+:**[COLOR=Blue]Pwr:0000:00:02.0[/COLOR]**
```
In this output you can see that my intel card is powered on (indicated with "Pwr") and the ati card is powered off (indicated with "Off"). The "+" sign show which gpu is being used.

---

### Post by andy12345 on 2010-11-28
> **jocko said:**
> First you need to know the BusID of the cards:
```
lspci | grep VGA
```
This will give you an output similar to this:
```
**[COLOR=Blue]00:02.0[/COLOR]** VGA compatible controller: **[COLOR=Blue]Intel[/COLOR]** Corporation Core Processor Integrated Graphics Controller (rev 18)
**[COLOR=Red]02:00.0[/COLOR]** VGA compatible controller: **[COLOR=Red]ATI[/COLOR]** Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)
```

To see the status of the switch for the cards:
```
cat /sys/kernel/debug/vgaswitcheroo/switch
```
The output will look something like this:
```
0: :[COLOR=Red]**Off:0000:02:00.0**[/COLOR]
1:+:**[COLOR=Blue]Pwr:0000:00:02.0[/COLOR]**
```
In this output you can see that my intel card is powered on (indicated with "Pwr") and the ati card is powered off (indicated with "Off"). The "+" sign show which gpu is being used.
this is what mine shows
```
0: :Pwr:0000:01:00.0
1:+:Pwr:0000:00:02.0

```
so I infer that both of them are ON?
I followed the instructions as they are, wonder where I went wrong, any other solutions?

---

### Post by jocko on 2010-11-29
Try switching it manually:
Press Ctrl+Alt+F1 to switch to a vt and login, then run these commands:
```
sudo service gdm stop
cat /sys/kernel/debug/vgaswitcheroo
sudo -i
echo DIGD > /sys/kernel/debug/vgaswitcheroo
echo OFF > /sys/kernel/debug/vgaswitcheroo
exit
cat /sys/kernel/debug/vgaswitcheroo
sudo service gdm start
```

If that works, maybe you have a typo or some other mistake in your /etc/rc.local?
Let's see how it looks:
```
cat /etc/rc.local
```

---

### Post by grichak on 2010-11-29
Hello !

I have the same pc and the same problem :(
I'm sure there isn't any errors in the file you told to edit because it was just a copy/paste. 

All I want is to deactive the ATI card, I just want the Intel to work. If you have other solutions, it would be great :-)

---

### Post by grichak on 2010-11-29
After a little bit of search on internet, I found this howto : [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) 

It allows switching between different graphics cards and it worked for me ! 
My battery status is also not working. But after using this script, it sometimes works... but not everytime :(

---

### Post by andy12345 on 2010-11-29
> **jocko said:**
> Try switching it manually:
Press Ctrl+Alt+F1 to switch to a vt and login, then run these commands:
```
sudo service gdm stop
cat /sys/kernel/debug/vgaswitcheroo
sudo -i
echo DIGD > /sys/kernel/debug/vgaswitcheroo
echo OFF > /sys/kernel/debug/vgaswitcheroo
exit
cat /sys/kernel/debug/vgaswitcheroo
sudo service gdm start
```

If that works, maybe you have a typo or some other mistake in your /etc/rc.local?
Let's see how it looks:
```
cat /etc/rc.local
```
Didn't work
This is how it looks like
[HTML]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo DIGD > /sys/kernel/debug/vgaswitcheroo
echo OFF > /sys/kernel/debug/vgaswitcheroo
exit 0
[/HTML]

Now going to try the solution suggested by grichak.

---

### Post by andy12345 on 2010-11-29
> **grichak said:**
> After a little bit of search on internet, I found this howto : [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) 

It allows switching between different graphics cards and it worked for me ! 
My battery status is also not working. But after using this script, it sometimes works... but not everytime :(

Thank you so much works perfectly for me :D
I am now again a happy person.

also thank you very much to everyone who took the pain in helping me out (especially jocko)
I will now test if my alp heats or not when it is on onboard graphics.

PS- Even after 1 and half hours of use it shows 5 hours left YEY!!

---

### Post by Confusered on 2010-11-30
Hi,

I recently purchased the same laptop, an Acer 4820tg, and am having the same problems. I thought it was a 32 bit/64 bit issue, but apparently its not. I have tried VGA switcheroo, and it works great, but after the switch, what happens is that the graphics quality is worse than using the i915 IGP. I can't even enable desktop effects. Also, Ubuntu will sometimes show a blank screen if too many switches are made too quickly, but this is still okay. Output to an external display using IGP is fine, but when 5650m is activated, the external display is garbled. Installing the proprietary FLGRX drivers will only crash the system. I am currently trying out the open source drivers and will report back if there is any success. Thanks!

This page might be of interest: [http://art.ubuntuforums.org/showthread.php?t=1621487](http://art.ubuntuforums.org/showthread.php?t=1621487)

---

### Post by hutini on 2010-12-01
Hey guys i am not sure if i understoud this thread completly.
So did u manage to use both cards (with switching) 
or did u just turn off the radeon gpu?
If ur able to switch right now which driver do u use 4 the radeon gpu.

I am askting this because i managed to switch the gpus, but the radeon gpu's driver dont work correctly (didnt even manage to play tuxcart)
So if you can tell me which driver is could use and how to install it, you woult make me feel very very happy :D

PS Sorry for my bad english.

---

### Post by andy12345 on 2010-12-24
> **hutini said:**
> Hey guys i am not sure if i understoud this thread completly.
So did u manage to use both cards (with switching) 
or did u just turn off the radeon gpu?
If ur able to switch right now which driver do u use 4 the radeon gpu.

I am askting this because i managed to switch the gpus, but the radeon gpu's driver dont work correctly (didnt even manage to play tuxcart)
So if you can tell me which driver is could use and how to install it, you woult make me feel very very happy :D

PS Sorry for my bad english.

Nope, we can just switch, the radeon is on when you switch it, i.e. its eating up power, but doesn't work.


-------------
Major problem found again, and I think its again because of the graphics thing [http://ubuntuforums.org/showthread.php?p=10277139#post10277139](http://ubuntuforums.org/showthread.php?p=10277139#post10277139)

---

### Post by 27CaseyCZ on 2011-02-01
So I finally figured out how to turn off ATI graphic and turn on Intel HD graphic.. after 6 ntb reinstalling :D.. after start .. 

WRITE THIS IN TERMINAL: 

[COLOR="Teal"]sudo su
(your password)
echo OFF > /sys/kernel/debug/vgaswitcheroo/swicth
echo DIGD > /sys/kernel/debug/vgaswitcheroo/swicth[/COLOR]

and logout... then you have to wait about 15 sec.. after that login... 

THATS ALL :) 

I have 5820TG 5464G75Mnks and a battery runtime is about 5-6 hours ;-)
Ubuntu 10.10 Maverick, BIOS 1.19

0: :[COLOR="Red"]Off:0000:01:00.0[/COLOR]
1:+:[COLOR="Red"]Pwr:0000:00:02.0[/COLOR]

---

### Post by iotriado on 2011-08-03
i want to ask something else.
In case you need to extend the monitor , using the HDMI output , can you disable the intel graphics and enable the ATI?

---

