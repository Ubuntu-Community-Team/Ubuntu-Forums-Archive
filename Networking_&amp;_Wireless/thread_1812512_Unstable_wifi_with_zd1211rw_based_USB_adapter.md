---
title: "Unstable wifi with zd1211rw based USB adapter"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by staffann on 2011-07-26
I have a problem with my wifi connection being unstable with my Ubuntu 11.04 and a Philips USB adapter (SNU5600, based on zd1211rw). It can work for hours, but then it fails and cannot be made to work again unless I remove the adapter physically and reinsert it. Sometimes I even have to restart the network-manager daemon. When I check with iwconfig it is not tied to an access point. The gnome network manager cannot reconnect even though it indicates that it tries.

After it fails it looks like this:
```

staffan@bilbo:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````

staffan@bilbo:~$ lsusb
Bus 005 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0471:1236 Philips (or NXP) SNU5600 802.11bg
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I had the same problem in the beginning after I installed 10.04LTS, but after a while it disappeared (I don't remember if I did anything in particular). Now after the upgrade the problem reappeared.

ifdown and ifup doesn't recover the situation and choosing disconnect in the gnome upper panel doesn't even work.

Since this is a computer that is amongst other things used as a web server, it is critical that the network connection is stable. I do want to avoid having to use a cable (it will be long and will look awful), so is there anyone out there with a tip what could be wrong?

---

