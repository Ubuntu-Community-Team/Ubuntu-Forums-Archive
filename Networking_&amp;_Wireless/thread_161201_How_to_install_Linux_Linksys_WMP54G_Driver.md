---
title: "How to install: Linux Linksys WMP54G Driver"
date: 2006-04-16
forum: Networking &amp; Wireless
---

### Post by Dambrosio on 2006-04-16
So I come across the problem of getting my Linksys WMP54G wireless card to be recognized in linux. I installed ndiswrapper and got it to work but it would randomly shut off and i would have to restart to get my wireless connection back. I was searching around and I found that the chipset maker for the wireless card came out with a native linux driver. [http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm") under Linux 11g-RT2500.
I was wondering if I could use this driver for my linksys wireless adapter. And if anyone can guide me through the install with the driver.
Thanks a bunch!
Dan

---

### Post by bryanl on 2006-04-16
The WMP54G is natively supported with the RA open source driver. You do not need ndiswrapper for a windows driver and you do not need the wpa supplicant install. If I understand correctly, the driver is in Breezy as well as Dapper

But it does not talk to the network manager for WPA security.

I am using it with Dapper. I added a clause to /etc/network/interface as

auto ra0
iface ra0 inet dhcp
  pre-up iwconfig ra0 essid [network name]
  pre-up iwconfig ra0 mode managed
  pre-up ifconfig ra0 mtu 1492
  pre-up iwpriv ra0 set Channel=[channel you are using]
  pre-up iwpriv ra0 set AuthMode=WPAPSK
  pre-up iwpriv ra0 set EncrypType=TKIP
  pre-up iwpriv ra0 set WPAPSK=[your WPA pass key phrase]
  pre-up iwpriv ra0 set TxRate=0
  pre-up ifconfig ra0 up

this does not bring up the interface on boot. For that, I need to 
 > sudo ifdown ra0
 > sudo ifup ra0
and that usually works but it keeps falling down so I have to repreat the down up when I see no traffic. I am still trying to figure out why it requires manual dinkering and won't stay up but I hope this will give you a start.

for more information see
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500)
[http://www.linksysinfo.org/](http://www.linksysinfo.org/)

---

