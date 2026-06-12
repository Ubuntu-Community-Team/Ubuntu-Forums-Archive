---
title: "D-Link DWL G122 rev C not recognized under lsusb"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by marcus121 on 2013-01-20
So, to say, I've been using windows almost 10 years now. For some advantages, I set up windows 7 and ubuntu 11.04 dual boot- Everything was working fine, and then it updated to 11.10 . The only problem that came is that my usb dongle is now not working. Then I tried to fix it with a series of other discussions that worked for someone but not for me. So to give some info that I acquired (i'm noob when its about linux) : 

"lsusb" command doesnt show it,
"lsmod | grep rt73usb" as described on wiki, shows that driver is loaded

What can I try other? 
But to tell 1 more time, I'm completely new to this, so if I have to run some command please type it fully how I'm supposed to type it in terminal.

Thank you.

---

### Post by chili555 on 2013-01-20
Please insert the device and run and post the result of these two separate commands from a terminal:```
lsusb
iwconfig
```Thanks.

---

### Post by marcus121 on 2013-01-20
And now it works, and now its detected by usb.

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c03 D-Link System AirPlus G DWL-G122 Wireless Adapter(rev.C1) [Ralink RT73]
Bus 002 Device 002: ID 04cf:8819 Myson Century, Inc. USB 2.0 SD/MMC Reader
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 04f2:0833 Chicony Electronics Co., Ltd 
```


But why this happened anyway? 
I can also see it now on list but before reboot it wasnt there.

Can you maybe tell me why is that?


Oh, here's for the iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Mario1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:17:D3:6B:E5   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:32   Missed beacon:0


```


I'm now typing from ubuntu on wireless.


Thanks for help, but why this happened? Should I update it to newer version?

---

### Post by chili555 on 2013-01-20
> Thanks for help, but why this happened? Should I update it to newer version?I have no idea what happened. If there is a repeat, I'd suspect a hardware issue, either the device or the USB port. I'd just keep a watch on it for now. Post back if we can assist again.

---

### Post by marcus121 on 2013-01-21
Well, why would it work on windows fine if its hardware issue?

And, also every device except mouse and keyboard (both USB) wasnt detected...


Thank You for help :)

---

### Post by chili555 on 2013-01-21
As I said, I haven't any idea. I suggest you keep an eye on it and post back if it acts up again.

---

