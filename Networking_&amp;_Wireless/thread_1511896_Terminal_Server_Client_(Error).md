---
title: "Terminal Server Client (Error)"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by Infinitum7 on 2010-06-17
Alrighty, I have a couple of questions regarding use of the TSC for remote desktop connections. 

I'm connecting from my Ubuntu Desktop (Lucid) and i'm connecting to my Laptop (Windows 7) i'm running PC Tools Firewall Plus on the windows machine. The window's machine has remote assistance allowed. 

At the moment i'm just trying to get the TSC to work on my home network. I filled it out as follows:

Computer: Lappy's IP
Protocol: RDPv5
Username: ZachAdmin
Password: *My password*
Domain: Blank
Client Hostname: Blank

Now the first time I tried to connect, about 20ish seconds passed and "The connection has timed out" appears. So I went into my Firewall and sure enough it was blocking the UDP/TCP packets that my desktop was sending. So I temporarily allowed all UDP/TCP packets. Now when I connect "Connection Refused" immediately pops up. I go into my firewall and it's allowed both inbound and outbound packets from my laptop to my desktop and vis versa. So now i'm really stumped. Any thoughts would be greatly appreciated! :)   


PS: Not sure if this has any bearing on the situation, but i have a share folder working with samba between the two computers.

---

### Post by pricetech on 2010-06-17
Windows 7 has a lot of paranoia built in to it.

On your Remote tab, under Remote Desktop, choose "Allow connections from computers running any version of Remote Desktop".  The third option won't work.  (tested it here)

I've had to specifically open ports even with the firewall turned off on both my Windows 7 computers.  I created a rule that explicitly opens everything since both computers are at this point still in testing.

Gonna be fun when the whole herd migrates.

---

### Post by Infinitum7 on 2010-06-17
Odd, i can't seem to locate the "Allow connections from computers running any version of Remote Desktop" even in the advanced options.

---

### Post by pricetech on 2010-06-18
> **Infinitum7 said:**
> Odd, i can't seem to locate the "Allow connections from computers running any version of Remote Desktop" even in the advanced options.

Which version of Windows 7 are you running ??  I"m on professional here.

---

### Post by Infinitum7 on 2010-06-19
Must be because i'm running home premium

---

### Post by CharlesA on 2010-06-19
Home premium doesn't have Remote Desktop. :)

---

### Post by Infinitum7 on 2010-06-20
Whaaa! Damn, then why the heck do they even put the remote connection thinger in there! That would explain it though.

---

### Post by pricetech on 2010-06-22
Indeed it would.  I wonder if there's any way to use RDP Client with a Remote Assistance request.  I've never tried it, so I don't know.

---

