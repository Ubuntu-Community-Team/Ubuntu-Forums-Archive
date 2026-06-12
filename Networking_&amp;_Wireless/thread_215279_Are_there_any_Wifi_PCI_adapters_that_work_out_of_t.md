---
title: "Are there any Wifi PCI adapters that work out of the box?"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by FooAtari on 2006-07-13
Are there any Wifi PCI adapters that work out of the box, or at least with minimal fuss?

I have nearly had enough of my my Asus WL-138GE (Broadcom 4138 chip)...


Cheers

---

### Post by tturrisi on 2006-07-13
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by sidlinux on 2006-07-13
The following cards work right out of the box.  However, you may have to get them on eBay since you won't find them in stores.

[LIST]
[*]Linksys WUSB11 Version 2.4 802.11b
[*]Dell Truemobile 1150 PCMCIA 802.11b
[*]D-Link DWL 650
[*]D-Link DWL-G650
[/LIST]

Don't get the new ones yet.  They do NOT work out of the box or with the help of NDISWrapper or Linuxant.

The Dell Truemobile 1300 (802.11g) doesn't work out of the box, but with the help of Linuxant, I got it to work.  In fact, your Asus WL-138GE (Broadcom 4138 chip) may work with the help of Linuxant.  Just go to [http://www.linuxant.com](http://www.linuxant.com) and give it a try.

Good luck.

Sidney:)

---

### Post by Efrain Valles on 2006-07-17
Does the D link dwl 650... really work out of the box?

I upgraded from Hoary to Breezy and Lost my connectivity...

I am seriously thinking about a installing dapper... I ran the live cd and it worked fine!! however the live cd for breezy also worked with my card and after I upgraded they card failed to work... good thing I can still use my old Kernell... that supported my Card... Does anyone know why???
](*,)

  I hate wireless connections they are such a pain...

---

### Post by tturrisi on 2006-07-17
Many cards work out of the box w/ no effort, however one must pay attention to version numbers of the card.  For example, the dwl650 of several years ago has a different chipset than the current.  The newer dlink 650 & 630 use an atheros chipset which do work out of the box along with installing linux-restricted-modules.

I researched pcmcia cards & linux for a month prior to buying the cards I use because I wanted zero headaches and ability to use the cards w/ kismet.

---

### Post by Efrain Valles on 2006-07-17
the newer you mean???

I have a DWL 650+

does the Plus make it  a newer model (D-link considers it outdated and they offer no support for it anymore... No dirvers no anything)... I also saw DWL G650 reading a post somewere... I member Hoary worked it out of the box... now... Breezy.. has been a different story... altogether...

thanks for your insights...

gotta love the feeling of not being alone in this ubuntu world...

---

### Post by tturrisi on 2006-07-17
product ID 	vendor & product code 	host I/F 	chipset 	driver 	works with Linux 	comments

DWL-650+ 	 	 Cardbus 	 TI 	 	 grey  	 Tx power 15 dBm; 256-bit WEP; development: [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

DWL-650+ 	man:168c dev:0013 	Cardbus 	Atheros 	Mad WiFi 	green 	version A1 works; driver available at: [http://madwifi.org](http://madwifi.org)

---

### Post by Efrain Valles on 2006-07-17
DWL-650+
gray cardbus...
H/W B 1  F/W 1.9
:-D

---

### Post by weekend warrior on 2006-07-18
The Free Software Foundation has [a good list of linux friendly cards]("http://www.fsf.org/resources/hw/net/wireless/cards.html").

I got a Belkin F5D7010 card from this list for my laptop and it worked out of the box with no configuration needed; just plug n' play. Looks like you're wanting something for desktop; that'd be the [Belkin F5D7000]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136479").

As already mentioned, Ebay is your friend for these models. You can usually pick one up on the cheap there.

Good on you for seeking out a sane alternative and not just slogging on with what you have. If only more people would do the same instead of taking the "damn the torpedoes!" :rolleyes: way.

---

### Post by Bezmotivnik on 2006-07-18
> **FooAtari said:**
> Are there any Wifi PCI adapters that work out of the box, or at least with minimal fuss?

Define "work."

Seriously, this is not a meaningful question otherwise.

Full, easily-accessible, current-tech features like on-demand WPA2/AES for multiple APs, etc.?

I honestly don't know of any.  It's a real problem. ](*,)

---

### Post by tturrisi on 2006-07-18
> **Efrain Valles said:**
> DWL-650+
gray cardbus...
H/W B 1  F/W 1.9
:-D
To get that card working you will need to install the linux-restricted-modules via Synaptic which contain the mad-wifi drivers for atheros chipsets.

---

### Post by chris.raighn on 2006-07-31
I've found that some of the 2Wire PCMCIA cards work out of the box too (Wireless B, non-branded). I have a dead USB adapter from them, and I took it apart and it is just a USB to PCMCIA Adapter and the card is not marked and works perfect even in installation.
Agere chipset

It is also _FAIRLY_ painless to get the Motorola WN825G v3 working. There was a few hitches, but then it worked.


C.R.

---

