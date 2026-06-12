---
title: "Can Connect To Network But No Internet!"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by playing_with_matches on 2009-09-09
Hello,

I have been trying to install a wireless card I got:

D-Link DWL 520 PCI (uses Atheros chipset).

And using the MadWiFi driver, Network Manager says I'm connected to the network, but I can't browse the internet or even connect to my gateway router.  I have no idea where to even begin troubleshooting.

My router is currently set to broadcast SSID (since it wasn't letting me connect to hidden) and used WPA encryption.

---

### Post by aromo on 2009-09-09
perhaps you are connecting to the neighbour's wireless network?  Can you ping or tracert your router?

---

### Post by playing_with_matches on 2009-09-09
Hello,

No, it's definitely my network (well... at least according to Network Manager).

I was not able to ping my router.

---

### Post by Iowan on 2009-09-09
What IP address does it have (**ifconfig -a**)?

---

### Post by playing_with_matches on 2009-09-09
Hmm... Thanks for the ifconfig thing.  I did notice something weird:


 My wireless IP Address is 192.168.2.2 but when I try to ping, it attempts to ping from 192.168.2.177!  The only thing I have in my network manager is the wireless connection (no wired, etc.)

Turns out I setup a static IP address a few years back and forgot about it, so i just deleted everything in my /etc/network/interfaces.

Thanks for the help!

---

### Post by Iowan on 2009-09-10
> **playing_with_matches said:**
> Turns out I setup a static IP address a few years back and forgot about it, so i just deleted everything in my /etc/network/interfaces.Everything - or (hopefully) just the static IP info? 
(You'll still need the "lo" configuration.)

---

### Post by playing_with_matches on 2009-09-11
To be honest, I deleted everything because it was such a wreck (i've just been upgrading since Edgy, new hardware, etc).  

I cleared it all out, out of frustration (it was telling me certain things didn't exist, etc.)  And then network manager just wrote the correct settings in it. Everything works now.

NOTE: People who may be reading this, if you clear it all out, BACK IT UP!  Just because it worked for me doesn't mean it'll work for you.

---

