---
title: "Ubuntu 11.04 alpha2 in virtual box 4.0"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rjbgbo on 2011-02-07
I'm trying to install Ubuntu 4.11, the following 
following configuration:

> lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)


> lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Tinning before finalizing the installation, the following screen appears:

[[IMG]http://img155.imageshack.us/img155/5195/capturadetela3vz.th.png[/IMG]](http://img155.imageshack.us/i/capturadetela3vz.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

And the installation is aborted.

I'm used to install using Virtual Box and also following the link below for reference:
[http://www.webupd8.org/2010/12/how-to-test-ubuntu-1104-with-unity-in.html](http://www.webupd8.org/2010/12/how-to-test-ubuntu-1104-with-unity-in.html)

To make sure of compatibility of my hardware with Unity, I read:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

---

### Post by howefield on 2011-02-07
Moved to *Natty Narwhal Testing and Discussion* forum.

---

### Post by [Snc] on 2011-02-07
I also had the same problem today, with natty alpha2, but on a *real* machine.

The installation aborted, I retried to install, it aborted again in the same spot. (I've got some logs ... if anyone is interested, PM me or post here)

Then I ran natty and everything was OK, after a few updates, it was a normal OS (just like a clean install)

PS. (just like a clean install) except:
-everything crashes as soon i move my mouse over the screen decoration
-I cannot run terminal
-I had no way to update except synaptic
-kernel updates don't budge .... :)
-... i know, its alpha

---

### Post by MadCow108 on 2011-02-07
might be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/webkit/+bug/710582](https://bugs.launchpad.net/ubuntu/+source/webkit/+bug/710582)

the alternate installer works for me

---

### Post by w3rt on 2011-02-07
I had this on a daily install about a week ago, but since upgrading to alpha 2 I no longer get the problem

---

