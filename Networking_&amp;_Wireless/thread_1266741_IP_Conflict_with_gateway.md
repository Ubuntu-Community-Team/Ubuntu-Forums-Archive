---
title: "IP Conflict with gateway"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by omrsafetyo on 2009-09-15
Kinda strange... if I run an ifconfig, I receive my public IP address.

I use Vonage and use the vonage device as my gateway.  It seems I have a IP conflict with the device.  My vonage device is hooked directly to the cable modem.  My Ubuntu box is attached to the gateway via USB; I use the ethernet for my work laptop (Windows).

If I run an "arp -a", I only receive the address of the comcast router for arp entries.  Every once in a while my net goes out, and I'm guessing its due to the IP conflicts. 

Any ideas as to the cause?

---

### Post by falconindy on 2009-09-15
> **omrsafetyo said:**
> Kinda strange... if I run an ifconfig, I receive my public IP address.

I use Vonage and use the vonage device as my gateway.  It seems I have a IP conflict with the device.  My vonage device is hooked directly to the cable modem.  My Ubuntu box is attached to the gateway via USB; I use the ethernet for my work laptop (Windows).

If I run an "arp -a", I only receive the address of the comcast router for arp entries.  Every once in a while my net goes out, and I'm guessing its due to the IP conflicts. 

Any ideas as to the cause?
Nothing here sounds out of the ordinary. `arp -a` lists local devices that resolve addresses (aka DNS servers aka your gateway) so it makes sense that you're only seeing a single device. Because you're not actually connecting via ethernet, normal protocols sort of go out the window. The USB connection to the gateway becomes your NIC. You share a single IP address because only 1 network device exists between the two. As for why your internet intermittently goes out... I don't think this is related. When an IP conflict occurs, normally one or both devices are completely blocked -- there's no "flicker".

If you connect via ethernet, I'll bet you'll get a different (local) address on your ubuntu box.

---

