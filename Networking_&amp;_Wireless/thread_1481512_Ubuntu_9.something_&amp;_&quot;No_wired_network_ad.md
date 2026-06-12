---
title: "Ubuntu 9.something &amp; &quot;No wired network address&quot; (sudden)"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by Hardtoid on 2010-05-12
Hello. I am using ubuntu 9.something for about a month. I managed to get everything working as close to my needs as I could (i installed U.Studio packages). A long painfull procedure which made Windows Xp seem like a golden product. I am really willing to keep using ubuntu, but, what is going on with stability? Yesterday I had a nice working wired network with my router. Today ubuntu acts like there is no ethernet! I googled all day and found no good solution yet. And here I am, using my windows XP over the same system. The router and the ethernet (onboard) are obviously fine working. I wish someone could help me, giving any hint on what to do. Thank you!
Some info I gathered are:

[SIZE=3]**ifconfig:**[/SIZE]
eth0      Link encap:Ethernet  HWaddr 00:22:15:75:ff:4a  
          inet6 addr: fe80::222:15ff:fe75:ff4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8460 (8.4 KB)
          Interrupt:27
[SIZE=3]**lspci -nn:**[/SIZE] (this is confirmed @ the motherboard manual)
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller [1969:1026] (rev b0)
[SIZE=3]**iwconfig:**[/SIZE]
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Hardtoid on 2010-05-13
Anyone please?

---

### Post by Iowan on 2010-05-13
I had [this]("http://ubuntuforums.org/showthread.php?t=1156441") problem on my Jaunty (9.04) laptop.

---

### Post by sir_nasty on 2010-05-13
what's odd for me is that your ifconfig doesn't even show it attempting and ipv4 address.... I'd try something simple first like

sudo ifconfig eth0 down
sudo ifconfig eth0 up

then see if it can get an address... if not... right click on the notification icon (upper right hand corner) edit connections, Auto eth0 edit, and make sure it's available for all users and set to automatically connect, then make sure ipv4 is setup for DHCP.

---

### Post by Hardtoid on 2010-05-14
> **sir_nasty said:**
> what's odd for me is that your ifconfig doesn't even show it attempting and ipv4 address.... I'd try something simple first like

sudo ifconfig eth0 down
sudo ifconfig eth0 up

then see if it can get an address... if not... right click on the notification icon (upper right hand corner) edit connections, Auto eth0 edit, and make sure it's available for all users and set to automatically connect, then make sure ipv4 is setup for DHCP.

Thank you for your replies. I'll try these 'ifconfigs' and see what I get. The eth0 settings are just like those you mention. I have to add that yesterday I installed a fresh 10.04 ubuntu, and I get the same problems with my wired connection.
I repeat that everything worked fine for a month and I have no automatic updates. So, nothing could change and mess with any drivers without knowing. Or could I be wrong? Could it be a virus or something?

---

### Post by Hardtoid on 2010-05-15
Well. Absolutely nothing yet. Should I report a bug? Ubuntu is of no use without the possibility of a network.

---

### Post by sir_nasty on 2010-05-17
If you edit the connections via network manager and specify an IP address instead of dhcp will it work then? (PS Don't forget your dns....)

---

