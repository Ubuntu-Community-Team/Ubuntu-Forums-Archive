---
title: "Wifi problems when using mains power on laptop"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by roton on 2013-02-09
This is really weird, but it is happening.

When I use mains power on my laptop, every other wireless device on the network has its connection slowed down so much that it's not usable.
However, when using wifi on battery there are no problems with the network.

- Ubuntu 12.04 (fully updated)
- Broadcom (BCM4313) chipset

The syslog is showing the "could not get rate" and "could not get rssi" errors, but that is not important right now; I will hopefully fix that later. I am more concerned about what the difference is between mains and battery in relation to wifi.

Wireshark is not showing any problems imo, however I will post the output if necessary.

Power settings seem to be identical on both battery and mains. I have also tried different power sockets in the room.

Any suggestions on what to check next would be really helpful.

---

### Post by praseodym on 2013-02-09
Hi,

please show the output of:```

iwconfig
```
If the power management is "on" disable it with:
```

sudo iwconfig wlan0 power off
```

---

### Post by roton on 2013-02-09
Thank you for the quick reply and excellent solution my friend.
The mains power management was already off. I changed it to on and now it seems to have fixed the issue (the laptop is still slightly slow, but I believe this to be related to the errors flooding my syslog).

Now the iwconfig is:

```
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"my_ssid"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: **:**:**:**:**:**   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```

Out of interest, is there an explanation as to why this happens without power management?

---

