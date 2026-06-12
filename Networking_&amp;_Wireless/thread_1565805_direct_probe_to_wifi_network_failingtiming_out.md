---
title: "direct probe to wifi network failing/timing out"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by techrascal on 2010-09-01
Hello

Until a few days back i was easily able to connect with 40% of wifi signal. However from the last 2 days I am unable to connect.

Dmesg gives me this output repeatedly until it stops probing.

[ 5594.996580] wlan0: direct probe to AP 00:1b:90:77:c4:30 try 3
[ 5595.196565] wlan0: direct probe to AP 00:1b:90:77:c4:30 timed out

Wifi card is : Intel Corporation Wireless WiFi Link 5100

running ubuntu 9.04 32 bit 

Any help regarding the starting point to investigate the issue would be great.

Cheers!!

---

### Post by MaindotC on 2010-09-01
You'll have to try following the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  That will guide you as to the commands and output you should be viewing for troubleshooting.  If you're having difficulty with the guide, please let us know at what point and we'll help you further.

---

### Post by techrascal on 2010-09-01
Thanks for the indication.....i'll try to find the fault..

---

### Post by techrascal on 2010-09-01
I tried a few methods mentioned and found that it detects the wifi signal but it doesnt associate access point with the system. When i went pretty close to the wifi source it was able to connect, but it dropped the connection aftrer moving a bit farther. 
It never used to happen earlier and my other devices like ipod connect to the wifi at the same distance quite well.

Any pointers for correcting it ?

---

### Post by techrascal on 2010-09-01
this the output i get when i try to connect via the terminal

root@techrascal-laptop:/home/techrascal# iwconfig wlan0 mode managed channel 12 key open essid INS
root@techrascal-laptop:/home/techrascal# iwconfig wlan0 ap 00:1b:90:77:c4:30
root@techrascal-laptop:/home/techrascal# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:22:fb:95:e8:ac
Sending on   LPF/wlan0/00:22:fb:95:e8:ac
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@techrascal-laptop:/home/techrascal#

---

### Post by aero13972486 on 2011-08-25
This 'direct probe' three strike timeout still seems to be a problem in Ocelot 11.10 with kernel 3.0

I've got an AR9271.

---

