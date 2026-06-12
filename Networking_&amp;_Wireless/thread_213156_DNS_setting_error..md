---
title: "DNS setting error."
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by Kisiao on 2006-07-10
I just install dapper drake 6.06 into my laptop last night, and since i'm new to world of linux(ubuntu too)... i can't seem to get DNS properties to work. Everytime i added the setting and press ok, it indicates in progress for a while then closed. I reopen the screen, it restored to my gateway ip address "192.168.0.1". I can ping google's ip address for no problem so i guess it's DNS setting error. While using WinXP, everything's fine. It's there anything i've miss out? Thanks in advance!

---

### Post by Sendervictorius on 2006-07-11
Not sure: I would guess you have a DHCP connection, and every time you connect the DHCP resets your settings? Do you have a router that you are connecting through?

Anyway, have a look at /etc/resolv.conf. You can always edit this file and add the dns server in there manually. As soon as the file is saved, it should work. BTW: Can you ping the nameserver?

My /etc/resolv.conf file looks like this:

nameserver 203.96.152.4
nameserver 192.168.0.1

---

