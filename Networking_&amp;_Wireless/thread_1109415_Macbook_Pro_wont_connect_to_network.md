---
title: "Macbook Pro wont connect to network"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by garretth on 2009-03-28
Hi,

I've just started dual-booting Kubuntu with my Macbook Pro and the installation went fine. The only problem I've found yet is that I can't connect to the network to get the internet via wifi.

I click on the globe icon down the bottom and click to make a new wlan connection. It finds the network (an Apple Airport Extreme) so I select it and press next. Then it asks for a "shared key", which I assume is just the password for the WPA network? So I enter the password in the shared key area and then click "save and connect".

Once this happens, the network appears in the globe menu but its status bar just stays at about 60% and it never connects. Any help would be greatly appreciated!

Thanks

---

### Post by fukr on 2009-05-16
garretth,

My Jaunty MacBook Pro had similar wireless connectivity issues out of the box. I was eventually able to connect -- after retrying a number of times and waiting a VERY long time for the connection to be established.

Once you get connected (or if you can get wired up):
```
sudo apt-get update && sudo apt-get install linux-backports-modules-jaunty wicd
```

Good luck.

---

