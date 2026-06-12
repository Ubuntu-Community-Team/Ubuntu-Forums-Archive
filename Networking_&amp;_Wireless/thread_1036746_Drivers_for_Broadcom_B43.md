---
title: "Drivers for Broadcom B43"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by Micro_s on 2009-01-11
Hi,
I'm using Kubuntu 8.04 on my Dell Vostro 1700. Card specification:
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

I was using ndiswrapper ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")) and it works just fine, but I can't use Monitor mode.
Searching forums I found that using new Broadcom STA driver could solve this problem. Installing the driver was OK and I think the signal is now stronger. The problem is that now I can connect only via knetworkmanager and it works very well. But when I use Konsole it's disaster:

```
jan@Vostro1700:~$ iwlist eth1 scan
eth1      Interface doesn't support scanning.
```

And even if I know SSID, connecting using iwconfig does not work. Monitor mode does not work either.
Is it necessary to do the firmware upgrade?

Any help? Thanx.

PS: I'm new to Linux so if you need any specific info, please ask.

---

### Post by HunterThomson on 2009-01-11
you what to get this Linux native driver that I can't remember the name of. It is a alsom one that has Monitor mode Packet injection and all that. Look around but at lest I gave you a hint and hope.

Linux native driver.

---

### Post by kevdog on 2009-01-11
eth1 probably isn't the logical name assigned to the device.  If you post either
ifconfig 
or 
iwlist scan

this will show you the logical name.

Also post
lshw -C network
just so I can clarify and some things.

---

### Post by Ayuthia on 2009-01-11
It also could be possible that Network Manager is interfering with the manual method.  Regardless, the STA module does not appear to all the monitor mode even with the newest release.  I just tried it on my laptop and I was unable to change the mode.

Unfortunately the b43 module does not work for your card.  I think that is what HunterThompson is trying to suggest.

---

### Post by kevdog on 2009-01-11
Did not know the STA driver doesn't do Monitor Mode. Thanks for heads up on that -- a bummer indeed.

---

### Post by Micro_s on 2009-01-11
So you think there is no way how I can switch my card to Monitor mode? Not even with B43 module?

The Broadcom STA driver has better signal, but I can't use it via command line. So I will probably return to the ndiswrapper version.

Btw, *eth1* is the assigned name. I used to have *wlan0* using ndiswrapper, but with Broadcom STA driver a have *eth1*.

---

### Post by kevdog on 2009-01-11
ndiswrapper for certain does not do monitor mode.

---

### Post by Micro_s on 2009-01-11
I understand that Monitor mode does not work under ndiswrapper, but since I am unable to get it work under any driver I stick with ndiswrapper where I can connect also via command line (this I can't do with Broadcom STA driver). Only one positive thing with Broadcom STA driver is slightly stronger signal.

In some other forum I found that the b43 module works fine in 8.10 even for my card. One day I'm gonna try it.

---

