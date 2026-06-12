---
title: "Wireless only seems to work with open networks"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by bmb0x on 2011-01-22
Tonight I replaced Ubuntu 10.04 with Kubuntu 10.10. While running Ubuntu 10.04 wireless worked fine and I had no problems. 

However, now with Kubuntu 10.10 I seem to be having a bit of a problem with the wireless. It will only connect to a wireless network that is 'open' (no security). It sees the network i want to connect to, but when i go to put in the correct security values it does nothing. Never seems to try to connect again. I've edited both the local Kubuntu wireless settings, as well as change settings on my router (went from WPA to WEP just to see if I could get it to work. It didnt). 

So im wondering if there is any other software I could use to try to manage the local wireless hardware to see if different software will connect? 

Here is my iwlist, not that it helps but at least it proves my hardware sees the wireless i want to connect to. 

wlan0     Scan completed :
          Cell 01 - Address: 00:23:54:EF:51:A0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Free Interweb"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002da799183
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 000D4672656520496E746572776562
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

---

### Post by nerdy_kid on 2011-01-22
yeah I've actually had the inverse problem with the network manager in KDE before.  Are you sure you have the key type right?  Like for WEP networks, there are "password" and "hex key"  types.  if it still won't connect, then you can always install wicd and use that instead of KDE network manager.

```

sudo apt-get install wicd

```

There is a KDE frontend on projects.kde.org, but you have to grab it from git and compile it yourself -- so maybe you would want to stick the the GTK interface.

---

