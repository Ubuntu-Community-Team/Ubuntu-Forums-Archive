---
title: "wireless NOT working Fijitsu Siemens Amilo Pro v3505"
date: 2012-09-17
forum: Networking &amp; Wireless
---

### Post by denP on 2012-09-17
I have fujitsu siemens amilo pro v3505 laptop.

I have two systems installed. They are:
- Ubuntu 12.04;
- Windows 7.

I do not have a special button to switch on / off the Wireless adapter. The button can be supported by drivers.

Case 1.

When I start Win7 WiFi is enabled (I had to install the driver to be able to switch it on automatically). I reboot and then WiFi is enabled for Ubuntu. It is not switched off during the reboot procedure.

Case 2.

I start Ubuntu. WiFi is switched off.

I have Intel PRO/Wireless 3945ABG [Golan]

Could you help me?

```


rfkill list all
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: phy5: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Note that I use also Ralink 11n Adapter to be able to connect to the Internet.

---

### Post by chili555 on 2012-09-17
> rfkill list all
1: [COLOR="Red"]phy0[/COLOR]: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: [COLOR="Red"]phy5[/COLOR]: Wireless LAN
	Soft blocked: no
	Hard blocked: noDo you have two wireless devices running? Why? I think you will have better luck blacklisting one or the other.

Is there a setting in the BIOS to enable wireless? Is it enabled?

---

### Post by denP on 2012-09-18
Thank you for the answer.

Yes I use two (see above). One of them is to be able to connect to the Internet. In the Case 1 both of them work.

In BIOS WiFi is enabled. The problem is the indicator of WiFi is switched off when I shut down the laptop. Now it turns on when I start Win7 (see Case 1).

I tried with one. It does not work. I would like to work with one only.

---

### Post by chili555 on 2012-09-18
> Yes I use two (see above). One of them is to be able to connect to the Internet. In the Case 1 both of them work.Why are you running the internal at all if it can't connect to the internet? Why can't it?

Are you trying to manage both wireless devices and their connections with Network Manager? That's probably some of the problem.

---

### Post by denP on 2012-09-18
I would like to use only the internal one.

When I try to use only internal adaptor, boot Ubuntu. It does not work. I would like to make it work alone, without the external one.

When I boot Win7 both of them work, reboot (not switch off the laptop and then switch it on) both work for Ubuntu.

I would like to use only the internal adaptor, but it does not work in Ubuntu if I boot Ubuntu at first.

---

### Post by einonm on 2012-09-18
It sounds like there's a hardware or software killswitch that enables your internal wifi that your kernel is not aware of. 

There may be a kernel module you can build to enable it, unless the laptop is very new. For example, a quick google found these:

[http://ubuntuforums.org/archive/index.php/t-1901052.html](http://ubuntuforums.org/archive/index.php/t-1901052.html)
[https://secure.kitserve.org.uk/content/xorg-and-wireless-ubuntu-and-debian-fujitsu-siemens-amilo-pro-v2000d](https://secure.kitserve.org.uk/content/xorg-and-wireless-ubuntu-and-debian-fujitsu-siemens-amilo-pro-v2000d)

I suggest you take a look at the second one - there is a comment from someone saying that it also worked for your model.

---

### Post by denP on 2012-09-18
Thank you.

I have done:

```
sudo nano /etc/modules
```

and add

```
wistron_btns
```

to the bottom of the list.

After reboot I press the button to enable wireless and it does not work.
Should I do something else? Should I try the command

```
sudo modprobe wistron_btns
```

---

### Post by einonm on 2012-09-19
Browsing through the code for a recent kernel, the driver that controls amilo laptop kill switches appears to have the name 'amilo-rfkill'. 

I'd suggest trying the fix again, but with 'amilo-rfkill' instead of 'wistron_btns'.

---

### Post by denP on 2012-09-19
> **einonm said:**
> Browsing through the code for a recent kernel, the driver that controls amilo laptop kill switches appears to have the name 'amilo-rfkill'. 

I'd suggest trying the fix again, but with 'amilo-rfkill' instead of 'wistron_btns'.

Thank you.

file /etc/modules:
```


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

amilo-rfkill


```

After reboot WiFi does not work.

The command gives:

```

sudo modprobe amilo-rfkill
FATAL: Module amilo_rfkill not found.

```

---

### Post by einonm on 2012-09-19
Ok, looking at my current 12.04 kernel (3.2.0-30) the amilo-rfkill driver is not there, but the wistron_btns and also fsam7400 are (the amilo-rfkill driver is based on fsam7440, and the blog post mentions this).

So...my last resort would be to see if the original fsam7400 driver  would make a difference (same procedure as last time, Miss Sophie...).

Oh, and I also found this... which is old, but may be of interest

[https://answers.launchpad.net/ubuntu/+question/2639](https://answers.launchpad.net/ubuntu/+question/2639)

---

### Post by denP on 2012-09-19
> **einonm said:**
> Ok, looking at my current 12.04 kernel (3.2.0-30) the amilo-rfkill driver is not there, but the wistron_btns and also fsam7400 are (the amilo-rfkill driver is based on fsam7440, and the blog post mentions this).

So...my last resort would be to see if the original fsam7400 driver  would make a difference (same procedure as last time, Miss Sophie...).


Thank you. It does not work. Laptop goes to the black screen with some system lines. But WiFi does not work.

> **einonm said:**
> 
Oh, and I also found this... which is old, but may be of interest

[https://answers.launchpad.net/ubuntu/+question/2639](https://answers.launchpad.net/ubuntu/+question/2639)


It is old (for kernels 2.4 and 2.6). They suggest to go to [http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/) and download the file [http://www.cakey.de/acerhk/archives/acerhk-0.5.35.tgz](http://www.cakey.de/acerhk/archives/acerhk-0.5.35.tgz).

When I type 'make' it waits something. Changed a string in Makefile to
KERNELSRC=/usr/src/linux-headers-3.2.0-30-generic-pae

I think it can not find something in this version. Could you help me?

---

### Post by einonm on 2012-09-20
> **denP said:**
> 
When I type 'make' it waits something. Changed a string in Makefile to
KERNELSRC=/usr/src/linux-headers-3.2.0-30-generic-pae

I think it can not find something in this version. Could you help me?

I think that may not be the issue. I have uncovered this bug report from 2007, which indicates that it may be a BIOS issue, and that a BIOS upgrade may work.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105420](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105420)

---

