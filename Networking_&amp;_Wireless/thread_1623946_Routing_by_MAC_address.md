---
title: "Routing by MAC address?"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by xefialtis on 2010-11-17
Greetings...
I have an issue that y'all might be able to help with...

I recently got a new phone... and while not ideal (Windows Mobile 6.5) it is what I have...
I am planning on putting Linux on it (Android) but I won't/can't do that just yet.
So what I need to know is the following...

I have a secure network. I lock down the wireless to MAC addresses, and I have a Linux server that handles routing, DHCP, filtering, proxy, and everything else.
I can get connected to the wireless, but I cannot access the internet, due to the phone's inability to install and run IDENT Server. 
I don't know if Android would solve this, but as I said, I don't have that installed yet.
I have dual NICs in my server to handle input/output... one is on the inside of the network, the other is on the outside...
I have the routing table set up to keep all 80/8080 traffic through the proxy and dansguardian (hence, the need for IDENT)...

Is there a way to rout based on MAC address to bypass the proxy and filter? Or do I have to rout it by IP address, in which case, I would have to set DHCP to hand out a static address based on MAC address.

Which is "doable", which is "better", and which is "easier"?

If I could get an example of this from someone, I can mod it to fit my needs... 

Thanks in Advance.

---

