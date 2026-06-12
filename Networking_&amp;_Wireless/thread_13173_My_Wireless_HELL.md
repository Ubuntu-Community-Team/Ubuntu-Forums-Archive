---
title: "My Wireless HELL"
date: 2005-01-29
forum: Networking &amp; Wireless
---

### Post by Leebobs on 2005-01-29
](*,) We have a wireless network at home and I am banned from running cables...

So I'm trying to get Linux working with either one of my Wireless cards, both are Netgears:
MA111v1
MG311v2

Both work well in XP, any idea if the next version of Ubuntu will support them? Or whether it supports:
Asus Wireless WL-138G PCI Adapter
Belkin F5D7000UK 802.11g Wireless PCI Adapter 

Which I will happly buy to get Internet, e-mail, etc in Linux

---

### Post by flyfishin on 2005-01-29
Wireless can be an adventure under Linux. You generally need to know the chipset the card uses to really know if it will work.  Although some distros now show a list of compatible cards in the network setup section. Many manufacturers will have v1, v2, v3 of a card and each version uses a different chipset.  Some work, some don't.  It's a bit frustrating. I found this site which discusses the MA 111 

[http://lists.linux-wlan.com/pipermail/linux-wlan-user/2004-September/012825.html](http://lists.linux-wlan.com/pipermail/linux-wlan-user/2004-September/012825.html)

This site lists cards that do/don't work with the wlan drivers:

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

The madwifi drivers support a different chipset and a list of supported cards can be found here:

[http://customerproducts.atheros.com/customerproducts/](http://customerproducts.atheros.com/customerproducts/)

The madwifi drivers are stored in the linux-restricted-modules package.

There are other drivers for different cards out there but I can't remember them all at the moment.

I know this doesn't help with your question of whether or not your cards will work with the next version of Hoary, it really depends on the underlying drivers, but if you decide to buy something different these should help you pick one that is known to work with Linux.

---

### Post by flyfishin on 2005-01-29
I forgot about linuxant.  They make a driver loader that allows you to install  Windows drivers on linux.  I have no clue how it works but I've heard others using it successfully.  I believe the cost is $20.

---

### Post by spockster on 2005-01-30
i have just finished setting up a ma111 usb adapter ,which is all working fine now.im running warty 4.10  and the modules i needed were already instlled.what does ifconfig show?

---

### Post by Kinimod on 2005-01-30
[QUOTE=spockster]i have just finished setting up a ma111 usb adapter ,which is all working fine now.im running warty 4.10  and the modules i needed were already instlled.[/QUOTE]
Can you explain how you succeeded in setting the MA111 up, please? I've this adapter too ...

---

### Post by Domhnull on 2005-01-30
I don't know if you'd be interested in this, but I followed the suggestion of someone over at linuxquestions.org and bought a Linksys Wireless Ethernet Bridge.  It's a driverless device - just plug it into an ethernet card.  I have a dual boot machine (although it is extremely rare these days that I boot to Windows) and the device works well under both systems.  In fact my connection is much faster than it was with an internal wireless card.  So much so that I went and bought one for my wife's Windows machine just to speed things up.  I did set it up under Windows, the Linksys configuration utility is a Windows app.  There is a web interface though so you might be able to do the setup just by going to that but I'm not sure.  Anyway it made my whole "wireless hell" evaporate.

---

### Post by king_arthur on 2005-01-30
[QUOTE=flyfishin]I forgot about linuxant. They make a driver loader that allows you to install Windows drivers on linux. I have no clue how it works but I've heard others using it successfully. I believe the cost is $20.[/QUOTE]
      No need to go to the competition, and pay for it, we have it all in home.
      Try [NdisWrapper]("http://ndiswrapper.sourceforge.net/"), it is a small module which allows for using the win-XP drivers you got together with the card. You can install it if you have "Universe" enabled, by simply typing *sudo apt-get install ndiswrapper*.
      
 It did the job for me with an obscure, no name, Taiwaneese card hosting a Realtek chip. There is plenty of information around and a good howto in the Ubuntu FAQ.
      
 Hopefully it will turn your hell into heaven. Good luck.

---

### Post by flyfishin on 2005-01-30
[QUOTE=king_arthur]No need to go to the competition, and pay for it, we have it all in home.
      Try [NdisWrapper]("http://ndiswrapper.sourceforge.net/"), it is a small module which allows for using the win-XP drivers you got together with the card. You can install it if you have "Universe" enabled, by simply typing *sudo apt-get install ndiswrapper*.
      
 It did the job for me with an obscure, no name, Taiwaneese card hosting a Realtek chip. There is plenty of information around and a good howto in the Ubuntu FAQ.
      
 Hopefully it will turn your hell into heaven. Good luck.[/QUOTE]

I knew I was missing something.  Good info.

---

### Post by king_arthur on 2005-01-31
flyfishing,
  
sorry but the correct spelling is *sudo apt-get install **ndiswrapper**-**utils**.*
  And the howto can be found [here]("http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper/view?searchterm=ndiswrapper") (please post back the results)
  
  Best of luck

---

