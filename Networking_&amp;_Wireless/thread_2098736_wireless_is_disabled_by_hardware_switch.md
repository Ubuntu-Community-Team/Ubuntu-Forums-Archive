---
title: "wireless is disabled by hardware switch"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2012-12-27
I cannot get wireless because of this problem. Though this has appeared as a common problem, according to this forum and others, I have yet to find a solution that works for me (for example: [http://ubuntuforums.org/showthread.php?p=12423677#post12423677](http://ubuntuforums.org/showthread.php?p=12423677#post12423677))

Unlike the poster in the link above, I have an rtl8187 chipset. There is a hardware block on but no software block, and the hardware block cannot be disabled by rfkill unblock all. Installation of linux-firmware-nonfree does nothing either. Other info:

```
matt@MT6452:~$ sudo lshw -C network
[sudo] password for matt: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:c0200000-c0203fff ioport:a000(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:c0:a8:d8:96:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.2.0-35-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

---

### Post by Pjotr123 on 2012-12-27
Try this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on)

---

### Post by scholzilla on 2012-12-27
Thanks for that, but no luck. I didn't try two things mentioned:

1. I wasn't able to find a fn key combo that turns the wireless on/off on my laptop (Gateway MT6452). Not sure that exists.

2. I didn't install ndiswrapper. I've never needed this before and I'm hesitant to install something with the consequence that "sometimes you can only connect to unprotected wireless networks or to weakly protected networks". That's not what I would call a solution. I should note that wireless has worked fine for a long time on this machine and just magically stopped when I was running 10.04. I upgraded to 12.04 with the hope of fixing the problem, but no luck.

One thing I did notice is that in my BIOS settings (Phx BIOS), Wireless LAN is greyed out and set to [Restore]. Because it is greyed out, I can't change that setting. Not sure if that's a helpful clue...

Any other suggestions?

---

### Post by mtreece on 2012-12-27
> **scholzilla said:**
> and the hardware block cannot be disabled by rfkill unblock all

Do you get some sort of meaningful output from this or any other command?

---

### Post by scholzilla on 2012-12-27
Thanks for the follow up. No real useful info. This is the best I've got:

```
matt@MT6452:~$ sudo rfkill list
2: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

also, not sure if this is helpful, but:

```
matt@MT6452:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

---

### Post by scholzilla on 2012-12-27
oh, and one more thing I tried but didn't work:

```
 matt@MT6452:~$ sudo iwconfig wlan0 txpower on
matt@MT6452:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

---

### Post by mtreece on 2012-12-28
Not sure what else to tell you ... a friend of mine had a very similar issue to this the other day, actually, and rfkill unblock all was the fix for him. I'd suggest trying that again, if nothing else, but I'm not sure how else to help you. Maybe someone else has an idea?

A few last thoughts ...

Following up with your BIOS comment earlier,
> One thing I did notice is that in my BIOS settings (Phx BIOS), Wireless LAN is greyed out and set to [Restore]. Because it is greyed out, I can't change that setting. Not sure if that's a helpful clue...


According to [this forum]("http://www.dslreports.com/forum/r21993566-Phoenix-BIOS-Wireless-LAN-RESTORE"), it seems that the problem then resides at the wireless card and/or BIOS settings. Have you changed anything in your BIOS between it working and now not working? Otherwise, it seems as if they're suggesting the card could now be burnt out.

You can try and flash your BIOS and see if that helps any.

---

### Post by scholzilla on 2012-12-28
well, thanks for giving it a shot. Anyone else have suggestions?

---

### Post by scholzilla on 2012-12-28
one more piece of info: I just tried inserting a linksys wireless usb adapter, and it too is listed as disabled by hardware switch

---

### Post by srekcahrai on 2012-12-28
```
$ sudo ifconfig wlan0 up
```

This works everytime to me although there is ifconfig for wlan.

---

### Post by chili555 on 2012-12-28
> One thing I did notice is that in my BIOS settings (Phx BIOS), Wireless LAN is greyed out and set to [Restore]. Because it is greyed out, I can't change that setting. Not sure if that's a helpful clue...
You might try resetting the BIOS to defaults. In some BIOS, it is F9 followed by F10.> I wasn't able to find a fn key combo that turns the wireless on/off on my laptop (Gateway MT6452). Not sure that exists.Please see attached.

We will get nowhere until we resolve 'Hard blocked: yes.'

---

### Post by scholzilla on 2012-12-28
Thanks for the reply, srekcahrai, but all I get is:

SIOCSIFFLAGS: Operation not possible due to RF-kill

You win, chili555! I have no idea where you found that, but the combination of Fn+F2 solved it. What an annoying but welcomed solution! Thanks.

---

### Post by chili555 on 2012-12-28
> **scholzilla said:**
> You win, chili555! I have no idea where you found that, but the combination of Fn+F2 solved it. What an annoying but welcomed solution! Thanks.Glad it's working. Please use thread tools at the top to mark Solved.

Have fun!

---

### Post by scholzilla on 2012-12-28
thanks, but when I go to thread tools, all I get is an option to show a printable version of the thread. Happy to oblige if you instruct.

---

### Post by chili555 on 2012-12-28
It should be an available option. Don't worry about it. My pay is zero either way!

---

