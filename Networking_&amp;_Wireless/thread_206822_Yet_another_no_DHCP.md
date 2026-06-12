---
title: "Yet another no DHCP"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by MerZo on 2006-06-30
Hello there!

I have got a problem with my wireless network. The thing is that it worked great  the first time installed ubuntu, I went into the networking option in the meny, entered them accordingly. Essid, key, and then it magically worked. Happily i surfted the net. 

After some experimenting i reinstalled the system and it still worked the same way. After breaking everything again and reinstallning for a second time it didnt work. The iwconfig says that it is connected, the command iwlist eth1 scanning shows the router. 

But when I try to get an IP with the command dhclient eth1 it just results in a timeout because it doesn´t find the dhcp server.

Now the strange thing with this is that it is the same both at my house and at my girlfriend. And I can´t just get it.

The computer is a Thinkpad R40 with an internal Cisco card. That is found when i type lspci.

Can someone guide me to get it working? Even tried archlinux, same problem there. But windows do work. Freaks me out. :/

Can I read a log or something to get a answer?

---

### Post by madbuda on 2006-07-15
I have the same problem....

I just installed Ubuntu 6.0.6 on my t41 with internal Atheros wifi.

Using window$ I can connect to wirless and get an ip via dhcp.
Ubuntu I can get connected to the wifi but not the actuall lan, even tried static IP.

Hopefully someone has som sugestions :)

---

### Post by madbuda on 2006-07-15
Well.. I have got mine working...

It seems there are issues with WEP. Once disabled everything works fine.

Some people suggested you set your AP for open WEP.. I didn't try this since my Wifi is onb a seperate network that my lan..

Hope this helps

---

### Post by MerZo on 2006-07-24
Hmm, anyone with more information about this? Have my wireless set to WEP 64-bit HEX. Doesnt work with ascii either and really want WEP. 

Windows XP works perfect.

---

### Post by tymek666 on 2006-07-25
under Kubuntu i had to:

sudo dhclient wlan0 (or your inteface)

and then dhcp worked fine.

---

### Post by markusfarkus on 2007-03-21
I am using an IBM T41 at work.  Just installed Ubuntu 6.10.  I didn't get a chance to try the wireless card because we use a VPN server.  But I couldn't connect to the internet.  I could ping internal servers, and I was getting a proper IP address via DHCP, but could not get to the internet.  

I tried sudo dhclient eth0 and it is working wonderfully.  I just wish I knew what the real problem was!  

Thanks guys,

---

