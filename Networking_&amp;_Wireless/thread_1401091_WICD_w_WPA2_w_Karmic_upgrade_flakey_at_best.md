---
title: "WICD w/ WPA2 w/ Karmic upgrade flakey at best"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by robertbub on 2010-02-07
After my Karmic upgrade, I was happy that my display and sound continued to work (unlike previous upgrades).  But!  My wireless doesn't work consistently.

I'm using WICD with WPA2 using a Preshared Key (PSK).  Wired connections always work consistently, but my wireless connections won't come up in sometimes (there's no pattern I can discern).

I am using the PPA WICD from [http://apt.wicd.net](http://apt.wicd.net) since I read somewhere that that may fix the problem, but it doesn't.

I turned on debugging in wicd and it looks like it should work:>  2010/02/07 14:13:19 :: WPA_CLI RESULT IS ASSOCIATING
 2010/02/07 14:13:20 :: iwconfig wlan0
 2010/02/07 14:13:20 :: WPA_CLI RESULT IS COMPLETED
 2010/02/07 14:13:20 :: Setting static IP : 192.168.2.4
 2010/02/07 14:13:20 :: ifconfig wlan0 192.168.2.4 netmask 255.255.255.0
 2010/02/07 14:13:20 :: Setting default gateway : 192.168.2.1
 2010/02/07 14:13:20 :: route add default gw 192.168.2.1 dev wlan0
 2010/02/07 14:13:20 :: Setting DNS : 208.201.224.33
 2010/02/07 14:13:20 :: Setting DNS : 208.201.224.11
 2010/02/07 14:13:20 :: Setting DNS : 208.201.224.33
 2010/02/07 14:13:20 :: Verifying AP association
 2010/02/07 14:13:20 :: ping -q -w 3 -c 1 192.168.2.1
 2010/02/07 14:13:20 :: Connection Failed: Failed to ping the access point!
 2010/02/07 14:13:20 :: ifconfig wlan0 0.0.0.0
 2010/02/07 14:13:20 :: /sbin/ip route flush dev wlan0
 2010/02/07 14:13:20 :: wpa_cli -i wlan0 terminate
 2010/02/07 14:13:20 :: exiting connection thread
 2010/02/07 14:13:20 :: Sending connection attempt result association_failed

Anyone else have this problem?

---

### Post by robertbub on 2010-02-07
I discovered 2 things since posting:[LIST=1][*]wicd doesn't wait long enough before trying to verify the Access Point connection
[*]there seems to be an implicit dependency upon /etc/network/interfaces (despite there being no claims as such)[/LIST]To solve #1, I[LIST][*]renamed /usr/shared/wicd/wicd/networking.pyo & /usr/shared/wicd/wicd/networking.pyc to other names
[*]edited /usr/share/wicd/wicd/networking.py and commented out```
        #self.verify_association(wiface)
```[/LIST]For #2, I restored my entries in /etc/network/interfaces:```
auto wlan0
iface wlan0 inet static
    address 192.168.2.4
    netmask 255.255.255.0
    gateway 192.168.2.1
    wpa-driver wext
    wpa-ssid dlink
    wpa-ap-scan 2
    wpa-proto RSN
    wpa-pairwise CCMP
    wpa-group CCMP
    wpa-key-mgmt WPA-PSK
    wpa-psk XXXX
```Without this stanza, no **route** table is set up.  Oddly.

Also, despite the above changes, initially connecting is usually hit-or-miss.  And, when the next upgrade happens or wicd gets updated, the above changes will get clobbered and I'll have to reapply them.

---

### Post by robertbub on 2010-02-20
My laptop died and got a new laptop.  So, never got to follow up with this problem.

I'm running NetworkManager and it works fine.

---

