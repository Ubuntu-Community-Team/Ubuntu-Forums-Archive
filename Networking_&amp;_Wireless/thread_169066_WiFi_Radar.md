---
title: "WiFi Radar?"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by Pyro MX on 2006-05-01
I made Ubuntu 51.0 work with WPA encryption, but it was really a pain... I don't know if there will be a new network manager supprting WPA in 6.06, but anyway... I found this recently:

[WiFi Radar]("http://wifi-radar.systemimager.org/")

It is a graphical user interface to manage wireless networks and it seems to work with WPA. I haven't tryed it, but I would like to know if anybody did and if it worked fine. Because I don't want to mess too often with wpasupplicant. Just wondered if this was a good alternative.

---

### Post by encompass on 2006-05-05
Yes, it works great for me... I have three different Networks I use and I jsut run the program and switch to the new network.  But non of my networks are encripted.
to install it...
> sudo apt-get install wifi-radar

---

### Post by encompass on 2006-05-12
Well, do you have any results?` Is it working?  Do yo like it and is it working for you?:???:

---

### Post by Pyro MX on 2006-05-13
Yes I tyed it, it appeared to be working a bit but it messed up with wpasupplicant. I must re-install my computer soon so I will un-install wpasupplicant (but let my madwifi dirvers) and try WiFi radar more in depth. But it appears to have the same problem that the network manager has with automatic DHCP: it doesn't work. But I'll write up some news about it soon.

---

### Post by encompass on 2006-05-14
a quick note...
Some drivers have conficts when they are trying to get dhcp while the eth0 is connected.  I had that with my rtl8180 card and the open source driver.
Try not having the internet on at all when you boot rather than cabled on when boot and see if that helps.  If you have cabled connection on boot.  Hope it helps.  I have gone as far as I know.

---

### Post by Pyro MX on 2006-05-14
eth0 is never connected (well I believe it is so). The device is not activated and the default bridge is ath0.

What I do is that I put the whole thing in Static IP, I put an IP adress out of the DHCP's IP range (I think it's that...) and I manually add the DNS. Not the best way to work, but it does. Tomorrow I'll remove wpasupplicant and try WiFi radar to see if it works well.

---

### Post by Pyro MX on 2006-05-15
Well, it didn't work. I tryed Wifi Radar without wpasupplicant, and I haven't been able to get on the internet. It says I am connected, but the network doesn't work. Sad... Oh well, I'm ire-installing the whole computer soon so it doesn't matter lol!

---

