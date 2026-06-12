---
title: "what are linux restricted modules"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by tapas_mishra on 2009-11-24
I found some files like

/usr/share/linux-restricted-modules/2.6.28-11-generic/modules.alias.override/wl
/usr/share/linux-restricted-modules/2.6.28-16-generic/modules.alias.override/wl
/usr/share/linux-restricted-modules/2.6.28-16-server/modules.alias.override/wl

what do these files do how can I know more about modules.alias.override

---

### Post by editrix on 2009-11-29
Hi tapas_mishra:

I found your post because I need an explanation, too. I found an old one at [http://ubuntuforums.org/showthread.php?t=216472](http://ubuntuforums.org/showthread.php?t=216472) but it just quotes the package description:

> This package provides restricted modules for Linux version 2.6.15 on
Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.
Currently the following modules are included:
- madwifi (Atheros)
- fglrx (ATI)
- nvidia
- fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)

These modules are "restricted" because they are not available under a
completely Free licence. 

Which might as well be written in hieroglyphics for how much it  helps me. I found some of the terms by googling, but not the one I'm looking for: fwlanusb. I *think* it enables something usb to work, but I don't know what.

Sorry I can't be helpful, but at least I bumped your post.

---

### Post by linuxonbute on 2009-11-29
> **editrix said:**
> Hi tapas_mishra:

I found your post because I need an explanation, too. I found an old one at [http://ubuntuforums.org/showthread.php?t=216472](http://ubuntuforums.org/showthread.php?t=216472) but it just quotes the package description:



Which might as well be written in hieroglyphics for how much it  helps me. I found some of the terms by googling, but not the one I'm looking for: fwlanusb. I *think* it enables something usb to work, but I don't know what.

Sorry I can't be helpful, but at least I bumped your post.

This bit tells you :

"These modules are "restricted" because they are not available under a
completely Free licence. "

You have some device which has a driver which is not released under a free license. It is probably something written by the makers of the device and they do not release the source code so only they can alter/improve it.
For example, my desktop PC has an Nvidia graphics card in it. Nvidia supply a module ( driver ) which can interface it to my system.
I can install it but have to rely on Nvidia to sort out any bugs in it.
Free code would have the source with it and anyone with the knowledge could work on it to improve it.

---

### Post by jward3010 on 2009-11-29
Here's a little side note restricted modules and drivers (same thing) and why they are a bad idea, but for the moment necessary. First of all they are basically the code that makes the hardware they deal with work and communicate properly with the system. In Windows they are called drivers.

- In a few wireless cases Linux users have to use a Windows driver passed through an emulator or converter (if you like) called ndiswrapper. This system is fraught with problems for obvious reasons - for example the Linux kernel is written differently from the Windows one so the language they speak is slightly different. It also means that a lot of Linux users have terrible problems with getting these devices to work.

- nVidia make pretty good drivers for Linux (my GeForce 9400GM and 7800GTX works pretty good all the time) but nVidia have written there driver to become part of the kernel, not as a separate module. There is one golden rule about the Linux kernel: Anything that doesn't have to run within the kernel SHOULDN'T! This is done for reasons of stability, in other words if the graphics driver crashes, it won't cause the whole system to crash, just the display - which can then be restarted separately. When the driver becomes implemented tightly into the kernel then something as stupid as a display driver can bring down as entire system. This isn't a big deal on desktops (well you might disagree if you have 4 hours of a document done and BANG, it all dies) but in terms of server farms which have highly critical data it's another story.

---

### Post by editrix on 2009-11-30
Hi linuxonbute:

Thanks for the reply.

> "These modules are "restricted" because they are not available under a
completely Free licence. "

Yes, I saw that, but when I run the Gnome Hardware Drivers Manager it says I don't have any proprietary hardware. The output of lshw doesn't name any of the brands (like Nvidia) that I could find by googling.

I think what tapas_mishra and I both need, at least to start with, is a list of the various modules, and a Plain English explanation of what they do. But I can't find one.

---

### Post by linuxonbute on 2009-11-30
Well, as jward3010 said they are drivers so they, one way or another, allow a piece of hardware to be used by Linux.

I cannot really give you a list and it would probably be of little use to 
you, what would you do with it? 
As it would be a restricted driver you would only need to use it for hardware which didn't have free drivers for your hardware.

As we explained, it is used by your system. 

If Gnome Hardware Drivers Manager says you don't have any restricted drivers you don't need them or at least your hardware works fine with the free linux drivers. 

In Windows if you bought, say a webcam, it would come with drivers. Normally you would install the drivers then connect your webcam. 
Windows would say it found new hardware and incorporate them into the system so the Windows kernel and programs could use it. 

It's similar for linux and modules. 
One difference is that for most hardware linux comes with free modules and the source code is available. 

If you knew how to program and knew how to improve the code you could edit the source code and compile your own version of the software and so on.

---

### Post by jward3010 on 2009-11-30
Reading you first post again I realise that you're simply wondering what "restricted modules" are. Well, I'm in a chatty mood so here's a nice overall idea; like we said they are drivers for particular hardware that has no open source equivalent and "why" is this important you ask (well maybe you ask); 

Well, when software is open source, EVERYONE can look at it's code and see what's there, this is great for fixing bugs and finding malicious code that shouldn't be there, among many other things. We can make the hardware work to it's maximum performance without any holding back that the manufacturer might do to promote a more expensive model product. It means problems can be fixed at any particular time, you're not waiting for a release cycle that a hardware company might have and it also assists in experimental design where we can take a wireless card and make it act like something else. The manufacturer would never let you do this. This leads to fantastic innovation in how you can build Linux into anything that you like, like a network router or onto your mobile phone or MP3 player. you'll never do that with Windows or Apple OS's. A final reason, if a hardware manufacturer goes out of business that doesn't mean people suddenly cease to use the hardware, they continue to use it and if it's open source, bugs and problems can be continued to be ironed out whereas if you we're relying on the now non-existent manufacturer and the hardware had some deep future bugs it will never be fixed if they're not around anymore.

There are a few reasons for using closed source drivers; 

- The manufacturer of a particular piece of hardware doesn't want to make the driver open-source but still provides a linux driver. 

- Open-source developers have difficulty making an open-source equivalent that's stable maybe down to the complexity of the hardware and help from the manufacturer is needed (even just the source code) (a graphics card for example, pretty complex stuff).

- Linux driver developers can't write drivers for a particular piece of hardware so we are forced to use closed-source versions or worse, emulate windows drivers into the system.

- A lot of very up to date hardware would have no linux equivalent driver straight-off (although everywhere you look there's someone working on something to get a particular thing working, take 3G modems for example, because they never get the source code or the software kits cost $25,000 from the manufacturers, linux developers take guesses with the hardware and see what responds and what doesn't, until it works) unless the manufacturer decided to make one which is often rare, expect strangely enough for Intel. 

Manufacturer's are in business and they don't spend money where it doesn't matter to them - such as Linux development, on the other hand they are very responsive to Windows and maybe Apple because they sell most of their units based on these OS's.

TO GET BACK TO THE POINT: These modules are included in Ubuntu IN CASE they are needed for absolutely basic functionality like getting a wireless card working or particular firmware for some device to go through that wouldn't work apart from that. If Ubuntu was forced to use one of these restricted modules they would have shown up in "Hardware Drivers" and you would have got a notification about the fact that you're "system was using drivers that Ubuntu and Linux developers have no right to support and look after".

---

### Post by editrix on 2009-12-01
linuxonbute and jward3010, thanks for these replies. The fog is slowly disspating :-)

I guess I should explain that what I'm trying to do is reduce memory consumption. I only have 512MB, and once Firefox and Xorg are running, that doesn't leave a lot. I found a Community Doc about Low Memory Systems that suggests blacklisting some restricted modules. Then, of course, I looked at all the running processes to see what I could shut off. Some, like Bluetooth, are easy to figure out. Others, like lt (in the restricted modules) and events/0 take some research.

The upshot of your explanations is, since I don't have the hardware the modules aren't running anyway. Which means I don't have to take my life in my hands and screw around with a system I don't understand very well :-)

As to tapas_mishra's problem, I haven't encountered it yet. Apologies if I hijacked his thread.

---

### Post by tapas_mishra on 2009-12-01
> **jward3010 said:**
> R
There are a few reasons for using closed source drivers; 

- The manufacturer of a particular piece of hardware doesn't want to make the driver open-source but still provides a linux driver. 
.

- A lot of very up to date hardware would have no linux equivalent driver straight-off (although everywhere you look there's someone working on something to get a particular thing working, take 3G modems for example, because they never get the source code or the software kits cost $25,000 from the manufacturers, linux developers take guesses with the hardware and see what responds and what doesn't, until it works) unless the manufacturer decided to make one which is often rare, expect strangely enough for Intel. 
.
Hmmm my system uses a Broadcom chipset and on boot there is a message that there is proprietary driver 
from Ubuntu it is a Dell 1440 Laptop.

---

### Post by linuxonbute on 2009-12-01
> **tapas_mishra said:**
> Hmmm my system uses a Broadcom chipset and on boot there is a message that there is proprietary driver 
from Ubuntu it is a Dell 1440 Laptop.

Does it say it is being loaded or just that there is one you can use?

---

### Post by jward3010 on 2009-12-01
If I'm reading correctly what you said, the driver isn't as such "from" Ubuntu, they don't make it, improve it or maintain it. It's simply sitting in their repositories available for download.

---

