---
title: "Cannot connect to secured networks on Asus EEE with netbook remix"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by dtech on 2009-04-09
Hi all,

I finally decided to give ubuntu netbook a swing on my Asus EEE 1000H. After swearing a few times because it was so complicated to convert my (by default) 4 primary partitions (windows, data, recovery and some 40MB I don't know the purpose for) to 3 primary & 2 extended I finally managed to get UNR 9.04 installed.

My enthusiasm was majorly tempered when I found out I couldn't connect to either one of my two wireless networks. I just kept getting the "Authentication required by wireless network".

I could however connect to a unsecured network in the neighbourhood, but it has a crappy speed (probably because its like 50 meters away :P)

But the question remains, how can I fix this so I can connect?

The networks are like this:

Network (home, dd-wrt wrt54g & another netgear router):
SSID: Something
Encryption: WPA/WPA2 Mixed TKIP/AES 

Network at university:
SSID: [eduroam](http://www.eduroam.org/)
Network verification: open
Encoding: WEP
Verification type: EAP/TTLS
Verification protocol: PAP

or

Network verification: open
Encoding: WEP
Verification type: EAP-PEAP
Verification protocol: EAP-MSCHAPv2

I've tried all of them, but none work :(

---

### Post by dtech on 2009-04-10
As an update and kick:

on another location, also a network with WPA2 mixed (that means that you can connect with any combination of WPA, WPA2, TKIP and AES) I got the same error, I did this:

1. Click the network name in Networkapplet
2. Enter the key
3. Cancelled when "Invalid authentication" message came up
4. Right clicked network applet -> Edit connections
5. Selected Wireless -> "Auto {networkname}" and clicked edit
6. manually entered the key again in wireless security

When I clicked connect, I still got the invalid key message.

However, to my suprise, **next time I rebooted it automatically connected perfectly fine, and keeps on doing so after every reboot!**
It also lost the connection a few times (like once every two hours) but proceeded to reconnect, get an IP and work perfectly fine...

---

### Post by dtech on 2009-04-16
I don't seem to have the problem atm anymore. Sometime it just "dissapeared".

It may be coincedence, but this was about the same time that I [fixed this of problem of mine](http://ubuntuforums.org/showthread.php?t=1121527), by removing the gnome config files.

This may also work for you. [b]Note that this will delete all you personal settings and you will need to configure almost everything again[/url]

Try this in the terminal (this will reboot your computer):
```

cd ~
mv .gconf .gconf_backup
mv .gconfd .gconfd_backup
sudo reboot

```

If it doesn't work, you can restore your settings with these commands:
```

cd ~
rm -rf .gconf
rm -rf .gconfd
mv .gconf_backup .gconf
mv .gconfd_backup .gconfd

```

---

