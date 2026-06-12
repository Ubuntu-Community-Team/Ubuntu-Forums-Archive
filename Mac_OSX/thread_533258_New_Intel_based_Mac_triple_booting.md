---
title: "New Intel based Mac triple booting"
date: 2007-08-23
forum: Mac OSX
---

### Post by bonestonne on 2007-08-23
Ok, so my new [well, almost a year old] G5 [bought used] is running OS X 10.4.10 [updated yesterday] and i also partitioned the disk so i'm triple booting with Ubuntu 7.04 and Windows XP. i'm using Grub boot loader to select the OS as its easier than parallels or boot camp for me.

i went out and stupidly bought a netgear wireless adapter, the WG111v2...only reason that was stupid is because Netgear doesn't make their own OS X drivers and i didn't check that when i got it.

after a lot of searching around, i managed to find out that the netgears' chipset is the same as the Realtek 8187, so what i tried to do was download the 10.4.x driver for that and install it, however i'm still unable to use my wireless adapter. strangely enough it works flawlessly for me in both Ubuntu and XP [and my network is setup with a 128bit WEP]. although i have very limited bandwidth wirelessly in Ubuntu, it works well, and is encouraging me to move my computer back upstairs.

my main problem is that i prefer using my mac's native OS [OS X] because its the only OS that has my library synced [i made the mistake of pointing to the wrong folder after reinstalling OS X and lost my winamp playlist for it and don't want to make it over]. I use Linux for most of my graphic design work, as i'm running 64 bit, and it runs faster than XP, however i can't sync my library with Ubuntu, as i'm denied access to my HFS+ partition [i've tried to change permissions without any luck].

does anyone know of a way i can use my netgear adapter with OS X or am i just screwed over on this? i've read of people using the adapter successfully on 10.3.x [not specified which version] however no luck on an intel based mac.

thanks in advance, i appreciate it.

---

### Post by pxwpxw on 2007-08-24
I think you need to elaborate, for instance -
How are you running XP on a G5, and why not get an Apple Airport Extreme wireless card for the G5, or maybe it is already built in?

---

### Post by 3rdalbum on 2007-08-24
I think he's a bit confused about the technical terms.

Bonestonne: G5 is the processor that was used in Apple's desktop computers (excluding the Mac Mini) before the switch to Intel. As Windows isn't compiled for the PowerPC processor, you've got a Macintel computer.

---

### Post by pxwpxw on 2007-08-24
Yes, just thought all macintels came with airport cards, I have one, but I see the current Mac Pro have it as an option. I would just get the Apple Airport Extreme card for intel mac if it is appropriate, sorry I can't help with the netgear.

---

### Post by bonestonne on 2007-08-25
well, maybe its a very barebone Mac Pro, but when it got to me, its got a single dual core CPU in it, single slot for a superdrive...it looks just like a G5.

whatever.

i don't have built in airport, and i would like to use what i have available rather than buying a new airport card.

now that i actually thought about it, when i got this thing, the previous owner said it wasn't in its original case...maybe thats why i'm getting thrown off.

just annoying that i've read about people's success and i have non in OS X.

i would have gotten back sooner, but work has been taking up lots of time.

---

### Post by pxwpxw on 2007-08-26
**bonestonne**

They do look the same externally, but my PowerMac G5 has got "G5" stamped on the CPU cover inside. Also if you open "About This Mac" (System Profiler) it tells me my MacBook (intel) Processor is Intel Core 2 Duo.

If you go further into System Profiler, look at Network and PCI cards, may give a clue about what it sees.

I am thinking the Apple Airport card on previous versions does not go in a PCI slot, but in a smaller separate slot. Hence maybe linux and xp are used to PCI, but Macosx expects wireless in an airport slot. 

However, I dont know if the Mac Pro may do it differently. 

You could have a look at apple.com support info, especially about how they do Airport Extreme cards for the Mac Pro, and whether a separate pci wireless card is normally supported. 

It would also be a legitimate query for the Apple Discussions forum, macosx, networking, or bootcamp (since xp works but osx does not). It is really a question that calls for Apple expertise. 

It is much more difficult to delve into MacosX than linux.

Hope you find an answer.

---

### Post by bonestonne on 2007-08-26
well, in essence what i need is a mac OS X driver for Intel based macs for the Realtek 8187 chipset. i have a Netgear USB wireless adapter and Netgear themselves don't make OS X drivers, however i found that the chipset is the same as the Realtek. my problem is that i can't find any Intel based drivers for it. the only version i see OS X using the USB adapter is 10.3.9

---

### Post by pxwpxw on 2007-08-27
Ah - I somehow got the idea you had a PCI wirless card, but now understand its a USB wireless dongle, i.e. plugs into usb port? Or am I still wrong?


Recalling a similar experience with a usb adsl modem, which required a minor hack to the driver package information (not the binary component) to get it to work on G5/G4 in macosx10.3/10.4. There was the driver package (it was gwausb.kext) to install in /System/Library/Extensions/
Opening the package in macosx (right click, show package contents) and it shows the items, with one small binary  plus plists and Macosx startup configuration etc,).

Possibly for your device, the linux or xp binary modules/drivers might be usable for the binary, with a bit of package hacking - they are all for the same intel cpu, so the available 10.3.9 macosx ppc driver you located might be usable if the binary was replaced by an intel binary, but with the same Macosx packaging. 

I still think $50 for an apple airport card would be a good buy, but its your choice.

I think this Macosx forum is a bit below critical mass to attract much useful input, might do beterr in the Apple Intel Users.

---

