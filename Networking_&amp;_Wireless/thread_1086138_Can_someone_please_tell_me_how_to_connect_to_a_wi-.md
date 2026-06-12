---
title: "Can someone please tell me how to connect to a wi-fi network using the command line?"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by andrewwg94 on 2009-03-03
I want to connect to wi-fi without network manager or wicd.

Please tell me how. Here's my information, if there's anything missing, please tell me:

Network Name [SSID]: 'Home Network'
WPA hex key: '7A5ACBB7E9'
adapter: wlan0
ubuntu 8.10

my goal is to connect automatically on start up. i already tried so much with network manager and wicd with no luck. i tried looking at that one how-to, with no luck either. i'm not sure what i'm doing wrong. i'm pretty new at this networking stuff so please help me out. this is on the ps3 by the way so it's ppc64 not i386.

thanks so much,
andrew

---

### Post by N04h on 2009-03-04
So in your case:

```
sudo iwconfig wlan0 essid "Home Network"
sudo iwconfig wlan0 key 7A5ACBB7E9
```

Next, Verify you're connected.  If you are you'll have to do a DHCP request from the command line.

---

