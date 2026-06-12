---
title: "Linksys WUSB54GC and rt2870 Ubuntu 9.10"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by azagaros on 2010-01-02
I am at wits end with this frustration.  Ubuntu 9.10 and variants, like lime and kubuntu, I have tried. They all see the damn thing with both the default driver that came with Ubuntu 9.10 and the 2.3 from the ralink site.  The device isn't responding when plugged in and scanning for networks.  The network manager knows its a network adapter and not using it what so ever.  Other noted issues are it causes the kernal to hang when shutting down the box, not sure why.  Can't load Ubuntu gnome with the device plugged in, like hal is having problems with it.

Iwconfig returns

```
wlan1     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

for the adapter.. the tx-power or control of the device has me bothered. Besides the power management flag, and the tx-power are the only things different from the other wireless adapter on the box.  It is like linux and or the drivers don't know how to use it at some level.  I don't know where to look.

I don't know what I am looking for anymore to make this device "turn on" and scan for networks as it does in windows.

I am looking for any suggestions any paths for a solution to what I feel is a simple problem. 

I have followed most of the posts for this chip out there and need help getting through this.  When I see no posts or replies it looks like I have not asked the right question to the "intelligence" out there. I don't know if it is because of the week end or holiday season.

---

