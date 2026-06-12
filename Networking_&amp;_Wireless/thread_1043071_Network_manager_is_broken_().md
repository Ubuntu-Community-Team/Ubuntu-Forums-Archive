---
title: "Network manager is broken (?)"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by Emanuele_Z on 2009-01-18
Hi all,

after seeing this behaviour [http://ubuntuforums.org/showthread.php?t=1041683](http://ubuntuforums.org/showthread.php?t=1041683)
I've figured out what's wrong.

When I first login to Ubuntu with my profile the Network Manager applet says it's trying to connect to my own wireless (I can see it let left-clicking on the icon, the dot is on my own wireless).
But when I run *iwconfig* from the terminal I see that the network it's trying to connect is another:

eg:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"<another network not encrypted>"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/100  Signal level:-64 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
And it doesn't connect.
Then when I force it to connect to my own wireless:
```

sudo iwconfig wlan0 essid "<my WPA+WPA2 wireless>"

```
I'm able to successfully connect and if I execute *iwconfig*
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"<my WPA+WPA2 wireless>"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1D:68:08:D2:4D   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-40 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
It connects.

Am I the only one experiencing this behaviour?
What is the config file to edit to make Network Manager work?

Thanks in advance,
Cheers,

---

### Post by Emanuele_Z on 2009-01-18
Anyone has any explanation/can point me towards network manager config file?

Cheers,

---

