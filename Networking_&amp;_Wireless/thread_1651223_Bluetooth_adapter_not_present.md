---
title: "Bluetooth adapter not present"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by KeepaTalk on 2010-12-22
I have been using ubuntu for a few years now but am a noob when comes to the technical side of things, so apologies for my lack of knowledge.

I am using ubuntu 10.10 on a ZOTAC IONITX-A-U Atom N330 1.6GHz Dual-Core Mini ITX Intel Motherboard and since I have upgraded from 10.04 I no longer have blue tooth capabilities.  I have a logitech mx 5500 wireless keyboard and mouse, which uses a bluetooth dongle.  This is the strange part as they have both been working until recently.

They both lost their charge and after replacing the batteries in my keyboard it no longer is able to connect.  The mouse however works fine, until I dropped it :(  So I bought a microsoft explorer mouse which came with its own bluetooth dongle.  Which I plugged in and the mouse works fine.

But when I go to **System> Preferences> Bluetooth**  

I get Bluetooth adapter not present and Your computer does not have any Bluetooth adapters plugged in.

I have spent the last week googling this and can't seem to find any relevant info.

I ran this in terminal

```
$ lsusb
Bus 004 Device 004: ID 046d:c71c Logitech, Inc. 
Bus 004 Device 003: ID 046d:c71b Logitech, Inc. 
Bus 004 Device 002: ID 046d:0b06 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bc2:3300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Am I wrong in assuming that the logitech and microsoft dongles are being seen?

I have also removed and reinstalled bluetooth and bluetooth manager in the software centre, and the same with synaptic package manager, to no avail.

With both dongles plugged in could this also cause a problem?

Is there another way of starting the bluetooth?

Thanks in advance

KeepaTalk

---

### Post by Gibsonbc on 2011-05-04
Hi, I was wondering if you ever got your bluetooth working.  I run Ubuntu 10.10 on a laptop with an internal bluetooth device that just quit working all of a sudden.  I have been using a bluetooth mouse with no problems for a couple months.  I have changed the batteries.  When I open the Bluetooth manager (GNOME) I get the message that no devices are present on your computer.  I have searched and searched and can't find any fixes.

---

### Post by KeepaTalk on 2011-05-05
I did get it going...  I bought a new bluetooth dongle!!!  The old one had stopped working completely, this obviously is no help to you so sorry about that.

---

### Post by fredhami on 2011-05-23
I recently got a blue tooth dongle and it gives me the same message, which bluetooth dongle did you find that was working or is ubuntu capable?

---

