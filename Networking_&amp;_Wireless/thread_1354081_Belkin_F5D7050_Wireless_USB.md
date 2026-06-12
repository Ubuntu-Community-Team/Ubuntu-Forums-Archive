---
title: "Belkin F5D7050 Wireless USB"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by davester65 on 2009-12-13
I have read a lot of different threads about this hardware and tried plenty of the workarounds but nothing seems to cure this issue. I installed Karmic to my home pc, Karmic recognises the receiver & attempts to connect to my Thomson router but fails, all settings are fine and password is correct. Now this is where it gets interesting, after tearing my hair out for a weekend:D and trying a few live cd distros of various flavours both Gnome & KDE all of which had the same issue!! I did a fresh install of Jaunty and Hey Presto connection works first time 'straight out of the box' and has stayed solid for about 10 days now. 

My question to all you teccies out there is has something been removed from Karmic which was a standard install in Jaunty that makes these two components talk to each other? If so can anybody ID it so i can reinstall it.

My competence level is fairly low, though improving rapidly, been using Linux regularly for about a year now. Can cope with synaptic confidently and getting there with a terminal.

My PC specs are

ASUS Mainboard
AMD 64 6000+ Dual Core
4gb Ram
NVidia 9300 graphics
WD 500gb sata hdd

---

### Post by The Toxic Mite on 2009-12-13
Hey!

Can you go to Applications > Accessories > Terminal, and enter the following command please?

```

lsusb

```

Thanks :)

---

### Post by coffeecat on 2009-12-13
> **The Toxic Mite said:**
> Hey!

Can you go to Applications > Accessories > Terminal, and enter the following command please?

```

lsusb

```Thanks :)

@davester65, this is very important. The Toxic Mite's suggestion is to find out your  wireless chipset. I have two Belkin F5D7050's which have completely different chipsets - even different manufacturers. They both work just fine, but it's quite possible that yours is different again.

Good on yer, Belkin. :rolleyes:

---

### Post by davester65 on 2009-12-13
Chipset is version 1000, here's what lsusb brought up

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 001 Device 004: ID 04b8:0803 Seiko Epson Corp. Printer (Composite Device)
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0403:fa88 Future Technology Devices International, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Thanks Guys

---

### Post by coffeecat on 2009-12-13
> **davester65 said:**
> Bus 001 Device 006: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi

Belkin are a pain. :( Apart from changing their chipsets every 5 seconds, the output from lsusb with Belkin devices is remarkably unhelpful. Other manufacturers often give much more information. We are left with googling the ID number (050d:7050), which eventually turned up this link:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

Scroll down into the USB heading with the entry 'F5D7050 v1000 (USB ID 050d:7050)' in the left column. You'll see you have the RT2500usb chipset (yes, it is different from my two) and thereby hangs a sad tale. The RT2500 used to be recommended as the definitive Linux-friendly wireless device. It 'just worked'. But that was a couple of years ago. Then something went wrong with the kernel drivers - I don't understand what. Just do a search for 'rt2500' and you'll see what I mean. I've got two devices with the rt2500 chipset (one USB and one PCI) and I've put them away and don't use them anymore because of this. You say it works with Jaunty, but check your connection speed. You may only be getting 1Mb/s. :(

I'm sorry I can't be of any help but I really don't know what you can do. Performance of the rt2500 was poor in Jaunty - it's clearly collapsed with the later kernel if you're getting the same problems in other recent distros.

The rt2500 is now an old chipset. It's no consolation, but the later Ralink chipsets using the rt73 driver work fine. That's what I've got in one of my Belkins.

---

### Post by coffeecat on 2009-12-13
@davester65, I just noticed that you are in the UK as well, so I do have a suggestion.

If your budget stretches to £23 (incl p&p), why not order a USB device from [The Linux Emporium]("http://www.linuxemporium.co.uk/products/wireless/")? It's guaranteed to work with Linux. UK consumer law means your money back if it doesn't. Save yourself a headache for the sake of the price of a good curry and beer and all the trimmings. It's worth it! :wink:

---

### Post by davester65 on 2009-12-13
Thanks for that Coffeecat, looks like time for a new usb receiver then:D
Ran a comparison speed test, home pc (9.04) vs laptop (9.10), using three different speedtest sites (all UK based) home pc came out on top with average 6.32mbps against 4.96mbps laptop (intel dualcore 1.73ghz, 2gb Ram
Tested @ 10pm on Sun evening.
I did consider it might be a kernel issue, do Jaunty & Karmic run the same kernel? Jaunty is fully updated and currently running Gnome 2.26.1, Karmic is running Gnome 2.28.1.
TY for the help

---

### Post by coffeecat on 2009-12-13
> **davester65 said:**
> Thanks for that Coffeecat, looks like time for a new usb receiver then:D
Ran a comparison speed test, home pc (9.04) vs laptop (9.10), using three different speedtest sites (all UK based) home pc came out on top with average 6.32mbps against 4.96mbps laptop (intel dualcore 1.73ghz, 2gb Ram
Tested @ 10pm on Sun evening.
I did consider it might be a kernel issue, do Jaunty & Karmic run the same kernel? Jaunty is fully updated and currently running Gnome 2.26.1, Karmic is running Gnome 2.28.1.
TY for the help

Jaunty and Karmic have different kernels and it's the kernel that has the drivers. Yes, those speeds look OK. Come to think of it, it was the rt2500 PCI card that was giving me hopeless speeds, not the USB. Can't see why they should be different though. But I haven't tested either with Karmic. Sounds as though that might be a depressing education.

Did you see my Linux Emporium post? That's the place to go. Interesting to see that the D-Link USB device has a tux on the box and 'Works with MacOSX, Linux and Windows'. Times they are a-changing. Woo-hoo! Good to see Windows in its place too - last. :)

---

### Post by davester65 on 2009-12-19
I'll mark this thread as solved, for the time being i'll retain Jaunty on my desktop and Karmic on my laptop and invest in an up to date wifi dongle to solve the issue. Thanks for the help guys.

---

### Post by windowsfree on 2009-12-19
really surprised to read about the problem,  mine worked right away after a clean install of 9.10.  Mine is apprx 6 months old but works from that machine to a windows xp machine without problems.

---

### Post by coffeecat on 2009-12-19
> **windowsfree said:**
> really surprised to read about the problem,  mine worked right away after a clean install of 9.10.  Mine is apprx 6 months old but works from that machine to a windows xp machine without problems.

Yes, but did you read **all** the thread. Belkin uses different chipsets in the F5D7050 depending on the version number. Three different chipsets are mentioned in the thread. Which chipset does your Belkin have?

---

### Post by Meneon on 2010-03-08
Sorry to reopen this thread, but i have this problem with the F5d7050:

output from *lusb*

Bus 001 Device 085: ID 059f:1029 LaCie, Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

as you can see, it's not even listed..

I'm updated, and it did work a few days ago (out of the box)

Any help?

---

### Post by mark bower on 2010-03-08
my hat is off to coffeecat and a bit of repenting on my part.  i have pushed the F5D7050 in this section because of my success with 4 of them, different versions, on multiple computers. however, it appears i was just lucky.  i can state that of the versions that work is 7050, no revision letter, ID 050d:705c v4000.  I have used all of the devices on 8.10 thru 9.10.

i appreciate the info re linuxemporium. seems the community should emphasize purchasing only what is known to work, and try and steer clear of ndiswrapper, etc.  maybe that would put more pressure on manufacturers to be more cooperative.

mark

---

### Post by sureshsaragadam on 2010-08-16
BELKIN Wireless G USB Network Adapter F5D7050ak P74470akH, F5D7050

It is just a matter of few seconds to go online, 
It's just a Plug and Play, 
and It is a perfect blend with Ubuntu 9.10

by default it should work without any configuration changes required with Ubuntu 9.10

---

