---
title: "Lubuntu 12.04 Broadcom 4312 wireless mess"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by arashiko28 on 2013-04-19
Ok. so this is a HUGE mess.
I have installed Lubuntu on an Acer Aspire One, everything perfect until I unplug the network cable... No wireless, I have tried everything so far and no success. The last I had was wireless, but had to go to software source and choose the driver everytime I started my computer, that was OK, minimum acceptable, but after the last update, I got this double options and no internet. If you choose anything but the marked options, it simply goes back without any changes. 

Please help! There has to be a way!

---

### Post by ubfan1 on 2013-04-21
You might get prompter response if you post this under the "networking wireless" forum.  Certainly a search there for 4312 will turn up a lot of information applicable to your problem.  From the lpphy in your post, I'd guess your chip is the low power version.  The b43 driver should work fine and should be present in your normal install, but I'm not familiar with lubuntu, just Ubuntu.  That driver needs firmware, which is available in package firmware-b43-lpphy-installer -- but you may already have the firmware from the listed linux-firmware-nonfree above -- just not sure it's the correct version for you.  Really, just adding the correct firmware and the b43 driver should start working with network manager.  If you tried any other drivers like the Broadcom STA driver, then maybe there is some cleanup to do to remove all traces of them, some of which interfere with the b43 driver.  Look for any
line exactly like "blacklist b43" in any file in directory /etc/modprobe.d, and delete or comment them out with an editor.  See if the b43 driver is listed in the "lsmod" command -- it should be there after a reboot.  Explicity add it with "sudo modprobe b43" and see if that starts networking.   Do check the other forum, your chip is not that new and is well supported, just too many possible choices which can mix things up.

---

### Post by mörgæs on 2013-04-21
> **ubfan1 said:**
> You might get prompter response if you post this under the "networking wireless" forum.

Moved.

Slightly off topic: It sounds like a new installation. Why did you pick such old version as 12.04?

---

### Post by arashiko28 on 2013-05-02
It was the available version when I installed it. The main problem is that I don't have wireless connection even though I have downloaded, installed and uninstalled every firmware related to this.

---

### Post by BazBear on 2013-05-03
> **mörgæs said:**
> Moved.

Slightly off topic: It sounds like a new installation. Why did you pick such old version as 12.04?
The OP isn't helping anyone help him/her with his/her lack of many important details, but calling 12.04...the last LTS build...old is a bit of a stretch, isn't it?

---

### Post by Hadaka on 2013-05-03
Hi, lets see if we can get this working for you.
Please COPY and paste the following
then post the output..
```
lspci -nn | egrep '0200|0280'
lsmod
cat /etc/modules
cat /etc/network/interfaces
rfkill list all
```
thanks.

---

