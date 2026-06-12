---
title: "hostapd with Ralink RT2573"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by strguntbr on 2010-05-05
Hello!

I'm trying to set up an wifi-accesspoint with hostapd on ubuntu 9.10. The box does not have an internet connection and the clients should not be able to access the internet but just be able to connect to a webserver that is running on this specific box. Therefore no routing is necessary and no encryption either.

According to lsusb the wifi-device is a "Micro Star International RT2573 and according to lsmod the driver that gets loaded is "rt73usb".

```
iw list
``` gives me the following output
```
{...}
Supported interface modes:
 * IBSS
 * managed
 * AP
 * AP/VLAN
 * WDS
 * monitor
 * mesh point

```my current hostapd.conf:
```
interface=wlan0
driver=nl80211
ssid=test
channel=3
hw_mode=g
```my current dnsmasq.conf:
```
dhcp-authoritative
domain=test.local
domain-needed
expand-hosts
bogus-priv
filterwin2k
loq-queries
log-dhcp
except-interface=eth0
address=/#/192.168.0.1
dhcp-rang=192.168.0.100,192.168.0.199,12h
```We have the following devices for testing:
- iPhone
- Google Nexus One
- Sony Ericsson G900 (Symbian UIQ based)
- A Nokia Series 60 based Phone

When i start hostapd and dnsmasq and issue a ```
ifconfig wlan0 192.168.0.1 up
``` at first everything seems to work. I can connect with the iPhone, SE and Nokia to the WLAN, they all get valid settings from the dhcpserver and i can access the local webserver.
But when i try to connect with the Nexus one, it says it can't connect and afterwards the other phones all disconnect from the wlan and cannot reconnect.

Does anybode have an idea what could be going wrong here?

Thanks,
Marcus

---

