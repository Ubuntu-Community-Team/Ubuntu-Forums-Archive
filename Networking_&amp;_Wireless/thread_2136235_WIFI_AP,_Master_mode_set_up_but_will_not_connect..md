---
title: "WIFI AP, Master mode set up but will not connect."
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by IainDaddy on 2013-04-16
Hi all,

I have a WIFI blind spot in the house, the kitchen, as I like to have the news on while I'm working I like to have the laptop with me.  To cure the blind spot problem I have put a WIFI card in my Ubuntu server and set it up using the following documentation:
[https://help.ubuntu.com/community/WifiDocs/WirelessBroadcastSystem](https://help.ubuntu.com/community/WifiDocs/WirelessBroadcastSystem)
[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

After some prodding and the use of a hammer I got it up and running and I can see the WIFI card SSID on my laptop and I can get a login prompt... and that is as far as I can get.  The laptop just keeps asking for the password.

So... 
Q1) I've not been able to find where any of the processes are sending logs to, so any help with that please (do I need to enable logging?)
Q2) The password system is poorly documented, does anyone have clear instructions about lengths and valid charicters?
Q3) This documentation seems to be for V7(Feisty Fawn) and we are on V12, is the documentation still relivent?

the output of iwconfig is:
```
lo        no wireless extensions.

wlan1     IEEE 802.11bg  Mode:Master  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth1      no wireless extensions.

mon.wlan1  IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
 
```

hostapd is running and just says:
```
Configuration file: hostapd.conf
Using interface wlan1 with hwaddr 00:12:17:82:51:d0 and ssid 'FBISecurityVan'
wlan1: STA 9c:b7:0d:bf:51:14 IEEE 802.11: authenticated
wlan1: STA 9c:b7:0d:bf:51:14 IEEE 802.11: associated (aid 1)
AP-STA-CONNECTED 9c:b7:0d:bf:51:14
wlan1: STA 9c:b7:0d:bf:51:14 RADIUS: starting accounting session 516E7397-00000000
AP-STA-DISCONNECTED 9c:b7:0d:bf:51:14

```

If anyone can shed any light on where I'm going wrong PLEASE do.

All the best.

Iain

---

