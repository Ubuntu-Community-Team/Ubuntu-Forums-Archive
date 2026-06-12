---
title: "Wifi refuses to connect"
date: 2006-02-07
forum: Networking &amp; Wireless
---

### Post by shade11 on 2006-02-07
I have been having troubles with my wifi connection. every time I login I will either not connect to my network or DHCP fails. I know it is not initNG becuase I did a normal boot and it still failed.

I tried using Wifiradar but it didnt work. The default network manager doesn't work either. And gtkwifi refuses to work.

I managed to write a shell script in /usr/local/bin that works but it only works for one Wifi connetion.

```
#/bin/bash
ifdown eth1
iwconfig eth1 essid WheaW
iwconfig eth1 key <censored>
ifup eth1
```

If someone can please tell me what to do.

---

### Post by Mikecore on 2006-02-07
Really shouldn't post in two location

---

### Post by Leigh on 2006-02-07
Have a look at [this wireless troubleshooting guide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide") in the wiki. It may give you a heads up as to what's wrong with your set up.

---

