---
title: "Intel 4965AGN wireless card on Ubuntu 9.10 doesn't always work"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by Joakim.Karlsson on 2010-02-24
[FONT=Fixedsys]I have problems with Intel 4965AGN wireless card on a Dell Latitude D830 with Ubuntu 9.10 64-bit. After googling the problem and reading a lot of forum posts I have got to the conclusion that something is wrong with the drivers and that the rfkill value isn't set correctly. I don't know what additional information you need but I will explain how the system behaves and how the rfkill value looks like.

When I boot the computer with the RF switch set to on the wireless doesn't get enabled. If I switch the RF switch to off the bluetooth gets the disabled. And when I turn the switch back on the bluetooth gets enabled but nothing happens to the wireless, it is still disabled.

/sys/class/rfkill/ contains the following after boot:
```

name                type            state
---------------------------------------------
hci0,               bluetooth       1
dell-wifi           wlan            2
dell-bluetooth      bluetooth       2
phy0                wlan            1

```/sys/class/rfkill/ contains the following when the switch has been turned to off:
[/FONT]
```
name                type           state
---------------------------------------------
dell-wifi           wlan           1
dell-bluetooth      bluetooth      1
phy0                wlan           2
```[FONT=Fixedsys]

/sys/class/rfkill/ contains the following when the switch has been turned back to on:

```
name                type            state
---------------------------------------------
dell-wifi           wlan            2
dell-bluetooth      bluetooth       2
phy0                wlan            1
hci0                bluetooth       1
```On the other hand. When I boot the computer with the RF switch set to off the wireless is disabled at boot. If I switch the RF switch to on the bluetooth and wireless gets the enabled. And when I turn the switch back off the bluetooth and wireless gets disabled. So everything works as it should when I boot with the switch set to off.

/sys/class/rfkill/ contains the following after boot:

```
name                type             state
---------------------------------------------
dell-wifi           wlan           2
dell-bluetooth      bluetooth      2
phy0                wlan           2
```/sys/class/rfkill/ contains the following when the switch has been turned to on:

```
name                type           state
---------------------------------------------
dell-wifi           wlan           1
dell-bluetooth      bluetooth      1
phy0                wlan           1
hci0                bluetooth      1
```/sys/class/rfkill/ contains the following when the switch has been turned back to off:

```
name                type           state
---------------------------------------------
dell-wifi           wlan           2
dell-bluetooth      bluetooth      2
phy0                wlan           2
```[/FONT]

---

### Post by coskierken on 2010-02-24
The kernal provides support directly for the 4965AGN.  Intel has let a few faulty 4965AGN go out the door with the N not working correctly, if at all.  Is this the mini-PCI version or a USB version?  I have found with a dual-band router, you will connect to both 2.4 and 5 GHZ at the same time if both are transmitting.  If you can, turn off the a and g on the intel and just connect with the N.  I would personally do this on the router, also, if you don't have any older G equipment or other machines using the connection.

---

### Post by chili555 on 2010-02-24
> Is this the mini-PCI version or a USB version?I was not aware there is a USB version of Intel 4965ABG. I want one! Do you have a link or source?

Does the odd behavior change if *dell-laptop* is removed? ```
sudo rmmod -f dell-laptop
```Now try the wireless button and see if things improve.

---

### Post by Joakim.Karlsson on 2010-02-24
Yes after removing the dell-laptop module it started working correctly. What is the dell-laptop module for? How can I fix this without having to remove the module manually?

---

### Post by chili555 on 2010-02-24
*dell-laptop* is supposed to enable some functions that are unique to Dell. As you can see, it doesn't work well. I suspect that it conflicts with another similar module, *dell-wmi*. If you notice that other functions now don't work correctly, obviously reverse the removal.

When I bought my first laptop, an IBM T30, certain functions were not well implemented, but they were not functions vital to me. In your case, wireless is vital! If you have ill effects, post back so the searchers will learn from your experience.

Please do:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Before you press Enter, proofread carefully. The double arrows append the line to any other lines currently in the file.

dell-laptop is now blacklisted and will not reload on boot, unless, of course, you edit */etc/modprobe.d/blacklist.conf* to remove the blacklist line.

---

### Post by Joakim.Karlsson on 2010-02-24
Just curious... Who is responsible for the development of the dell-laptop module? Where can I report the bug? Where can I get the source code, I'm a developer and is just curious how this is implemented. :)

---

### Post by chili555 on 2010-02-24
This is all I know at this time:> $ modinfo dell-laptop
filename:       /lib/modules/2.6.31-19-generic/kernel/drivers/platform/x86/dell-laptop.ko
alias:          dmi:*svnDellInc.:*:ct8:*
license:        GPL
description:    Dell laptop driver
author:         [COLOR="Blue"]Matthew Garrett <mjg@redhat.com>[/COLOR]
--- snip ---Of course, the issue may be in the way that Ubuntu implements it. You might search Launchpad for pending bugs and add your comments.

I have helped three or four people here with Dell laptops and non-funtioning wireless using this method, so it's a known issue.

---

### Post by Sjenitzer on 2010-02-25
You helped another Dell user, thanks!

---

### Post by masternosaj on 2010-03-02
This worked for me as well.  Thanks for the good info!

---

### Post by Tburger on 2010-06-05
I've been working for four days on getting my wireless connection - I'm running Ubuntu 10.04 (downloaded using Wubi) on a Dell Inspiron with a Dell Wireless 1397 card (BCM4312).  I tried everything and couldn't get the hardblock turned off; removing dell-laptop was the answer, so thanks! (New to Linux too; the last four days sucked but I've learned a lot after spending all this time in the terminal)

---

### Post by tonosecundino on 2010-10-05
> **chili555 said:**
> I was not aware there is a USB version of Intel 4965ABG. I want one! Do you have a link or source?

Does the odd behavior change if *dell-laptop* is removed? ```
sudo rmmod -f dell-laptop
```Now try the wireless button and see if things improve.

> **chili555 said:**
> *dell-laptop* is supposed to enable some functions that are unique to Dell. As you can see, it doesn't work well. I suspect that it conflicts with another similar module, *dell-wmi*. If you notice that other functions now don't work correctly, obviously reverse the removal.

When I bought my first laptop, an IBM T30, certain functions were not well implemented, but they were not functions vital to me. In your case, wireless is vital! If you have ill effects, post back so the searchers will learn from your experience.

Please do:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
```Before you press Enter, proofread carefully. The double arrows append the line to any other lines currently in the file.

dell-laptop is now blacklisted and will not reload on boot, unless, of course, you edit */etc/modprobe.d/blacklist.conf* to remove the blacklist line.

You have just fixed EVERYTHING that went bad in my Dell laptop, **thank you very very much**.

---

### Post by tommacca on 2011-01-10
Just wanted to say that this fixed my disabled wireless card on a Dell Vostro 3500 onto which I had installed 10.04 via Wubi. I spent hours banging my head against this so thank you.

I registered with Ubuntu Forums just so I could express my gratitude!

---

### Post by chriswu000 on 2011-10-06
> **chili555 said:**
> I was not aware there is a USB version of Intel 4965ABG. I want one! Do you have a link or source?

Does the odd behavior change if *dell-laptop* is removed? ```
sudo rmmod -f dell-laptop
```Now try the wireless button and see if things improve.

You are a god amongst men.  After a month of living without wireless and period bouts of furious frustration, your fix has enabled my wireless.  If you send me your address, I will send you a case of beer.  Or perhaps an Amazon gift card.

---

### Post by chili555 on 2011-10-06
> You are a god amongst men. More like a thief among men; I stole the idea from some other god. In any event, I am very glad it's working.> If you send me your address, I will send you a case of beer. Or perhaps an Amazon gift card.If you feel you must offer a reward for what I enjoy doing simply for its own sake, May I suggest this:  [http://www.ubuntu.com/community/get-involved/donate](http://www.ubuntu.com/community/get-involved/donate)

---

