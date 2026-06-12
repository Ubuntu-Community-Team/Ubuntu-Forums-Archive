---
title: "Are there any wireless cards that work out-of-the-box with Dapper?"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by calcifer on 2006-06-04
With all of the traffic about wireless problems in Dapper, I was wondering if there are *any* cards that actually work correctly out-of-the-box.

I've spent most of the day fighting to get my USB wireless card (Zonet ZEW2500P) to work with Kubuntu Dapper on my desktop. ](*,) Unfortunately it looks like there's a known error in the rt2500usb driver that causes it to always hang the system on ifup.

I'm planning to return that card (since I purchased it very recently). But with what should I replace it? Does there exist a PCI or USB wireless card that just-plain-works (no firmware splicing, no kernel modification, no unreliable /etc hacks, ...) under Dapper? Ideally with WPA encryption support?

(Edit: driver is rt2500usb, not ra2570, oops)

---

### Post by jbrader on 2006-06-04
The Intel Pro 2200BG in my laptop worked out of the box.

---

### Post by calcifer on 2006-06-04
[QUOTE=jbrader]The Intel Pro 2200BG in my laptop worked out of the box.[/QUOTE]
Unfortunately I'm looking for desktop cards; is there a desktop analogue of that card?

---

### Post by polo_step on 2006-06-04
[FONT="Courier New"]The tough part is that this mainly seems to revolve around what chip is in the device and about the only way to know for sure with a lot of them is to break the unit open.  Knowing the device name of one that works may be of no use as the circuits change and the model names stay the same.  I was down buying wireless devices to experiment with tonight and there were PCI wireless cards that were in identical manufacturer packaging, same UPC, everything, and yet were COMPLETELY different cards. :confused: [/FONT]

---

### Post by lynxus on 2006-06-04
From what i can see in a lot of posts is that ubuntu does support a fair few cards out the box, but i cant remember what.. however quite a lot of cards seem to be detected but cant be used as ubuntu doesnt have the full set of drivers and firmware.
It seems that fwcutter can resolve a LOT of issues people are having by inserting the windows version of the firmware.

I would recommend using any card that has a broadcom chipset and if any problems arise use the following post to help..

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)


Hope this helps ;)

---

### Post by calcifer on 2006-06-04
I did see that walkthrough; that's what I meant by "firmware splicing" in the original post, and I'd really like to avoid it, especially since I'm installing at least twice. It does seem like the best of the bad solutions though.

Another problem: Which cards have Broadcom chipsets?  I'd like to know this before I even buy the card, so lspci is no help. (Though given what polo_step has said, this may be impossible to determine *a priori*).

---

### Post by Skye on 2006-06-04
Any cards with Atheros cipsets are supported out of the box by the Ubuntu restricted modules package-  I have a laptop, and my Netgear WG511T worked out of the box fine on Dapper.

Since you have a desktop, I'd say look at [this]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards") entry in the wiki for a compatible card.  Hope this helps!

---

### Post by calcifer on 2006-06-04
I saw that listing too; unfortunately that indicates compatibility with some Ubuntu version, not with Dapper specifically. A "Yes" entry could be a Breezy Yes or even a Hoary/Warty Yes, and say nothing about Dapper; the only way to be sure is to see a Dapper confirmation in the notes.

To save future readers some time, here's a list of all the cards in that wiki that were claimed to work out-of-the-box in Dapper:

Hawking HWC54D (Ralink RT2500)
MSI MP54G4 (Ralink RT2500)
ADDON ADD-GWU180 (zd1211)
D-Link DWL-G122/B1 (Ralink RT2500)
Linksys WUSB11B Ver.2 (?)

It looks like the RT2500 driver is good news, though that's to be expected since the community has open-source access to it (although the RT2500USB driver is not so happy; see original post).

Looking for desktop cards, so the MSI is a no-go. Unfortunately, I haven't actually been able to find any of the other models for sale (newegg). There's a DWL-G122 but it's not B1, and everything else is a mystery.

---

### Post by parksobong on 2006-08-17
If you use ndiswrapper with the original driver included in the OEM CD for the ZEW2500P, it works fine. It worked for me in Ubuntu 6.06.

---

