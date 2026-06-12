---
title: "network card failing"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by DoppyNL on 2009-03-15
Hi people!

I've got a problem with the network of my new computer.
The hardware:
- Gigabyte ga-ep45-ud4p motherboard
- Core i7-920 (4x 2666 MHz) HT1I12
(the rest is probably not interesting for this topic).

I've succesfully installed Ubuntu 8.10 64 bit. Ran into some problems with the graphics card but that seems to be fixed.

The problem is the network card. It sometimes fails when I reboot the computer. I get no network at all. And I haven't got a clue on why that is.

I found this topic that describes the exact problem for someone else:
[http://forums.tweaktown.com/f69/ga-ex58-ud5-f5-ubuntu-8-10-network-bug-30741/](http://forums.tweaktown.com/f69/ga-ex58-ud5-f5-ubuntu-8-10-network-bug-30741/)
note: I'm not running windows myself..

He says he gets it fixed by removing all power from the computer and wait a bit.  But that isn't really a final solution ofcourse.
On top of that, it doesn't seem to be working for me at te moment :(

Any idea what might be causing this and how I can fix this?

---

### Post by DoppyNL on 2009-03-15
Extra information:
[list]
[*]My gigabit switch shows a light at 10/100Mbps for the network cable going to my computer. Allthough the motherboard is capable of 1000Mbps... (actual speed seems to be 1000Mbps though)
[*]my switch also reports the connection to my router as 10/100Mbps. This should also be 1000Mbps. Can't test the actual speed of that connection, as there is no device on the other side that supports that speed ;). The switch reports 2 other computers as 1000Mbps, wich is correct. (total of 4 connections used)
[*]When the connection is working, Ubuntu reports the connection is 1000Mb/s
[*]When my computer boots it shows a list of devices it's found (just after the boot-screen). Sometimes the network controller is NOT in this list. When this is the case the network will NOT work. When it is in the list it sometimes works, sometimes it doesn't.
[*]Network is configured using DHCP in Ubuntu.
[/list]

Need more information to help find the problem, please let me know what and I'll take care of it.

---

### Post by BatteryKing on 2009-03-15
Have you used ethtool yet?  I have a EX58-UD5 with the f5 BIOS patch and when I cold boot the computer with the twisted pair RJ-45 jack connected, ethtool reports the only physical interface on the particular tap as being FIBRE and there is a mismatch where ethtool reports 1000 Mb/s operation while the gigabit switch reports 100 Mb/s operation and thoroughput tests show 100 Mb/s operation.  The desired result is to have ethtool report TP (twisted pair) operation and have the speed numbers match.

My workaround for this is as follows: Shut down and turn off power supply.  Unplug Ethernet cable.  Turn on and boot up Linux.  Once I am to the login prompt, then I plug in the Ethernet cable.  Reporting of TP physical interface and real 1 Gb/s operation is now to be had.

---

### Post by DoppyNL on 2009-03-17
I'm a little at a blank on how to use ethtool for this problem.
I'm getting results from ethtool and it reports the following for the device:

```
~$ sudo ethtool eth0 
Settings for eth0:
	Supported ports: [ FIBRE ]
	Supported link modes:   1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: FIBRE
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

This is with a working line; not sure about the speed at the moment though.

---

### Post by DoppyNL on 2009-03-18
The same command with a network that isn't working:

```
$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ FIBRE ]
	Supported link modes:   1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: FIBRE
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: pumbg
	Current message level: 0x00000033 (51)
	Link detected: yes

```

I can't find any differences...

---

### Post by DoppyNL on 2009-03-27
Is there any way to install another driver to handle this card?
Or to tell the OS what driver to use for this card?
How do I do that?

---

### Post by chili555 on 2009-03-27
Here is a post from a person with this exact motherboard in which the ethernet could not even be detected (!) no matter what!!! His solution is the last post on page 3.

[http://ubuntuforums.org/showthread.php?t=1070631](http://ubuntuforums.org/showthread.php?t=1070631)

There is a bug in there somewhere, reliably turning the card on at boot, perhaps.

---

### Post by DoppyNL on 2009-03-28
The solution he had was installing an additional network card and using that card, instead of the onboard one.
Not really a fix, it's a workaround.

I allready thought of that allready.
I'm going to try ndiswrapper now and install a windows driver as linux drivers don't seem to handle this chip correctly.

---

### Post by DoppyNL on 2009-04-08
So I've not found any more information about this problem. The problem persisted.

Then I downloaded Ubuntu 9.04 BETA and installed it.
The problem dissapeared and the card is now working properly. 
When booting the bios shows the network controller allways as present. Seems that the driver in Ubuntu 8.10 was the cause of the problems. Therefore anyone having this problem in Ubuntu 8.10 should be able to fix this using another driver (not sure wich though)...

So, for me this problem is solved.

tnx for the input.

---

### Post by BatteryKing on 2010-07-03
My still fairly new EVGA board works fine.  However the exact same components fitted to my older GA-EX58-UD5 = failures all over the place until the system could no longer detect the boot device (among a number of other failures and instabilities).  The kicker is the Gigabyte board is still the same way because Gigabyte claims the board "passes all tests" when I RMA'd it after thumbing their noses at me for weeks.  What a sham!

---

