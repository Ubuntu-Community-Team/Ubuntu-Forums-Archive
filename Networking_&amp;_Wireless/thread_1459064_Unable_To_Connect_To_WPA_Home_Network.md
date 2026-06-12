---
title: "Unable To Connect To WPA Home Network"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by HouseShark on 2010-04-20
First off, I should state that I am still using Hardy.  I realize that it is many versions from the current release, but my schedule is full and provides little time to ring out a new distro and considering the nature of my problem I don't see much need.

The problem is that I cannot connect to my WPA home network.  The wireless card is working because I can connect to any WEP network and before upgrading to Hardy I could connect, although not at first.

Have recently installed WICD which has not helped.  WICD tries to connect but reports that it cannot obtain and IP address.  Network Manager did not report anything but did seem to translate the password into an encrypted key (saw posts relating to this before but no obvious fix)  Since switching to WICD I have not had the opportunity to test connection to a WEP network.

I do not wish to change the security of my home network to accommodate the operating system.

If there is a quick fix that does not require a lot of time I would appreciate any help.

---

### Post by marcwhitaker on 2010-04-20
Ditto . . . with 10.04 and 9.10, although it used to work, but a kernel update killed it.

Acer Aspire 1 AOA150.

---

### Post by brothers4ever2 on 2010-04-21
**Cant connect to Secure VPN In Ubuntu?**

I am running Ubuntu Netbook Remix.
My router is the Xtreme N GIGABIT Router Model DIR-655
It was originally set up to be a Wireless VPN for Windows 7
Every time I try to connect to it on my laptop. It asks me for the password
I put in the exact password. and it shows the activity for a while. 
Then it asks me for the password Again.
I have been at this for a month now.
PLEASE PLEASE somone help me.
I have all the VPN packages installed, is there something missing?
let me know.

---

### Post by HouseShark on 2010-06-28
Found out what the problem is.  Apparently the proprietary broadcom drivers do not handle hidden SSID's.

---

