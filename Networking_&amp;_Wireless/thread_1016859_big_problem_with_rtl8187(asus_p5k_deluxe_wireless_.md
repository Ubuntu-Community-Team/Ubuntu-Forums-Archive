---
title: "big problem with rtl8187(asus p5k deluxe wireless onboard card)"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Argard on 2008-12-20
Hi,

I have been some problems with my wireless card, realtek rtl8187( came with my Asus - P5K deluxe motherboard), It connects, but doesn't receive or send packets on the ubuntu, windows works fine :(

I follow this tutorial, very good by the way.
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

1 - I Removed the old driver
2 - Blacklisted the old driver
3 - Ndiswrapped instaled
4 - I tried with win98 and winxp drivers , win98's driver is the best
5 - I modified my interfaces file to this:
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
#-=-=-=-=-=-Static config[begin]-=-=-=-=-= {disable for tests}
#iface wlan0 inet static
#address 192.168.1.5
#gateway 192.168.1.1
#dns-nameservers 200.165.132.148
#netmask 255.255.255.0
#-=-=-=-=-=-Static config[end]-=-=-=-=-=-=
wpa-driver wext
wpa-ssid <MyNetworkessid>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <My hex pass using wpa_passphrase>

```

6 - ndiswrapper loaded with "depmod -a" and "modprobe"
7 - ndiswrapper installed and load at ubuntu startup
8 - I restarted the network services ". /etc/init.d/networking restart" 
9 - Iwconfig returns:
```

wlan0     IEEE 802.11g  ESSID:"<MyNetworkId>"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: AX:5X:FX:2X:9X:4X<access point mac>   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
11 - Dhcp is working and giving a valid ip (wireless network range).
10 - It's connected, but I can't even ping the gateway 192.168.1.1
12 - I disabled My two onboard wired cards by the way.

Now, I need some help, any suggestions?

---

### Post by afeasfaerw23231233 on 2009-03-11
I bump this thread for you.
I have the same very weak signal isuue on my realtek 8187 too. 
I am using ndiswrapper win 98 driver now and the wireless siganl will be broken if distance from the router to the notebook more than 3 metres, making the wlan completely useless. 
The native driver came with ubuntu 8.10 kernel 2.6.27-11 is even worst. 

Bump.

---

### Post by AggravatedGestalt on 2009-08-15
I found the following to work perfectly after many hours of misery and failure:

 # sudo apt-get install linux-backports-modules-jaunty

This also fixed my issue with the atheros ar9285 internal wifi card.

Asus k50IJ, Ubuntu, Jaunty

---

