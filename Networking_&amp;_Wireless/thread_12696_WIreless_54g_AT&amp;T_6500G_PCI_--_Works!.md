---
title: "WIreless 54g AT&amp;T 6500G PCI -- Works!"
date: 2005-01-26
forum: Networking &amp; Wireless
---

### Post by holycow on 2005-01-26
I just purchase three 802.11g 54g AT&T 6500G PCI adapters from CompUsa for $11.99 per card (On Line Price Only) hoping that they would "just work" with Ubuntu.

They do!

I used the networking setup in Gnome and the card was already reconized under the Wireless Option.

Kernel
uname -a
Linux ubuntu 2.6.8.1-3-386 #1 Thu Nov 18 11:47:33 UTC 2004 i686 GNU/Linux

Here's what it added to  /etc/network/interfaces

iface ath0 inet dhcp
name Wireless LAN card
wireless_essid the_pasture

auto ath0


I since then have enabled WEP....

I don't know if this is a duplicate post, but it works!
This message was typed on the wireless connection.



G' Luck!
-j0h/\/

---

### Post by king20878 on 2005-01-31
Yup. I picked up the same card a few weeks ago, and it has been working flawlessly with my warty install and the hoary livecd as well.  Highly recommended.

---

### Post by grakhul on 2005-03-05
Wireless 54G AT&T 6700G works as well.  I saw this post and went to the comp USA website.  The 6500G listed above is for a puter with a pci slot. I saw a PCMCIA version available (6700G)and picked it up for my laptop,which has UBUNTU installed.  It worked without a hitch.  UBUNTU detected the card.  All I had to do was enter my network settings and it started automatically.  Pick up this card!!  it is only 9 dollars and has a great connection!

---

### Post by [pl]ice on 2005-05-27
i got EXCEL wless PCI ,  PLEASE don't buy this one!! Comes with acx chip, full of rubbish, i'm buying other one, and this one goes into the bin!!

---

