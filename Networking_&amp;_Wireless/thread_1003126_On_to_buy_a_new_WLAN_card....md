---
title: "On to buy a new WLAN card..."
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Lupusceleri on 2008-12-05
Heyhey there,

Since my old WLAN card is well, officially dead, I need to get a new one. My local computerstore ([www.mycom.nl](www.mycom.nl)) has the choice between a couple of cards, from brands NetGear and Linksys, but as far as I know neither of these are supported very well under linux. However I can always go and troll ebay.

Now my laptop, has a very good WLAN card. It's a DELL Inspiron 6400 laptop, with as WLAN card the "Intel Pro Wireless 3945ABG Network Connection" (or so says Windows), and was natively recognized by Xubuntu. Also it has great range, where the other network cards in my house can barely maintain a connection the laptop works at a normal signal and speed. :) So something comparable to that, but then in PCI form and stuffs, would be nice.

My current computer is an AMD64 3000+, with an A8N-SLI motherboard.

The most important requirements for my new card are:

a) 801.11g (or 802.11n, if linux can handle that yet)
b) moveable antenna (IE not an antenna that's stuck to the back of my computer), because my computer is rather far away from the access point. So to illustrate that: _[this](http://users.telenet.be/laboee/Gino/Wlan-antennes/wmp54g.jpg)_ is the thing I don't want, _[this](http://images.asia.ru/img/251403/WG-108PCIL.jpg)_ is the thing I do want.
c) PCI card
d) of course compatibility with Ubuntu Intrepid. ;) Preferably without ndiswrapper as I have a bloody trauma from that thing + the terminal, when I tried it a few years ago. :-\" Then again software improves, so if you guys are certain it actually works now, and doesn't slow my system down alot, I guess I can try it again.
e) ability to use WPA-personal with TKIP
f) costs around or less than 50 euro

Anyhow, are there any cards you guys would recommend? Right now I'm thinking the Netgear WN311B looks pretty decent - assuming it runs under Ubuntu Intrepid of course?

Thanks in advance,

Lup.

PS: I tried looking up the stuff found in searches/wikis, like the compatible WLAN card list and the madwifi project, but I couldn't really find the cards my computer company was selling in there and besides I can't see the other properties of the card there.

---

### Post by Lupusceleri on 2008-12-06
Ok, trolling the forums I found an old thread ([click](http://ubuntuforums.org/showthread.php?t=362616)) about the netgear card, and it appears to have a Broadcom chip. From what I've heard here, Broadcom is something you avoid like the pest! :D

The same's been done for the linksys card that met my requirements and guess what - broadcom.

-----------

So I trolled ebay for a bit and came up with the RTL8185L chipsetted card: [click](http://cgi.ebay.nl/54Mbps-REALTEK-PCI-Card-Wireless-Lan-Adapter-1m-Antenne_W0QQitemZ320322627612QQcmdZViewItemQQptZDE_Computer_Peripherie_Netzwerk?hash=item320322627612&_trksid=p3286.c0.m14&_trkparms=72%3A1399|66%3A2|65%3A12|39%3A1|240%3A1318)

The seller claims that it works on Linux ("CE Linux(2.6.x)"), but when searching on the forums I see there have been a zerg of problems with Hardy and the RTL8185L chipset. Is this issue solved in Intrepid?

-------------

Trolled ebay some more - found [this](http://cgi.ebay.nl/Wireless-LAN-WLAN-108-Mbit-PCI-Karte-Antenne-8-dBi_W0QQitemZ110314585007QQcmdZViewItemQQptZDE_Computer_Peripherie_Netzwerk?hash=item110314585007&_trksid=p3286.c0.m14&_trkparms=72%3A1399|66%3A2|65%3A12|39%3A1|240%3A1318).

Seller claims it "LAUFT AUCH UNTER VISTA UND LINUX" and that it has an Atheros chipset. I couldn't find out what brand it is for the life of me. But since I heard Atheros is a linux-friendly chipset, I guess that's okay?

Anyway. Any suggestions?

---

### Post by Lupusceleri on 2008-12-06
Found a new best [candidate](http://www.edimax.eu/en/produce_detail.php?pl1_id=1&pl2_id=44&pl3_id=86&pd_id=1). Edimax EW-7128g.

It even says on the official site that it works with Linux (so I can bug them too if it doesn't happen to work :p ), it is mentioned on [www.ubuntuhcl.org](www.ubuntuhcl.org) as "working out of the box", it has special drivers for my 64 bit Vista installation, it's cheap, it has an antenna that I can move around, it's for PCI. And as icing on the cake it supports WPA. :)

I'll probably go see if I can buy one in a bit, so unless I hear extreme sounds of negativity here I'll be chiming back in with how it works out in a few.

---

### Post by Lupusceleri on 2008-12-10
The Edimax EW-7128g arrived today.

I plugged it in, booted up Ubuntu, and without even touching the keyboard or mouse it already connected to the internet. :D

I can recommend this card to anyone using Ubuntu Intrepid! :)

For those interested, here's the lspci entry from the card: 

```
05:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

---

### Post by aely on 2008-12-15
> **Lupusceleri said:**
> I can recommend this card to anyone using Ubuntu Intrepid! :)

I'm interested. WPA works also with this card?

---

### Post by Lupusceleri on 2008-12-15
> **aely said:**
> I'm interested. WPA works also with this card?

> **Lupusceleri said:**
> And as icing on the cake it supports WPA. :)

And besides that, I can tell you I've used WPA-Personal and WPA2-Personal without a problem.

---

### Post by TCWriter on 2009-01-17
So has anyone found an 'n' standard PCI card that works as well as the Edimax 'g' card does? 

It seems the RaLink chipsets are very Linux friendly, but I don't know which new PCI cards use the RaLink chipsets.

---

### Post by ariscanete on 2010-02-04
Aside from Edimax EW7128G WiFi PCi card...are there any other WiFi PCI card that is completely compatible with Ubuntu?  

I tried one WiFi PCi card with a RTL8185L chipset. Its detecting our WiFi Router but it failed to connect even if its already Unsecured...

---

