---
title: "Wireless key lost on reboot after installing ndiswrapper (x64 flash player)"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by composites on 2009-02-07
I recently installed x64 Flash Player from [Adobe Flash install information for AMD64](http://ubuntuforums.org/showthread.php?t=772490), using the first set of instructions.

As others have reported, my network security key continues to reset itself upon rebooting. This is a huge pain and leaving the network unsecured is not an option. Having to manually edit it every time I reboot is also not an option.

I have followed suggestions from the following threads: [Network Manager + NDISWrapper settings lost after reboot](http://ubuntuforums.org/showthread.php?t=235276) and [Wireless network dissapears on reboot.....](http://ubuntuforums.org/showthread.php?t=711103)

But adding
```
ndiswrapper
```
to **/etc/modules** has had no affect. It is mentioned in [WifiDocsDriverNdiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Configuring%20Wireless%20Network%20Settings%20using%20nm-applet%20(GNOME%20front%20end%20for%20Network%20Manager) that if you are manually configuring your network not to add that line as ndiswrapper will be started by **/etc/modprobe.d/ndiswrapper**, but that doesn't exist either.

**/etc/network/interfaces** appears to be correct:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-psk 197795b73fdc1925ee41959942883f61f2a209140483c104405623a6e4fbf18d
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid O2wireless
```
or
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-psk 197795b73fdc1925ee41959942883f61f2a209140483c104405623a6e4fbf18d
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid O2wireless
auto wlan0
```

There is no difference between **/etc/network/interfaces** from rebooting (not working) to re-entering the security key (working), which doesn't make any sense to me either.

---

