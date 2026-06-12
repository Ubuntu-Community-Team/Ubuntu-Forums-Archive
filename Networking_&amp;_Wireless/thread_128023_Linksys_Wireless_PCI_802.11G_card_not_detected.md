---
title: "Linksys Wireless PCI 802.11G card not detected"
date: 2006-02-10
forum: Networking &amp; Wireless
---

### Post by JShamoon on 2006-02-10
Hey guys, I just installed breezy and it does not detect my card in the networking setup.  If I go into device manager, I can see the card, but I don't see it in the network setup screen.  Nor can I "add" a card. 

I'm pretty new to Linux, so any assistance is greatly appreciated.

Thank you in advance. :)

---

### Post by waldorf on 2006-02-10
Welcome to the club of people tearing their hair out over Linksys cards.

Here is one post that I found helpful

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=remove+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=remove+ndiswrapper)

this is another

[http://www.ubuntuforums.org/showthread.php?t=99490&highlight=Pleasant+Wireless+Experience](http://www.ubuntuforums.org/showthread.php?t=99490&highlight=Pleasant+Wireless+Experience)

you will find that there is a lot of threads out there on this issue. which one will be most helpful depends on the particulars of your card.

---

### Post by JShamoon on 2006-02-10
[QUOTE=waldorf]Welcome to the club of people tearing their hair out over Linksys cards.

Here is one post that I found helpful

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=remove+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=remove+ndiswrapper)

this is another

[http://www.ubuntuforums.org/showthread.php?t=99490&highlight=Pleasant+Wireless+Experience](http://www.ubuntuforums.org/showthread.php?t=99490&highlight=Pleasant+Wireless+Experience)

you will find that there is a lot of threads out there on this issue. which one will be most helpful depends on the particulars of your card.[/QUOTE]
Thank you!  I will try this tonight.

---

### Post by Kashirigi on 2006-02-10
[QUOTE=JShamoon]Hey guys, I just installed breezy and it does not detect my card in the networking setup.  If I go into device manager, I can see the card, but I don't see it in the network setup screen.  Nor can I "add" a card. 

I'm pretty new to Linux, so any assistance is greatly appreciated.

Thank you in advance. :)[/QUOTE]

I have the same card as you; I installed ndiswrapper and used the driver from the CD that came with the card. If you're using WPA, you might also want to install wpa_supplicant. The links above should help you -- I got all of my help from these boards.

There's also 
[https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)
[http://flacknews.blogspot.com/2005/11/use-ndiswrapper-to-setup-wireless-in.html](http://flacknews.blogspot.com/2005/11/use-ndiswrapper-to-setup-wireless-in.html)

and for wpa_supplicant
[http://ubuntuforums.org/archive/index.php/t-90450.html](http://ubuntuforums.org/archive/index.php/t-90450.html)


The major problem I had was a constantly dropping connection (which later affected any OS). It turned out to be a crappy power bar spiking the router and causing it to crash. But I digress.

---

### Post by UbuntuLinuxUser on 2006-02-12
ooo....gone to try it out!

---

### Post by UbuntuLinuxUser on 2006-02-12
didn't work...

---

