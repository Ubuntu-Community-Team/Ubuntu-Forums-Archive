---
title: "Wireless not working"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by manav_1001 on 2009-12-06
Hi everyone,

I logged into Ubuntu today and my wireless was not working. Usually when this happens I just restart and the wireless works, but this time instead of restarting I did sudo ifconfig eth0 down and then sudo ifconfig eth0 up. 
Nothing happened after I did this, so I restarted....still nothing. So I restarted again and booted to Vista and even there the wireless was not working. I turned the wireless switch off and on but still there was a red x on the network icon next to the clock. I uninstalled my network driver and reinstalled it, but that didnt help too.
I booted into Ubuntu again and did ifconfig eth0 and this is the result I got:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:f0:26:c2  
          inet6 addr: fe80::21b:38ff:fef0:26c2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55697 (55.6 KB)  TX bytes:7137 (7.1 KB)
          Interrupt:16 Base address:0x1000 
```

Someone, Please help me bring back my wireless connectivity.

---

### Post by northd_tech on 2009-12-07
Can you post the results of the following terminal commands here?

```

lshw -C network

lspci

lsusb

lsmod

ifconfig

iwconfig

```"eth0" is your cable network connection- have you tried hooking up a cable?  That's often the easiest[/only?] way to get your wireless working.  Once we figure out what kind of hardware you have, we can go from there.

It seems a little odd that it also quit under Windows about the same time, though.  Have you tried cycling the power on your cable modem and/or wireless router?  Sometimes ours will get "locky" and turning it off for a few minutes is the only way to bring it back up.  That's usually related to Comcast cable TV trouble, and we often need to call the ISP to get things running correctly.  I'm not sure what they "reset" on their end, but we've had to do that several times.

Usually, the wireless interface will be called "wlan0" by the ifconfig and iwconfig commands, and the up/down commands are fairly similar (but can vary on location and syntax, depending upon your hardware).

---

