---
title: "roaming and rt73"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Miaxi on 2009-01-27
Hello and thanks in advance for reading. 

My problem is that I can only get my usb dongle with rt73 chipset (serialmonkey drivers) to connect to this essid by manually editing the /etc/network/interfaces file. 

#-------------------
auto wlan0
iface wlan0 inet dhcp
dns-nameservers 192.168.0.1
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid youressid
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="yourpassword"
#-------------------

Any attempt to get it working with wpasupplicant, network-manager or wicd failed, however. 

Now I would like to be able to connect to open networks without having to manually edit the file. Can anybody give me a hint towards solving this problem?

---

