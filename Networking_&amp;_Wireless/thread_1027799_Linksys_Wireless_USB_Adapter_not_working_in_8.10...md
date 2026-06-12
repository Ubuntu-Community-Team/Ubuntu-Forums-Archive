---
title: "Linksys Wireless USB Adapter not working in 8.10..."
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Sneaky07 on 2009-01-01
Hi I was following the tutorial [here]("http://ubuntuforums.org/showthread.php?t=530772") which was very helpful but when I try loading the driver it my desktop freezes up on me.  I've tried using the driver from the tutorial and from the Linksys website.  Neither one of them seem to work.  Also when I tried running the command:
```
sudo dmesg | grep ndis
```
I got a weird error and it said that it had failed to load basically.  I don't know what I'm doing wrong.  Has anyone else had this problem or know of a solution? :confused:

Edit:  I am also using the most current version of ndiswrapper:
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.27-9-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 
```

---

### Post by Sneaky07 on 2009-01-01
I finally got it sort of working... now I tried sudo dmesg | grep ndis and get:
```
[  594.732875] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  595.026554] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco Systems, Inc.,12/07/2006,1.0.5.1) loaded
[  596.022731] usbcore: registered new interface driver ndiswrapper
[  641.844398] ndiswrapper: device wlan0 removed
[  642.519826] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco Systems, Inc.,12/07/2006,1.0.5.1) loaded
[  668.816998] ndiswrapper: device wlan0 removed
[  669.497685] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco Systems, Inc.,12/07/2006,1.0.5.1) loaded
```
Anyone know what I'm doing wrong?  I also got my network to come up on the Netork Manager but it never connects to it.  I get one green light but it keeps crashing and trying again.  :confused:

Edit:  Also when I run iwconfig I get:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by oobe-feisty on 2009-02-22
did you end up finding out about this i only just upgraded to intrepid and im having the same problem as of today i will get back with and answer when i figure it out if you let me know how you are going

---

