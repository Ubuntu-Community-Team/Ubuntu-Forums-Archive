---
title: "Ubuntu's broken my ethernet port?"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by Brittany ITG on 2010-08-07
I'd like to start up by saying I really don't have much of a clue about networking. PC Hardware and the likes is my specialty, but when it comes to people talking about DHCP and gateways, you're going to have to talk me through it slowly.

So I use wired internet, using a standard ethernet cable from my motherboard (Gigabyte GA-785GMT-USB3) to my router. 

I normally use Windows, and have only used Ubuntu 3 times thus far, as is going to be a requirement for college in the coming year. I use Ubuntu 64-bit, using the 'grub' (or something similar) utility for multiple operating systems on one computer.

Immediately when I got into Ubuntu, it started complaining that it couldn't connect to any networks, I eventually gave up, and decided to go back into Windows.

Now when I logged in, My 'Local Area Connection 3' using the Realtek PCIe GBE Family Controller driver is acting erratic. It is completely incapable of connecting going from 'Network Cable unplugged' for a while, then flashing to 'Enabled' then quickly to 'Identifying.' and back to the original state, and repeat.

I'm getting a laptop next week anyway, so I don't mind losing Ubuntu. Is there any way I can deal with this? I'm currently using a very old, tempermental PCI wireless card, which I am not happy with.

Is there anything that can be done, or am I going to be digging into my ever-emptying purse again for a new piece of hardware.

Thanks in advance to anyone who can offer any input,
- Brittany

---

### Post by Brittany ITG on 2010-08-07
Sorry for the bump, just need an answer before I go buying anything if anyone has a clue

---

### Post by jbreckmckye on 2010-11-26
I wouldn't necro this thread, expect I've had the exact same problem, albeit with Mint-64 (another 'buntu variant). I've had the same issue with the same router, except that my ethernet port flat-out insists that 'a network cable is unplugged'. Again a Realtek PCIe GBE Family Controller.
 
The idea that an OS could 'break' hardware sounds fanciful, I know, but I wondered if anyone else had this issue?

---

### Post by jbreckmckye on 2010-11-26
I don't like necroposting. I like doubleposting even less. But I think I've resolved this by using a *full* power reset (including unplugging and leaving the machine for four hours) to reset the PHY.

My understanding is that the ehternet card has two components: a MAC and a PHY. The PHY has its own memory and, with certain BIOSes / wake on LAN / power settings, can remain powered as long the computer is plugged in (ie physical power is available to the PSU and motherboard). Wake on LAN is obviously a prime contender. Alas, an OS can put a PHY in a 'broken' state, or a 'standby' state it can't later override, and the ethernet card becomes unworkable, even after a reboot into another operating system, because a simple power down doesn't actually 'clean' it.

My symptoms - the fact the light was off, the need to do a full power reset (after multiple OSes, restorations, driver installs, etc. etc.), that the bug persisted whatever OS I booted with - all corresponded to those outlined in [this]("http://ubuntuforums.org/archive/index.php/t-1104867.html") archived thread.

More information is provided at [http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg00168.html]("http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg00168.html"):

> "As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues
with the r8169 driver if you dual boot Windows on some systems. Windows
by defaults disables the NIC at Windows shutdown time in order to
disable Wake-On-Lan, and this NIC will remain disabled until the next
time Windows turns it on. The r8169 driver in the kernel does not know
how to turn the NIC on from this disabled state; therefore, the device
will not respond, even if the driver loads and reports that the device
is up. To work around this problem, simply enable the feature
"Wake-on-lan after shutdown." You can set this options through Windows'
device manager."

Who'd have thought an obscure mailing list archive would hold the answer?

---

### Post by anmg on 2010-12-31
**jbreckmckye**
Thanks for explanation. I'll check it.
Becouse I have MB with Realtek on board.

But what about sound? looks same simptom problem with it problem with it on my MB ASUS P7P55D based on Intel HDA - VIA® VT1828S 8-Channel High Definition Audio CODEC

---

### Post by skinlayers on 2010-12-31
These symptoms perfectly match the problems I've been having with the GA-EP45T-USB3P I bought for my dad. I have it triple-booting Ubuntu 10.10 64-bit, Windows 7 Ultimate 64-bit, and Mac OS X 10.6. While doing a network file copy operation under Mac OS X over AFP, the UI locked up. After rebooting, I couldn't connect under any of the 3 OSes. Windows 7 will keep cycling between "Network Cable unplugged", "Enabled", and "Identifying". At one point it would connect, but only at 10Mbit. I sent the board back to Gigabyte, but nothing has changed since it was returned to me. At this point, I've given up and am using a PCI 100-Mbit card. If anyone can figure out a consistent way to rest the Realtek ethernet between reboots, I would be extremely greatful!

skinlayers

Note: I just checked the device manager properties on the NIC, and "Wake-on-lan after shutdown" is already enabled.

Note2: If you pull the power, and then try to power the machine on, it will expend that capacitors almost immediately. No need to wait 4 hrs with it unplugged to reset the PHY on the card.

---

### Post by anmg on 2011-01-04
**Brittany ITG** and to **ALL**

Please check this thread
[http://fostergrant.ubuntuforums.org/showthread.php?t=1436667](http://fostergrant.ubuntuforums.org/showthread.php?t=1436667)
there is a real solution

---

