---
title: "adhoc wifi"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2012-02-09
Hi,

I have a new Samsung n110 netbook, and it works fine on my home and work wifi networks, but when I try to use it through my phone using the wifi hotspot feature, it doesn't seem to connect to the network.

The symptoms are as if it doesn't get a response from DHCP.

When I try to use my regular laptop with my phone, it works just fine (I'm using it now), so it's not the phone.

In syslog, I see some messages from wpa_supplicant:

```
nl80211: Failed to set interface into IBSS mode
Association request to the driver failed.

```

plus a bunch of other messages.

Any ideas how to debug this and to get it working with my phone?

Thanks,

Max.
ubuntu 11.10 running unity. I use the network manager applet on both systems. Wifi has no password.

---

### Post by davidmaxwaterman on 2012-02-23
> **davidmaxwaterman said:**
> Hi,

I have a new Samsung n110 netbook, and it works fine on my home and work wifi networks, but when I try to use it through my phone using the wifi hotspot feature, it doesn't seem to connect to the network.

The symptoms are as if it doesn't get a response from DHCP.

When I try to use my regular laptop with my phone, it works just fine (I'm using it now), so it's not the phone.

In syslog, I see some messages from wpa_supplicant:

```
nl80211: Failed to set interface into IBSS mode
Association request to the driver failed.

```

plus a bunch of other messages.

Any ideas how to debug this and to get it working with my phone?

Thanks,

Max.
ubuntu 11.10 running unity. I use the network manager applet on both systems. Wifi has no password.

FYI, I booted the netbook to 11.04 and it still didn't work, and booted my laptop (remember, it works fine with 11.04) to 11.10, and it still worked.
Looks like it is something specific to the Samsung n110.

My Samsung n110 has a Broadcom BCM4313.

---

### Post by tumutanzi.com on 2012-05-19
> **davidmaxwaterman said:**
> FYI, I booted the netbook to 11.04 and it still didn't work, and booted my laptop (remember, it works fine with 11.04) to 11.10, and it still worked.
Looks like it is something specific to the Samsung n110.

My Samsung n110 has a Broadcom BCM4313.

I guess the hardware of your netbook may be not compatible for the ad-hoc wifi, but I am not sure.

My Acer netbook works using this kind of wifi connection.

---

### Post by SleepWalkerX on 2012-05-20
I'm confused.  When you setup adhoc wifi, did you setup a static address along with it?  

You'll need to have a static ip like 192.168.1.6 for your netbook's adhoc ip address and have the phone connect to your adhoc network with an ip of something like 192.168.1.7 so they can communicate with each other.  

If you don't manually specify the ip addresses then you need to setup some dhcp server on the netbook that runs on the adhoc interface.

---

