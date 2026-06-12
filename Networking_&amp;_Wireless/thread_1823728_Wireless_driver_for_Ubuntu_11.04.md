---
title: "Wireless driver for Ubuntu 11.04"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by TimmyK. on 2011-08-12
Hi, I've got a friend who, after experiencing the horrors of Vista and me telling of the wonders of Linux, decided to switch. However, her Wifi is not working. I typed in 'lspci -nn', and it seems that two things came up; a Broadcom BCM4401 and an Atheros AR2413. Does the computer have two Wifi cards? Which do I need the driver for, or both? Which brings me to my second question; where do I find and how do I install a driver? Thank you.

---

### Post by IWantFroyo on 2011-08-12
You'll have to plug the computer into an ethernet port, and run Additional Drivers. If that doesn't work, look for some bcm drivers in Synaptic.

---

### Post by TimmyK. on 2011-08-12
How do I run additional drivers? Please keep in mind that unlike most of the people on Ubuntu forums, terminal commands are not my second language (I wish). As for Synaptic, I typed in "BCM" and a bunch of stuff came up. Which one? b43-fwcutter maybe? (it seemed to work for [this thread]("http://ubuntuforums.org/showthread.php?t=1795391")).

---

### Post by IWantFroyo on 2011-08-12
There's a program called Additional Drivers. If you're using Ubuntu, you should be able to just type it into the dash and find it.

Oh well. If that isn't working for you, just open up a terminal or alt-f2 and type 'jockey-gtk''.

You'll definitely need b43-fwcutter. You'll have to look through the other packages to see if they support your wireless card (it should be in the description). I'd do this for you, but I'm on an openSUSE computer right now, so you're on your own there.

---

### Post by TimmyK. on 2011-08-12
Hang on a second, B43-fwcutter is only for BCM43xx series, is it not? So will it work with the BCM4401?

And should I try this terminal command and install them all and see if this works?

```
sudo apt-get install b43-fwcutter firmware-b43-installer jockey-gtk
```

But will the b43 packages support BCM4401?

---

### Post by pdc on 2011-08-12
Timmy:

I think the Atheros is your wireless !

eg from here

[http://wiki.debian.org/ath5k](http://wiki.debian.org/ath5k)

seems like the ath5k is built into the kernel since 2.6.32

> PCI: 168C:001A Atheros Communications Inc. AR2413 802.11bg NIC

if you copy and paste some commands

uname -rm
sudo iwlist scan
lshw -C Network
iwconfig

there was a bug reported with the ath5k in May;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/784351](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/784351)

then; a post said

> For anyone else with this problem, ***a workaround would be to install the latest snapshot of the madwifi driver from madwifi-project.org,*** which is working perfectly so far. (I'd still like to see ath5k fixed though :)

so:

you go here:

[http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k) as the full page 

and they then point you to 

[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

you need to identify the kernel you are using

> uname -a

and then download the correct package 

if I leave it to you to install? they tell you on the page

---

### Post by TimmyK. on 2011-08-18
> **TimmyK. said:**
> Hang on a second, B43-fwcutter is only for BCM43xx series, is it not? So will it work with the BCM4401?

And should I try this terminal command and install them all and see if this works?

```
sudo apt-get install b43-fwcutter firmware-b43-installer jockey-gtk
```

But will the b43 packages support BCM4401?

Thanks for your help everyone! It was not an Atheros card. I'm still not sure why there are two results. Maybe one is Bluetooth or something? 

Anyhow, she ran the command on her computer, rebooted, and it worked! So the b43 packages do include the BCM4401. Thanks for the help. Au revoir!

---

### Post by bkratz on 2011-08-18
> **TimmyK. said:**
> Thanks for your help everyone! It was not an Atheros card. I'm still not sure why there are two results. Maybe one is Bluetooth or something? 

Anyhow, she ran the command on her computer, rebooted, and it worked! So the b43 packages do include the BCM4401. Thanks for the help. Au revoir!

Tim,

Glad you got it working, but the BCM4401 is the ethernet card not the wireless. The modules that control it are ssb and b44. Since the ath5k module is in the kernel, I suspect that is what is actually controlling your wireless. Not sure why what you did worked, but congratulations!

---

