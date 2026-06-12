---
title: "WOL not working"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2010-11-05
I followed the instructions at [http://ubuntuforums.org/showthread.php?t=360901]("http://ubuntuforums.org/showthread.php?t=360901") to be able to turn on my Ubuntu 8.04 workstation remotely.

But I can't seem to make this work.

I know that my system supports WOL, as I enabled it in the BIOS ("Wake up by Onboard LAN").

The relevant settings reported by 'sudo ethtool eth0' are perfect:
```
        Supports Wake-on: pumbg
        Wake-on: g
```
But for some reason WOL doesn't work for me (yet), regardless whether I try to turn on my workstation from my DD-WRT router or from a laptop on the same subnet (all Ethernet-wired, not wireless).

Any idea how to troubleshoot this?

Thanks! :popcorn:

---

### Post by xp_newbie on 2010-11-07
It turns out that the green LED on the NIC is OFF when the computer is off.

Which means this isn't really a Linux problem but more likely a motherboard or BIOS problem.

Do you know of a good forum that discusses WOL problems at the Motherboard level?

Thanks.

---

### Post by psusi on 2010-11-07
Is the NIC an add in card or build into the motherboard?  Also what are you using to send the magic packet to wake it up?

---

### Post by xp_newbie on 2010-11-07
> **psusi said:**
> Is the NIC an add in card or build into the motherboard?
It's built into the motherboard (ABIT IP35 Pro (LGA 775), BIOS ver. 17, latest version!)

> **psusi said:**
> Also what are you using to send the magic packet to wake it up?
I've been using two methods:
[LIST=1]
[*]MC-WOL from a remote Windows XP laptop.
[*]DD-WRT router (Linksys WRT54GL)
[/LIST]

However, as long as the NIC's LED is off, it really doesn't matter who sends the magic packet.

---

### Post by psusi on 2010-11-07
Yep, that's odd... if it is built in, and especially if the bios has an option to enable WOL and it is on, then the link light should remain on in suspend.  Does it go off on the router as well?  Are you sure you are suspending and not hibernating?  If so then I can only conclude that this is a defect in the motherboard.  Mine remains on in suspend and I did once use ethtool to enable WOL from any packet rather than just the magic packet, and I could suspend and then it would wake back up as soon as someone said something on IRC.

---

### Post by xp_newbie on 2010-11-08
> **psusi said:**
> Are you sure you are suspending and not hibernating?
I am neither suspending nor hibernating. I am turning the PC off, using either the 'Shut Down' button in Ubuntu or the following shell command:
```
sudo shutdown -h -P now
```
Any idea how to leave the NIC's LED on, even after powering off the computer? (AC & DC are still in, it's the motherboard's logic that decides that the computer is "off").

---

### Post by psusi on 2010-11-08
Ohh, no, WOL wakes up the computer from suspend, not off.

---

### Post by xp_newbie on 2010-11-08
> **psusi said:**
> Ohh, no, WOL wakes up the computer from suspend, not off.
Are you sure about that?

I am able to to wake up the computer from off by simply hitting Ctrl+F1 on the keyboard, so I know that the motherboard's circuits are "listening" even when the computer is *not* in suspend/hibernate mode.

The question now is whether this could be possible for the NIC as well.

Are you absolutely positively certain that the ABIT IP35 Pro is not capable of powering on via its built-in NICs?

Thank you @psusi :popcorn:

---

### Post by psusi on 2010-11-08
Hrm... what does cat /proc/acpi/wakeup show?

---

### Post by xp_newbie on 2010-11-08
> **psusi said:**
> Hrm... what does cat /proc/acpi/wakeup show?
Answer:
```
PCI0      S5     disabled  no-bus:pci0000:00
PEX0      S5     disabled  pci:0000:00:1c.0
PEX1      S5     disabled  
PEX2      S5     disabled  
PEX3      S5     disabled  
PEX4      S5     disabled  pci:0000:00:1c.4
PEX5      S5     disabled  
HUB0      S5     disabled  pci:0000:00:1e.0
IGBE      S5     disabled  
USB0      S3     disabled  pci:0000:00:1d.0
USB1      S3     disabled  pci:0000:00:1d.1
USB2      S3     disabled  pci:0000:00:1d.2
USB3      S3     disabled  pci:0000:00:1a.0
USB4      S3     disabled  pci:0000:00:1a.1
USB5      S3     disabled  pci:0000:00:1a.2
EHC1      S3     disabled  pci:0000:00:1d.7
EHC2      S3     disabled  pci:0000:00:1a.7
AZAL      S5     disabled  pci:0000:00:1b.0

```

---

### Post by psusi on 2010-11-08
Take a look at the output of lshw and see if the PCI ID of your network card matches any of those.  Maybe HUB0.

---

