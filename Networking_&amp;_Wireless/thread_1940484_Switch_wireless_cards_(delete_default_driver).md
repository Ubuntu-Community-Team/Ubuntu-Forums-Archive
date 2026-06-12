---
title: "Switch wireless cards (delete default driver)"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by grnorris on 2012-03-13
I'm working on a friends computer (Win7 x64 and Ubuntu 12.04) which has both a built in (Crappy) wireless card and a Netgear N300 card.  Following instructions I found online I managed to install the drivers (or at least I'm pretty sure they're installed) but because the crappy internal card is recognized (ath9k) I can't seem to use the better card.  The N300 is installed via ndiswrapper and shows up as working in ndiswrapper but doesn't show up if I run iwconfig.

I'm thinking I just need to remove the default driver and that should make it default to the new one (I'm afraid if I just remove the old card it might cause other issues).

Any help would be greatly appreciated.

Other info:
Ubuntu is installed by using pendrivelinux.

I'm not completely new to linux but it has been a few years since I last played around so I'm still consider myself a novice.

---

### Post by gordintoronto on 2012-03-13
You are using unreleased software, so you should expect problems.

Why not Ubuntu 11.10?

---

### Post by grnorris on 2012-03-14
> **gordintoronto said:**
> You are using unreleased software, so you should expect problems.

Why not Ubuntu 11.10?

Pendrive Linux gave me the option so I decided to go with the most up to date version(honestly I didn't even think about the fact that it would be unreleased).  Regardless it seems to be working just as well if not better than 11.10.  From what I've read my situation would usually result in Ubuntu simply freezing up (since their should be two things fighting for wlan0).  My problem is simply that their is already a wireless card controlling wlan0 and I need to use get rid of it and use a different one (Thus delete the default driver ath9k).

---

### Post by gordintoronto on 2012-03-14
I can understand wanting to use the faster card, but if I had to choose between an Atheros and NDISwrapper, I would go with the Atheros every time.

If there are any 802.11G devices on the network, that's the speed it will work at.

---

### Post by grnorris on 2012-03-14
> **gordintoronto said:**
> I can understand wanting to use the faster card, but if I had to choose between an Atheros and NDISwrapper, I would go with the Atheros every time.

If there are any 802.11G devices on the network, that's the speed it will work at.

It's not just faster but functional.  The built in card has a horrible antenna and will randomly lose the connection where as the USB card should work anytime.  In any case I didn't start this thread for a debate but rather an answer:  How can I get Ubuntu to use the other card, if it's deleting the default driver as I suspect how do I do that.

---

