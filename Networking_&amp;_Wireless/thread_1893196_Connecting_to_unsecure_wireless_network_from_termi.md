---
title: "Connecting to unsecure wireless network from terminal"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by Afiorentino on 2011-12-09
I installed a new video card, but while installing the driver for it, the installation got interrupted. Since then my GUI has stopped working and I can't even connect to my wireless network so that I can re-install the new video driver.

I've been playing around with the iwconfig commands in terminal, but still haven't  been able to figure out how to connect. 
```

iwconfig wlan0
wlan0    IEEE802.bg  ESSID:"dlink"
             Mode:Managed   Frequency: 2.47 GHz  Acess Point: Not-Associated
             Tx-Power=20dBm
             Retry   long limit:7    RTS thr:0ff   Fragment  thr:off
             Power Management:off
```


Any ideas/suggestions? I would prefer not to do a clean install.

---

### Post by jonobr on 2011-12-09
hello

Assuming alls ok with your driver

try bringing up the interface

```
sudo ifconfig wlan0 up
```

check ifconfig that its there..... if it has an IP address you may be ok at this point,.

scan for the ap


```
sudo iwlist wlan0 scan | grep ESSID 
```

(Drop | grep ESSID to see more info)

This should show you your AP (eg mynetwork)

connect
```
sudo iwconfig wlan0 essid "mynetwork"
```

if you need to force an IP address acquisition 

```
sudo dhclient wlan0
```

Post an errors you may see along the way

---

### Post by Afiorentino on 2011-12-09
That did it! I'm not sure what I did differently, but it's working.

Thank you very much

---

### Post by jonobr on 2011-12-09
Sweet

Recommend you change title to have Solved at the start for others

---

