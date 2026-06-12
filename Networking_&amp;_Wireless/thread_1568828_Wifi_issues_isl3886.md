---
title: "Wifi issues: isl3886"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by Wolf9466 on 2010-09-05
It's a 2wire 802.11g PCMCIA card, it initially didn't show up at all. After I used "modprobe prism54" it would show up, but it would not work.


```
# ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 00:30:b4:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

```

But if I try something like:


```
# ifconfig eth2 up
SIOCSIFFLAGS: No such file or directory
```

When I use iwconfig, it shows:

```
eth2      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And for information about the card, lspci and dmesg show:

```
03:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
```

```
# dmesg | grep eth2
[   16.166961] eth2: resetting device...
[   16.166982] eth2: uploading firmware...
[   16.297159] eth2: could not upload firmware ('isl3886')
[   16.297162] eth2: islpci_reset: failure
[   16.659059] eth2: resetting device...
[   16.659080] eth2: uploading firmware...
[   16.865501] eth2: could not upload firmware ('isl3886')
[   16.865504] eth2: islpci_reset: failure
[   78.836123] eth2: resetting device...
[   78.836139] eth2: uploading firmware...
[   78.888801] eth2: could not upload firmware ('isl3886')
[   78.888804] eth2: islpci_reset: failure
[   80.102824] eth2: resetting device...
[   80.102848] eth2: uploading firmware...
[   80.155124] eth2: could not upload firmware ('isl3886')
[   80.155127] eth2: islpci_reset: failure
[   80.853181] eth2: resetting device...
[   80.853200] eth2: uploading firmware...
[   80.906545] eth2: could not upload firmware ('isl3886')
[   80.906548] eth2: islpci_reset: failure
[ 1667.876328] eth2: hot unplug detected
[ 1667.876336] eth2: removing device
[ 1706.358593] eth2: resetting device...
[ 1706.358614] eth2: uploading firmware...
[ 1706.470085] eth2: could not upload firmware ('isl3886')
[ 1706.470093] eth2: islpci_reset: failure
[ 1706.525518] eth2: resetting device...
[ 1706.525544] eth2: uploading firmware...
[ 1706.586317] eth2: could not upload firmware ('isl3886')
[ 1706.586320] eth2: islpci_reset: failure
[ 1825.778779] eth2: resetting device...
[ 1825.778803] eth2: uploading firmware...
[ 1825.861822] eth2: could not upload firmware ('isl3886')
[ 1825.861826] eth2: islpci_reset: failure
```

And one more thing, I have tried to install the firmware for it, but it hasn't seemed to work. Anyone know how to fix this?

---

