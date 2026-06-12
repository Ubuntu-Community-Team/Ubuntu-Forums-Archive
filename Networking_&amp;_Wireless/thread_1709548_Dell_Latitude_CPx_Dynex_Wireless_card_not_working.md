---
title: "Dell Latitude CPx Dynex Wireless card not working"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by chrisman01 on 2011-03-18
Okay, I've been lurking on these forums for years now, figured it was time to man up and ask for help officially.

I have a 10 year old Dell Latitude CPx that has no ethernet or modem ports, and the only way to connect to the internet is the Dynex Wireless G DX-BNBC PCMCIA card.

It came with Windows 98, and I put Xubuntu on it for a while.  I believe it was Xubuntu 8 or 9.

Back then I had no clue what to do whatsoever, so after a couple weeks removed it and put Windows 2000 on it.  It worked, I used it for a while, but it was slow and 2000 took up a lot of space on the 12gb hard drive after all the updates.  I left it forgotten and gathering dust for the past year.

Then a few days ago I discovered Lubuntu 10.10, and from what I've seen so far it is definitely a lot more compact and faster than 2000.

However, the wireless card still won't work.  It's *somewhat* recognized, because whenever I unplug it and plug it in a bubble pops up saying "you've been disconnected from the network"... which is odd, since it never says I'm connected, and says that the firmware is missing for this card.

Anyway, I discovered something this time.  By running "lspci -nn | grep -i 14e4":

```
06:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```It turns out this Dynex is a Broadcom clone.  So I used my full time laptop to find the drivers and transferred them to the CPx.

However, it seems every tutorial I find involves using apt-get or some other means that involves connecting to the internet.

Is there a way to get this card working without connecting to the internet, or should I abandon this project permanently?

---

### Post by Jared Norris on 2011-03-22
I've had this problem in the past and found [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection]("https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection") to be a useful reference. 

I hope that helps.

---

