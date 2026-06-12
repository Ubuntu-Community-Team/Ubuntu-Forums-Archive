---
title: "[Ubuntu 10.04] can't connect to AP after changing MAC address"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by cftmon on 2011-01-24
I have a school project that requries me to bypass MAC filtering by changing my MAC address.
I changed my mac address through the following:
```

sudo service network-manager stop
sudo ifconfig wlan0 hw ether 00:11:22:33:44:55
sudo service network-manager start

```when i try to connect to my access point through network-manager , it would always time out.Bringing the interface down then up does not help too.Even if my AP is open , or using encryption it just refuses to connect. I got this in my syslog though everytime i try to connect
```

Jan 24 19:08:05 eug-desktop kernel: [ 3856.843332] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```i did not use maverick because i encountered the same prob as[ this]("https://bugzilla.redhat.com/show_bug.cgi?id=629644"): 
I am using the default rt2400usb driver that came with ubutnu by default. Is this a driver prob or a network-manager problem?

---

### Post by cftmon on 2011-01-24
Somehow if my AP is already inside the preferred list(Right click Netowrk Manager->Edit connections->Wireless ), and then i run the commands above,network manager would attempt to connect back and the association would be successful with my spoof MAC.

A bit of sidetrack,If i try iwconfig essid <AP> followed by sudo dhclient wlan0 , i can't associate to the AP.dhclient would just say "no DHCPOffers received".Anybody know why?

---

### Post by cftmon on 2011-01-24
ok, i solved the problem by taking network manager out of the equation.
if network manager is up then:
```

sudo service network-manager stop
sudo ifconfig wlan0 hw ether [mac address]
sudo iwconfig wlan0 essid "myessid"
sudo dhclient wlan0

```Now my AP sees me with my new forged MAC address. :)

---

