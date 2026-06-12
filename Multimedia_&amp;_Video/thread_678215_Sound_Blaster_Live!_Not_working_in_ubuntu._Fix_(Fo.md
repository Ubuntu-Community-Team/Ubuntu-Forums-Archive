---
title: "Sound Blaster Live! Not working in ubuntu. Fix (For me anyway)"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Barocius Grimaldi on 2008-01-25
Alright, Earlier today I was trying to figure out why my SB Live! card wasn't friggin' working in Ubuntu. I had come across this forum in my search for answers and came across a couple posts (Through a Google search) that dealt with this problem... I tried some of the things suggested, but got absolutely nowhere and it appeared there were some other people not being able to figure out what was going on with their sound card (SB Live! particularly) I can't find those particular forum posts/threads, so I'm posting what I've found to be the problem for me. 

Ok, all the posts I read (And I didn't read them all, so forgive me if this is dead wrong) seemed to revolve around a software fix, and I too was thinking it was as such as well (It usually is these days) but I remebered something about dealing with these SB Live! cards in win98, 2000 and XP (The main OS's Ive played with, I'm just starting on Linux) and that was the system would become unstable/crash in an endless loop (Win98 especially) If you put the sound card, mixed with other pci devices in all but a certain order. For some reason or another these sound cards didn't like it very much if you put them in a particular Pci slot and not the other (I always experienced less problems the higher it was on the pci slots, that is; closer to the video card/agp slot) I've had many a windows 98 installation die horribly simply because I put the sound card in a different slot after an upgrade.

Well anyway, in summary, I think that some of the people whom are having problems with their SB Live card under Ubuntu would do well to switch around their Sound card to a different pci slot/take out other pci expansion cards/switch them around. It might solve your problem. It solved mine quite nicely :popcorn:

Also, heres my system stats, just so ya know what I was dealing with: (Sorry can't remember everything right off the top of my head)
Motherboard - ASUS CUV4X, latest bios
Processor - Celeron 1100mhz 256k cache (PIII architecture)
HDD: 40GB Maxtor
RAM - 384 meg pc-100
Vid - Voodoo 3 16mb
Ethernet Card - 3com brand pci card
Wireless - MSI branded wireless card

Apologies if someone else has already posted this possible solution.

---

### Post by crjackson on 2008-01-26
This happens because your sound card was sharing an IRQ with another device.  PCI slots are often assigned to share an IRQ with another particular PCI slot.  If you have a device that can't share IRQ's then you get this problem.  The solution as you have already found is to move the device to a slot that isn't sharing an IRQ with another device.

---

### Post by Barocius Grimaldi on 2008-01-27
Well, I Should have also stated that this particular computer wasn't having any problems in winxp, this was what threw me off initially, I just figured the IRQ assignment would be the same/it wouldn't make a difference as to the devices functionality from OS to OS provided you have working drivers. 

I noticed a post somewhere that said if it works in xp then you know it's not hardware, evidently, depending on how you think of IRQ assignments, that statement would be false in my case.

---

