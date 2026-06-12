---
title: "trouble connecting via ethernet cards"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by rogdawg on 2010-10-10
I have just installed Ubuntu Studio onto a machine that has two ethernet cards on board. I am trying to connect the machine to the internet but, I can't seem to do it. This is not my area of expertise so, I would like some advice on what procedures to follow (I am not getting a lot from the documentation). 

I have connected my Macbook, using the same ethernet cable that I was attempting to use with the new Ubuntu install, so I could see the settings and try to emulate them. 

My Macbook is connecting using DHCP and I can see the address of my DNS server (my router) and the Search Domains address. So, I opened up Network Tools on the Ubuntu machine, and for BOTH of the ethernet cards (eth0 and eth1), I have selected Configure and, on the DNS tab, I added a DNS Server and a Search Domain, with information matching what I see on my Macbook. My Macbook is connecting using IPv4.

One thing that might be a problem is that, in Network Tools, Devices tab, the IP Address is 0.0.0.0 and the Netmask / Prefix is 0.0.0.0. On the MacBook, those fields have values. I think the IP Address is probably assigned by the router but, I am wondering about the NetMask. Can I edit that? Should I? Where would I do that?

Any more suggestions would really be appreciated. 

Thanks in advance for any help you can provide.

---

### Post by rogdawg on 2010-10-10
I solved it by re-installing Ubuntu Studio, this time with the ethernet cable plugged in. I let the installation autodetect the network, and it all worked smoothly. 

Better than spending hours trying to figure this stuff out. 

On to other adventured...

---

### Post by lance21broke on 2010-10-10
The problem i think is you dont have permission to access folders. To solve this try to go to your properties on the security tab right click and allow  for all users.
Repeat it in all folders, this should fix your problem

---

