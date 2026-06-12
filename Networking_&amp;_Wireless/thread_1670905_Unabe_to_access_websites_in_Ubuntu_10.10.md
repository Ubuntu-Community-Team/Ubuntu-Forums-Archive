---
title: "Unabe to access websites in Ubuntu 10.10"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by itsme2011 on 2011-01-19
I am unable to access few websites on my Ubuntu 10.10 (64 bit), but I am able to access them from Kubuntu 10.10 (32 bit) Live CD and Windows 7 (64 bit) on same computer using same Modem and same Internet connection.

Here is what happens when I try to access them on Ubuntu 10.10 (64 bit)

**1)**[U][B]On Chrome, Opera, Firefox, Links2 browser 

[/B][/U]Status bar says waiting for "www.website.com ", the page never gets loaded.

2) [B][U]On Elinks Web browser
[/U][/B]
ERROR
UNABLE TO RETRIEVE 
[http://www.website.com/](http://www.website.com/)
RECEIVE TIMEOUT

3) [U][B]On TELNET

[/B][/U]itsme@itsme-System-Product-Name:~$ telnet passportindia.gov.in
Trying 111.93.222.135...
telnet: Unable to connect to remote host: Connection timed out


itsme@itsme-System-Product-Name:~$ telnet passportindia.gov.in 80
Trying 111.93.222.135...
Connected to passportindia.gov.in.
Escape character is '^]'.
GET / http/text1.0

Connection closed by foreign host.
itsme@itsme-System-Product-Name:~$ 

****************************************************************************************************
****************************************************************************************************

_**[http://passportindia.gov.in/](http://passportindia.gov.in/)**_   is one of the website that I am unable to access.


****************************************************************************************************
****************************************************************************************************

**_Things that I have tried, but failed_**
1) Installed Flash.   (Although most of the Websites, that I am trying to access, do not use Flash)
2) Installed Windows XP (32 bit) through Virtual-Box inside Ubuntu 10.10 (64 bit) and accessed through Internet Explorer, still same problem occurs. (Installed Flash inside Windows too)
3) Tried Ubuntu 10.10 (both 32 bit and 64 bit) in LIVE CD mode. still same problem occurs.

**_Only way for me to access these websites_**

1) Kubuntu 10.10 (32 bit) Live CD 
2) Kubuntu 10.10 (32 bit) installed on my computer
3) Windows 7 (64 bit) through dual boot.

I am not using any Proxies or VPN on these Operating Systems, but still able to access those websites.

---

