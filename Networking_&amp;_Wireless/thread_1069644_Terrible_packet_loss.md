---
title: "Terrible packet loss"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by SeanTater on 2009-02-14
My laptop is regularly getting good signal strength (~70% most of the time) but gets terrible (~25% typical, ~75% occasionally) packet loss.
I thought interference would be a problem, as I am occasionally within range of 10+ access points, but that must not be the case since none of my other computers are affected.

One other oddity is that when I change channels (from 11 to 10) I get better signal strength from my access point (from 70% to 90%+), but no packets get through.

I'm using Ubuntu Hardy and the b43 firmware

Here are some relevant commands:
```
"lspci":
01:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

"ping":
--- google.com ping statistics ---
54285 packets transmitted, 40705 received, 25% packet loss, time 54334950ms
rtt min/avg/max/mdev = 18.709/24.045/1229.709/25.293 ms, pipe 2

"iwconfig wlan0":
wlan0     IEEE 802.11g  ESSID:"~"
          Mode:Managed  Frequency:2.462 GHz  Access Point: ~
          Bit Rate=2 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=73/100  Signal level=-49 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Ayuthia on 2009-02-14
Have you tried using the bcm43xx module?  If I recall correctly, some people had better luck with the depreciated module in Hardy for the 4306 rev02 cards.

---

### Post by SeanTater on 2009-02-15
I'm afraid I don't know how to switch to the bcm43xx module..
I added bcm43xx to /etc/modules,
removed "blacklist bcm43xx" from /etc/modprobe.d/blacklist
added blacklists for b43, b43legacy and ssb.
Unfortunately all that did was remove my wireless device. Nothing showed up in it's place.. Is there more I need to do?

---

### Post by superprash2003 on 2009-02-15
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by puppywhacker on 2009-02-15
Hi,

I have 15+ accesspoints in range, so I mapped all channels and I switched to a channel which has the least traffic, most are on chan 1 and 6 so I chose 13 (allowed in Europe) wifi in Europe spans 5 channels, since the channels are overlapping so actually I'm using 11,12,13,14&15

In the US you get 7 channels, but channel 11 is the max, this means more overlapping channels but in a smaller range. I used airodump-ng from the aircrack-ng package to sniff out my neighbors. I found that the higher the channel, the less competition.

I configured my Broadcom 4306 (on debian) years ago, I remember it was painfull and dropping connections, until I upgraded the driver and set the powertx to 15 (the maximum)

```
$lsmod | grep 43xx
bcm43xx               437620  0 
firmware_class         11744  1 bcm43xx
ieee80211softmac       31424  1 bcm43xx
ieee80211              34184  2 bcm43xx,ieee80211softmac

$iwconfig
eth2      IEEE 802.11b/g  ESSID:"zyxel"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: 00:02:CF:84:86:1C   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=100/100  Signal level=3/3  Noise level=183/100
          Rx invalid nwid:0  Rx invalid crypt:539844  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$iwconfig eth2 txpower 15
```

---

### Post by puppywhacker on 2009-02-17
I did a debian dist-upgrade so I had to refresh my memory :) I also moved to the b43 drivers. I used the instructions below. So I built a new fwcutter and I used the drivers from the instructions.

[fw-b43 instructions]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new")

```
wlan0_rename  IEEE 802.11  ESSID:"zyxel"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:02:CF:84:86:1C
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:off
          Link Quality=60/100  Signal level=-78 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The interface is now wlan0_rename but this can be renamed in the udev configuration /etc/udev/rules.d/70-persistent-net.rules. like described [here]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/rename-wlan0rename-to-eth0-618042/#post3064165")

---

