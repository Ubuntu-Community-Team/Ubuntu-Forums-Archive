---
title: "wvdial assistance"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by dastasha on 2009-04-28
I´ve searched and have not found a solution for this one yet.
After upgrading from Kubuntu 8.10 to 9.04 my network manager broke. Kubuntu 8.10 originally found my e220 USB HSDPA wireless broadband modem and asked for the ISP´s settings. Once entered, Knetwork worked perfectly for me.
That is, until I ran the upgrade.

Now, Knetwork is gone. The Network Manager widget/plasmoid recognises my device (the e220). I enter the settings for my ISP but I cant figure how to initiate the connection. From my searches, it appears other users are having the same problem, and I have not found a solution that works for myself yet. 

Other users are recommending to install Wicd. Which I would do, but I need a working connection to install it via adept. My USB modem is my only internet connection.
I´ve tried using a working connection on another partition to download a .deb of it, saved to a USB stick but running the .deb produces a message ¨an error has occurred¨, nothing else, no clues there.

Now I´m trying to connect using wvdial to establish a connection, then hopefully run adept to install Wicd.

My wvdial.conf fial is as follows:

```
[Dialer 3g]

Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
username = username
Password = password
Dial Command = ATDT
Baud =460800
Init4 = AT+CGDCONT=1,"IP","vfinternet.au"
```

When I run ¨sudo wvdial¨ from a console I get the error:

Cannot open /dev/modem: No such file or directory

- This is correct. There is no such file or directory named modem in /dev on my machine.

Problem is I dont know what to change/modify in order to establish a connection.

---

### Post by GeorgeVita on 2009-05-04
Hi **dastasha**,
I thing you should use **sudo wvdial 3g** as you have all parameters under the **3g** tag. If you place them under  **Dialler defaults** you can connect with **sudo wvdial**

Please try the above and if you did not succeed to connect, post any error messages to follow up.

Regards,
George

---

