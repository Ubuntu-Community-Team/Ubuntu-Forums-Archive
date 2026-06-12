---
title: "Wireless networking and DNS problem"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2010-08-14
I have a wireless card and though I can connect to the wireless network through the wireless router, I am having problems bringing up a web page.  I tried to ping the DNS servers, but it does not respond to any pings though an Internet server 8.8.8.8 does allow me to ping it.  When I first set it up, it worked just fine and then a few hours later, it would not work anymore.  The only thing I did was reset up my Ethernet ports.  I had moved the drive from a identical board to a new one and it messed up the Ethernet settings so I went and reset them to eth0 and eth1 instead of what it was.  I don't see any way that could interfere with the wireless settings.

Any one have any ideas?

---

### Post by Iowan on 2010-08-14
Curious... **route -n** probably won't reveal anything useful - since you can ping the internet. **/etc/resolv.conf** *should* contain the address of your nameserver. You might check if the drive-swap messed with the wireless settings. Unless you swapped the same wireless card - an onboard wireless card would probably have a different MAC and might have a different alias.

---

### Post by Z.K. on 2010-08-15
> **Iowan said:**
> Curious... **route -n** probably won't reveal anything useful - since you can ping the internet. **/etc/resolv.conf** *should* contain the address of your nameserver. You might check if the drive-swap messed with the wireless settings. Unless you swapped the same wireless card - an onboard wireless card would probably have a different MAC and might have a different alias.

Actually, I had set up the wireless settings after I had swapped the drive as the other board did not have a wireless card. Yes, I looked in the resolv.conf and it has the correct address of the DNS servers.  I had a colleague of mine use his laptop which has a wireless card and he was able to connect just fine though he is using Windows and not Ubuntu.

---

