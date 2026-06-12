---
title: "Internet connection"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by bob w on 2009-06-13
I am a dyed in the wool Windows User (from day 1) and brand new to unbutu and am trying to create an internet connection. It indicates I am offline and I need to know what to enter and where. I tried entering the MAC address and after that the "Apply" button was still grayed out. I have what I believe is all the info:

IP Address
Subnet Mask
DHCP address
DNS server
MAC Address

Any assistance you could provide would be appreciated.

Thanks,

bob

---

### Post by doas777 on 2009-06-13
well first a few questions. 

are you connected to a router or directly to the cable modem and is your system dualboot with windows?

are you connecting via wired or wireless?

if you open a terminal (Applications -> Accessories -> Terminal) and paste in:
```
ifconfig 
```what is the output? please paste it into a reply.

---

### Post by Iowan on 2009-06-14
Did you need to manually set up the connection in Windows - or did it automatically get an address (DHCP)?  Ubuntu *should* default to DHCP address... but sometimes issues get in the way. > **bob w said:**
> I am a dyed in the wool Windows User (from day 1)This, too, can be forgiven...;)

---

### Post by doas777 on 2009-06-14
I think the problem may be hotswapping the connection to the cablemodem without rebooting it. most cable modems need a reboot, when the client mac changes. can't tell without a response from op though.

---

