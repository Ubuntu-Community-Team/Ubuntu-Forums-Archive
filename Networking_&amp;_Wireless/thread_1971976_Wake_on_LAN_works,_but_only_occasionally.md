---
title: "Wake on LAN works, but only occasionally"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by ocwo92 on 2012-05-03
I want to set up a computer for wake on lan, but I have a rather strange problem: I can wake-up my computer **only sometimes** when it has been shut down from Ubuntu 12.04 (i386 desktop).

I'm shutting it down with:

  $ sudo shutdown -h now

I can't figure out what is different when I shut it down and WOL-wake it from one time to another, because I merely login via ssh, issue the shutdown command and then attempt to wake it--sometimes successfully, most often not.

Is anyone familiar with this problem? How do I troubleshoot this phenomenon?



My homework stuff:

I've made sure that the following command is run as root before shut-down (and, as a matter of fact, at startup, at network-up, and at network-down):

  $ /sbin/ethtool -s eth0 wol g

According to ethtool, the network card does get set to WOL-g:

  $ sudo ethtool eth0
    ...
     Supports Wake-on: pg
     Wake-on: g

WOL and everything else that can wake up the computer, including PS/2 keyboard and PCI devices, are enabled for wake-up in the BIOS.

According to [this thread](http://ubuntuforums.org/showthread.php?t=1380776), manual configuration with acpitool may be necessary. Unfortunately, my built-in network card doesn't seem to be listed when I issue "acpitool -w" so I don't know if acpitool is any good here.

I can WOL-wake the computer from sleep mode. I've attempted several shutdown measures (i.e., shutting down the computer using the Unity "Shut down" menu, as well as by issuing "sudo shutdown -h now" and "sudo shutdown -P now"). None of them seem to enable WOL; except, every now and then it wakes!

The network light flickers on the network card when the magic packet is sent, so the network card is clearly on.

I only checked the wake-up after a Windows 7 shutdown once, but it served to prove that the BIOS, motherboard, and network card support WOL.

I've attempted to shut down the computer with:

  $ sudo shutdown -P now
  $ sudo halt

but neither of them allow the computer to be consistently powered on via WOL.

(The reason "halt" doesn't work for WOL is that the computer shuts down but doesn't turn off; instead it stops after the message: "System halted." I suspect this is an entirely unrelated problem, possibly caused by the fact that network-mounted drives don't seem to be unmounted. Apparently halt isn't identical to shutdown -h as I used to think.)

---

### Post by ClashTheBunny on 2012-05-05
I feel your pain.  This has been a major headache for me too.

My problem is more similar to [this bug]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/324295").  Maybe the solution to this bug will help.

One of the issues may be bad ACPI support in your BIOS.  Have you tried updating the BIOS?

---

