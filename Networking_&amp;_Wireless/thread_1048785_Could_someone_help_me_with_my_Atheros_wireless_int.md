---
title: "Could someone help me with my Atheros wireless internet connection?"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by bobleny on 2009-01-23
Could someone help me with my Atheros wireless internet connection?

What I can't figure out is that ndiswrapper no longer has drivers for download (apparently).

After a bit of research, I found that I shouldn't need ndiswrapper for my network card anyways...
[http://www.atheros.com/news/linux.html](http://www.atheros.com/news/linux.html)
[http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

So I searched for Ubuntu and Atheros and found this guide:
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

I followed the guide except instead of the wget, I downloaded the latest version from madwifi:
0.9.4

Then, when it told me to make install, the program told me that the drivers where already installed. It said I should type in "r" to remove the previous version and install the new version. So I did.

I did the modprobe and restarted my computer, nothing. It still doesn't work...

Can anyone help me with this problem?


lspci:
```

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

lspci -n:
```

06:00.0 0200: 168c:001c (rev 01)

```

I am running Kubuntu 8.04

------
Also, under the Hardware Drivers menu, it says, "This driver is necessary to support the hardware, there is no free/open alternative." This is clearly not true... How do I tell the ubuntu team of this?

Further more, if the "HAL" driver is loaded, why doesn't it work?


I'm confused, lost and frustrated.

Please help, thanks!

---

### Post by bobleny on 2009-01-26
Every time I make a topic... :'(

---

### Post by tragicglee on 2009-01-26
> **bobleny said:**
> 
Also, under the Hardware Drivers menu, it says, "This driver is necessary to support the hardware, there is no free/open alternative." This is clearly not true... How do I tell the ubuntu team of this?


Actually, It *is* true :P

The driver available under the Hardware Drivers menu option *is* madwifi, and madwifi contains a proprietary (closed source) Hardware Abstraction Layer (err, I think that's what HAL means). It's free as in beer, not free as in open (or speech). Openness is the 'free' we care about.

I'm slogging through my own Atheros/8.04 nightmare at the moment [and have been for months], and wireless is not my strong point, so I'm probably not going to be able to help you, but... what happens when you run **ifconfig** in a terminal? Does your device show? If so, what happens when you run **iwlist ath0 scan**? If you're trying to connect to an encrypted network, can you drop the protection for a sec and see if you can connect then?

---

### Post by bobleny on 2009-01-27
Yay! Someone posted in my thread! Yay!

When I run ifconfig, I only get eth0, and lo.
Does this mean the drivers aren't installed, or does this mean ubuntu doesn't recognize the card???

I'm still stuck :'(


It is Hardware Access Layer, by the way....

---

### Post by bobleny on 2009-02-01
You know, It really sucks having a wired laptop that has built in wireless capabilities.....

---

