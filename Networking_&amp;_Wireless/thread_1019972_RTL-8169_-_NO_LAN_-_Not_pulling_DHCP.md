---
title: "RTL-8169 - NO LAN - Not pulling DHCP"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by alfordej on 2008-12-23
Hey Guys,

   I previously posted my problem at the end of another thread:

[http://ubuntuforums.org/showthread.php?t=919111]("http://ubuntuforums.org/showthread.php?t=919111")

I don't think it's getting views because it is old and has many views\replies already.

Here's my background:

I'm new to Linux. 
I've been doing WINDOWS-RELATED IT for the past 5 years. 
I know how DHCP works.

Here's my problem:

When I "sudo dhclient eth1" it says that no DHCPOFFERS were received. 

The NIC is good, it has worked on this same network with the same hardware on Windows XP.

I've been troubleshooting for the past two days, here are some different things I've tried:

All the GRUB switches (I don't know if thats what you call them):
```

kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash noapic nolapic

noapic acpi=noirq

noapic acpi=off

noapictimer

noapictimer irqpoll

noapic acpi=off

noapic acpi=noirq nolapic

clock=pmtmr notsc

notsc

```

I Also turned off IOAPIC in my BIOS


Turned off IPv6:
```

/etc/modprobe.d/aliases, change the line

alias net-pf-10 ipv6

to

alias net-pf-10 off

Then commented it out.

```

Heres my uname -a

```

Linux ubuntubox 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

My Hardware:
Desktop Computer (MSI K8n Neo2 Platinum, AMD 3500+)
Onboard NIC (RealTek RTL-8169)
Wired Connection to Home Router
Home Router provides DHCP
Router connects to Cable Modem

I've done all the basic troubleshooting steps (learned from other posts). /etc/network/interfaces is correct. ifdown \ ifup does nothing.

After looking at my lspci -vvnn results, I can see that my NIC shares the same IRQ with my Video Card or USB Controller (it varies after restarts). I believe this might be a problem.

Any help would be greatly appreciated. Thanks guys!

---

### Post by alfordej on 2008-12-24
Soo... It's still not fixed, and I'm pretty much spent. Can anyone give me a troubleshooting path to follow?

---

### Post by alfordej on 2008-12-25
Update:

I booted straight off the LiveCD, and it worked!!  So I figured it must have been something with my install...

I re-installed, and it worked!!

That is, until I walked away from my computer. I guess it went into standby or something. When I came back, I was right back at the same problem... No matter what I do, I can't get my NIC to talk to the LAN again :(

Someone out there has to have come across this problem before... Anyone? Please?

---

### Post by aztalon on 2008-12-25
I have the same issue. Same NIC card, when my pc goes into suspend, I lose LAN as well. I have done all the troubleshooting I can find on the forums w/o resolve. I will be watching this forum for updates.

---

### Post by alfordej on 2008-12-28
> **aztalon said:**
> I have the same issue. Same NIC card, when my pc goes into suspend, I lose LAN as well. I have done all the troubleshooting I can find on the forums w/o resolve. I will be watching this forum for updates.

Good luck to you, please let me know if you get it resolved! 

From what I've seen, this must be a "black sheep" issue. I've seen other people post similar problems, with the accepted resolution being "Pick another NIC".

---

### Post by Rapture2k4 on 2008-12-28
It seems like it's not giving the NIC power when you "wake-up" the machine from sleep/stand-by.

I too am new to linux, but maybe there is an option to not put the NIC in standby mode...?

---

### Post by royleith on 2009-04-10
I have just discovered the same problem. The live installation CD comes with kernal 2.6.24.19 and this works fine for the installation. When the kernal is upgraded to 2.6.24.23 it stops working. For some reason they have either omitted the module for this card or they have changed it to a non-working version.

I discovered this when reinstalling Ubuntu Studio, but confirmed it with the existing Kubuntu installation.

I saw this coming with the Linux Rescue CD which failed to work with Ethernet when the actual module for this chipset was removed. I must try the latest version to see if that has been resolved.

Regards
Roy Leith.

---

