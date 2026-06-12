---
title: "Airlink 101 doesn't start automatically"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by abudaba on 2011-04-05
Good morning,
 
Just got an Airlink 101 AWLL5088 wireless usb card and was able to install it throught a linux driver from Realtek. The problem I'm having is when I turn on the machine I have to manually connect to it each time instead of automatically running at boot up. Is there a setting I need to change somewhere.
 
Thank you!

---

### Post by abudaba on 2011-04-05
The wireless starts only when I click on the wireless icon>connect to hidden wireless network.
I choose my wireless entry, type my password and the wireless is up again.
If I shutdown or restart I loose my wireless connection.
Connect automatically is checked as well.

Here is my iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:"xxxx"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 11:22:33:AA:BB:CC
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/100  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I tried to add some entries to /etc/network/interfaces but no luck:

auto lo
iface lo inet loopback

auto wlan2
iface wlan2 inet dhcp
wireless-essid xxxxxxxxxxxx
wireless-key xxxxxxxxxxxxxx

Thanks for any help.

---

### Post by abudaba on 2011-04-06
Can any senior member help?

---

