---
title: "Switched to Static IP - Now internet is slow or times out"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by bruceleeroy on 2009-03-25
Hey guys,

I consistently was having NAT problems with my torrents and playing games online with my PS3. I gave my computer a Static IP and it resolved both of those issues beautifully. My torrents download blazing fast and I never get drop outs from multiplayer. However, It seems to have affected my internet connection. My connection is generally a lot slower than it used to be but worse than that it consistantly times out when loading a webpage and can even disconnect my internet.

These are some of the settings I am dealing with.
My router is a [COLOR="Red"]**LINKSYS Router Wireless G WRT54GS.**[/COLOR]

----------ROUTER----------
My router settings are as follows:
**Internet Connection Type:** Automatic Configuration - DHCP
**DHCP Server:** Enable
**Starting IP: **192.168.1.100

**Wireless Settings:** Disabled
**Firewall:** Filter Multicast

**Port Range Forwarding:** Utorrent: 192.168.1.150
**DMZ:** Enabled: 192.168.1.50

-------COMPUTER----------
**Computers IP Address:** 192.168.1.150
**Subnet Mask:** 255.255.255.0
**Gateway:**  

And I think thats it. I would really appreciate any help you guys could offer.
Thanks,
Chris

---

### Post by bruceleeroy on 2009-03-25
I just realized this might be better in a different forum or thread have you guys seen any specific websites that might would be a good for me to try.

---

### Post by rhcm123 on 2009-03-25
Set your pc gateway to your router's ip.

EDIT: Also, turn off the DMZ'ing your PC, and only forward the specific ports you want. Your just asking for trouble with that.

---

### Post by bruceleeroy on 2009-03-25
Thanks man.
Ill try that post back.

So for the PS3 I should set it up with a static address like 192.168.1.50 and then forward a port called PS3 with the same IP. How can I determine what the port opening should be?

---

### Post by bruceleeroy on 2009-03-25
Is it normal for me to have the Router Internet Connection Type set up as this:

**Internet Connection Type:** Automatic Configuration - DHCP

---

### Post by rhcm123 on 2009-03-26
> **bruceleeroy said:**
> Is it normal for me to have the Router Internet Connection Type set up as this:

**Internet Connection Type:** Automatic Configuration - DHCP

yes, thats for wan setup.

---

### Post by superprash2003 on 2009-03-26
what is your internet connection speed?? its common to have low speeds if your downloads take all your bandwidth

---

