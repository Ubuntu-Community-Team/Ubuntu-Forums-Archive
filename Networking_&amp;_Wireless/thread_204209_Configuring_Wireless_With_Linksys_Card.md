---
title: "Configuring Wireless With Linksys Card"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by obrient on 2006-06-26
I have a wireless card for my Dell Latitude. I am really stumped of where to go with the wireless on my laptop. The card is a WPC54G ver. 4. I have Ndiswrapper installed and it seems to be configured correctly. Here is what I have when I put in ndiswrapper -l.
```
Installed ndis drivers:
wlipnds         driver present, hardware present

```

I also have wifi radar installed and have things there set up for the card. When I do iwconfig I get the following 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys-ob"  Nickname:"linksys-ob"
          Mode:Auto  Frequency:2.437 GHz  Access Point: 00:12:17:E1:0D:E8
          Bit Rate=54 Mb/s
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-12 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Also I have this in my network interfaces file

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp



iface wlan0 inet dhcp
wireless-essid linksys-ob
wireless-key 2627F68597





auto eth0

auto wlan0

```

The last thing from my dmesg output is this

```
[17179605.604000] ndiswrapper (set_essid:61): setting essid failed (00010003)
```

Anyone have any thoughts or ideas? It would be great to have this up and running so I can detach the 40 foot cable in my apartment :)

Thanks,
Tadge

---

### Post by FurryNemesis on 2006-06-26
Looks like we have a similar problem.

Can you ping the router?

---

### Post by obrient on 2006-06-26
No I can't get anywhere. I had it work a bit when I logged in a second time using swith users, but that was before any reboots. I have network manager installed too and it never sees the wireless network.

Tadge

---

### Post by nzruss on 2006-06-26
Does this help? 

[http://www.ubuntuforums.org/showthread.php?t=190967](http://www.ubuntuforums.org/showthread.php?t=190967)

Looks like you got your card recognized, so you should be able to just install network manager.... ah. just read the second bit,... network manager installed... 

mmm i'll keep looking.

---

### Post by obrient on 2006-06-28
Alright I can't believe that wireless is this difficult on this. Now I have network manager recognizing the wireless network, but I deactivated both connections so that when I rebooted I wasn't connected and I could see either choice. Now if I go to read the file "interfaces" I get this

> 
# This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5).  # The loopback network interface auto lo iface lo inet loopback

Now I get to attempt to connect to the wireless and have to enter a key, which is okay, but nothing further. Any thoughts or ideas. 

One Frustrated Mother
-Tadge

---

