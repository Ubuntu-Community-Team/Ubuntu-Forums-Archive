---
title: "Ethernet setup"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by iAlta on 2006-06-04
How can i setup a (non-wireless) connection to the internet?

---

### Post by RRS on 2006-06-04
Before any of us can help you we'll need a litle more information.

What type of connection; dial-up, DSL, Cable?

Equipment; (make and model if available) modem, router, ethernet card, etc. I realise you may not have or need all of these devices but any you are using would be helpfull.

Post back with this info and what methods you've tried so far and I'm sure someone can help.

---

### Post by iAlta on 2006-06-04
OK, thanks for the reply, here we go.
 I attached a .txt file with lspci -v. I have never attached a file on these forums before, so I don't know if it wil work.

The router is linksys, the card is d-link and the cable is blue.
oh yeah, I've got cable, 2Mbit down and 256Kbit up.

---

### Post by RRS on 2006-06-04
Ok, extra info will help.

Your attachment came thru fine.  In the future though for small files like that it might be easier to copy them into the post and then use the code wrap in the toolbar to seperate from the other text (or not?)

The info from ```
ifconfig
``` would also be helpfull.

Also (sorry for extra ?'s) does your ISP assign a static IP or use DHCP (have dsl with PPPoE myself)

BTW, how are you connected now, another computer or from windows on same machine? And how'd you get the .txt file uploaded?

Edit: Had to go find [this thread]("http://www.ubuntuforums.org/showthread.php?t=87643"), helped me a while ago.

---

### Post by unicycler on 2006-06-05
Does your Linksys router provide DHCP? Can you go into your system settings for network, select your network card, Edit its properties for Static or Dynamic IP Address, Activate the network card and exit Network Settings? This should connect you to your router and get you online.

---

### Post by iAlta on 2006-06-05
I am now on a xp laptop. The previous post was from a Sony PSP, which lacks copy-paste.

I'll try some of your things you two said, but I'm not so goos when it comes to network setings (that's why I haven't been online on Ubuntu for a year).

I'll check back in a while, and see with iconfig and the other info I can get.

The routher is a Linksys [WAG54G]("http://www1.linksys.com/international/product.asp?coid=6&ipid=667")

---

### Post by iAlta on 2006-06-05
That trobleshoot-link went fine until, "Reaching the Internet by number" it said the internet was out of reach...

---

### Post by iAlta on 2006-06-06
iconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0D:88:B3:A9:95
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:feb3:a995/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:438 (438.0 b)  TX bytes:468 (468.0 b)
          Interrupt:193 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)
```

---

### Post by Iowan on 2006-06-06
Dunno if it's causing your problems, but IPv6 doesn't work well for me.

Also, what's in your **/etc/network/interfaces** file?

---

