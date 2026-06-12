---
title: "Realtek 8187se wireless driver on Ubuntu 9.04"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by mrmrmrmr on 2009-03-23
Hi,

I have a MSI Wind Netbook with Realtek 8187se wireless card.
I tried Ubuntu 9.04 alpha 6 and I am very happy to see that it recognizes the wireless card without any need to compile drivers.

However, I noticed that the wireless card can only connect to WPA2 networks if hardware operation mode is set to "B" instead of "G" on the access point side.
I tested this with 2 access points (one commercial wifi adsl modem and one home made Linux access point running hostapd)
On both AP I have to set operation mode to "B" for proper connection. My Linux access point's hostapd writes to logs as "EAPOL key timout" if I try with mode set to "G"

I don't know where to post this problem.
Maybe it would be good to post it as bug report to Ubuntu 9.04 , but I don't know how and where we can do that.

Also, I don't know the producer of the driver on Ubuntu 9.04.
Can anyone help me to report these problems and find a solution ?

Thanks.

---

### Post by chili555 on 2009-03-23
You can find the developer of the driver with *modinfo.* So, if, for example, you are using *rtl8187*, open a terminal and do:```
modinfo rtl8187
```You should see this:> filename:       /lib/modules/2.6.27-11-generic/updates/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     290F0D334BA1A0FDE730BF6
etc., etc.If you email the authors, you may find they have a bug tracking system or mailing list that they want you to use.

---

### Post by therabidbadger on 2009-03-25
I too have a MSI wind that I have had trouble with get the wireless card to work. I saw this post and upgraded to 9.04 and my wireless still doesn't work. 

Am I missing something that I need to do extra? like a command or something.

Any help would be nice thanks!

---

### Post by mrmrmrmr on 2009-03-25
did you try with wpa instead of wpa2 ?

---

### Post by shadews on 2009-10-08
I have a MSI Wind U100 with the Realtek 8187SE as well.  I can connect to a wired connection perfectly.  I can only connect to unsecured wireless connections.  If I try to connect to a wep or wpa/wpa2 network it will fail.  For the WPA2 network, it requires PEAP version 0 with MSCHAP for authentication.  On an interesting note, when I connect through the unsecured, Pidgin won't connect to any IM but it comes up right away when I have a wired connection established.
 
Any help is appreciated!
 
Thanks!

---

