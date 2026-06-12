---
title: "Any 32-bit linux drivers for the rt73 ?"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by mtbuller on 2006-06-22
Had downloaded the drivers for a USB wireless adapter that uses the RT73 chipset from [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) and was having some problems.

Immediately after building the driver, internet connection is okay. But upon reboot the next day, the internet connection is unable to connect.

The command "iwconfig" reports

> 
rausb0 RT73 WLAN ESSID:"myessid"
Mode:Managed Channel=10 Access Point: 00:C0:00:C0:F0:C0
Bit Rate=36 Mb/s
RTS thr:  off Fragment thr: off
Encryption key:  off
Link Quality=71/100 Signal level:-68 dBm Noise level:-99 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0



Found out from some other forums that the driver RT73_Linux_STA_Drv1.0.3.0.tar.gz is actually for 64bit linux.

Any idea where I can get hold of drivers (for 32bit linux) for RT73.

Many thanks in advance for the advice.

---

### Post by linuxgeekery on 2006-06-22
Are you sure it's the drivers? If you use DHCP, try restarting dhcp (sudo killall dhclient3 && dhclient3). You can get 32 bit drivers by downloading the source for the driver from Ralink's website and compiling it yourself. Be sure to install the build-essential package first, if you don't already have it.

---

