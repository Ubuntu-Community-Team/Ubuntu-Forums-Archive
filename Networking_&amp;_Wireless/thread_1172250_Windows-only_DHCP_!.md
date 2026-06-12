---
title: "Windows-only DHCP ?!"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by yesint on 2009-05-28
Dear All,
I've changed the Internet provider and run into stupid problem - the DHCP server of the new provider only gives ips to Windows machines. My Ubuntu desktop was unable to connect, dual-boot laptop connected happily under Windows, but failed in Ubuntu. There is nothing special - just ordinary DHCP network with no additional configuration required under Windows. 
Finally I managed to connect in Linux by transferring the ip, dns server, gateway etc. from Windows manually, but I'm puzzled why this happened. As far as I understand the network protocols are universal, so why one OS obtains an ip by DHCP, while other does not? 
Any ideas?

---

### Post by dmizer on 2009-05-28
What type of networking equipment did your ISP provide you with (make and model number please)? What is your IP address in Windows?

---

### Post by superprash2003 on 2009-05-28
have you tried using the dhclient command to request for an ip?

---

### Post by Iowan on 2009-05-28
Probably doesn't matter, but which version of Ubuntu?

---

### Post by iponeverything on 2009-05-28
I have found that pump will sometimes work in cases where dhclient will not.

---

### Post by yesint on 2009-06-03
> **dmizer said:**
> What type of networking equipment did your ISP provide you with (make and model number please)?

I have no idea what does it mean, sorry...

---

### Post by yesint on 2009-06-03
> **iowan said:**
> probably doesn't matter, but which version of ubuntu?

9.04

---

### Post by lukjad on 2009-06-03
> **yesint said:**
> I have no idea what does it mean, sorry...
Did they give you a modem/router?

---

### Post by yesint on 2009-06-03
> **lukjad007 said:**
> Did they give you a modem/router?

No. There is a long standard network cable going from the basement of our large apartment building. I have no access to the switch or the router or whatever they installed there.
However, I know for sure that my network card is Ok. It was working in Ubuntu with other providers.

---

### Post by yesint on 2009-06-03
> **iponeverything said:**
> I have found that pump will sometimes work in cases where dhclient will not.

Unfortunately I'm completely illiterate in terms of these low-level networking utilities...

---

### Post by dmizer on 2009-06-03
Okay, if you cannot access the networking equipment, then please provide the IP address that the Windows computer gets when you connect.

Do you have to use any special software (specifically software which requires a username/password) to get connected?

---

### Post by Iowan on 2009-06-03
Might not fix your problem, but check [here]("http://ubuntuforums.org/showthread.php?t=1156441") or [here]("http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html").

---

### Post by yesint on 2009-06-06
> **dmizer said:**
> Okay, if you cannot access the networking equipment, then please provide the IP address that the Windows computer gets when you connect.

Do you have to use any special software (specifically software which requires a username/password) to get connected?

The IP is 10.35.63.202. No additional software is required. In Windows it just works (everything set to "automatic" in network settings, no additional software).

---

