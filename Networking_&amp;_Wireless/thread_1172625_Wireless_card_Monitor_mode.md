---
title: "Wireless card: Monitor mode"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by PietreWitobi on 2009-05-28
I'm trying to put my card in monitor mode, but I keep coming up against roadblocks.  How does one leave a card on, but free it from obligations so I can change the mode?  And explanation of my problem:
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Sirizzotti"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:34:81:3A   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=61/100  Signal level:-71 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```
But when I try to change the mode on wlan0:
```

$ iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

```
So of course, I sudo:
```
$ sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
```

Any help?  (9.04 Jaunty Jackalope)

---

### Post by chili555 on 2009-05-28
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Not every card will monitor, so cross your fingers first.

---

### Post by pytheas22 on 2009-05-28
What kind of wireless card do you have and which driver are you using?  If you don't know, post the output of:

```
lshw -C Network
lspci -nn
lsusb
```

Some wireless drivers in Ubuntu don't support monitor mode, but sometimes you can recompile them to fix that.  Other times, if no one has written Linux drivers for your device that support monitor mode, you're out of luck.

---

### Post by PietreWitobi on 2009-05-28
"PRO/Wireless 3945ABG [Golan] Network Connection"

And thanks a lot, chilli, that did what I wanted.  Unfortunately, I have a new problem.  It seems to switch into monitor mode just fine, but when I try to do a capture with weplab, I get:
```
$ sudo weplab -i wlan0 -c file.cap
weplab - Wep Key Cracker Wep Key Cracker (v0.1.5).
Jose Ignacio Sanchez Martin - Topo[LB] <topolb@users.sourceforge.net>

ERROR: datalink type is not DLT_IEEE802.11 or PRISM_HEADER. Maybe you need to configure monitor mode in your wireless card
```
even though when I check my card...
```
$ iwconfig wlan0
wlan0     IEEE 802.11abg  Mode:Monitor  Frequency:2.437 GHz  Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by pytheas22 on 2009-05-28
The iwl3945 driver (which you're using) should support monitor mode without a problem, so I doubt that's the issue.

I think the error message you're receiving may result from the fact that weplab is quite old and may not be compatible with more recent Linux wireless drivers.  Unless there's a specific reason that you need to use weplab, I'd recommend that you try the aircrack-ng suite instead.  It can be easily installed from Ubuntu's repositories, and should work well with your card.  There's plenty of documentation for it online, but if you need help, feel free to ask.

You could also try kismet, another program that you can use for wireless sniffing, but it's not quite as user-friendly as aircrack.

---

### Post by PietreWitobi on 2009-05-29
Nailed it, pytheas.  Thanks.  Using wireshark to sniff and aircrack-ng to crack.

---

