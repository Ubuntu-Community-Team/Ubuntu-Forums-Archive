---
title: "Second Wireless Card Setup"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by radioraheem on 2009-03-20
I'm trying to fix up a laptop for a friend, 8.10 is installed and running smoothly.

The laptop has an old internal wireless card that gets terrible signal reception no matter where it is.  I am trying to setup a PCMCIA Linksys WPC54G v.5 card.

lspci, network manager, etc all show the card is present but there are no activity lights on the card, and I cannot seem to figure out how to get gnome's network manager to use the new card.

I've been searching the forums for quite a while now and haven't found anything too useful, too many people out there asking for help with specific wireless cards and issues, couldn't seem to find a simple guide similar to "here's how you setup a second wireless card and make it the primary device" type of guide.

Anyone know what I'm missing or can someone point me in the right direction?

Thanks in advance!

---

### Post by radioraheem on 2009-03-23
I can't remember the last time I bumped a post, but...... bump (sorry)

Anyone?  I thought this would be a fairly routine question for laptop users, internal wireless cards can die, and the easiest way to replace them (if possible) is to just stick a card in there (better reception regardless).

I'll be happy with a simple "-link- here ya go newb" if anyone can help.

Apologies in advance if my google-and-ubuntu-forum-searching-skills have failed me and I missed an easy answer/page/guide/etc.

Thanks

---

### Post by theozzlives on 2009-03-23
Why don't you blacklist the old card?

---

### Post by radioraheem on 2009-03-24
So I blacklisted the card using the following:

sudo modprobe -r ath_pci

then vim'ed /etc/modprobe.d/blacklist and added:

blacklist ath_pci

I restarted the system and the internal wireless stopped working, but the external card is not being used by the GUI tools in gnome.

On a side note, does lspci show device info even if it has been blacklisted?  I see a line for "0b:00.0 Ethernet Controller:  Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)"  and another line for the internal Atheros card, so I'm assuming lspci always shows device info regardless of mod status.

Any ideas as to how I make the gnome network tools work with this card?  I did some research before purchasing it and was told this model was a good choice for ubuntu laptops.

Again, thanks in advance for any help.  Much appreciated!

---

### Post by radioraheem on 2009-03-24
Did some more research on this card and it looks like ndiswrapper is about the only way to go.  

Drat.

I'd managed to run linux for 4 years without having to use ndiswrapper.  Oh well.

If I have any further questions I'll update later.  Thanks for the advice!

---

### Post by radioraheem on 2009-03-26
Does anybody know if there's a driver solution available for this Marvell chipset similar to the solution given in this forum thread?

[http://ubuntuforums.org/showthread.php?t=993193](http://ubuntuforums.org/showthread.php?t=993193)

I would really like to be able to just install a module/driver/etc and have it work, but I don't know how to figure out what driver might work with it.

All of the other threads I'm reading usually go something like "Oh, you have X chipset, use the driver called 'blah' " without ever explaining how they got that driver name from the chipset name.

As always, thanks in advance for everyone's help.

---

### Post by captaino on 2009-03-26
with my pci wireless card i did use ndiswrapper and used the driver off the cd that it came with.  WOrks like a charm right now.

---

