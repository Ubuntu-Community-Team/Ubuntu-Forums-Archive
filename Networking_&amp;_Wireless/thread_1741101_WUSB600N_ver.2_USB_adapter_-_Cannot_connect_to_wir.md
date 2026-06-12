---
title: "WUSB600N ver.2 USB adapter - Cannot connect to wireless network"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by siranidis on 2011-04-27
Hi

I run Ubuntu 10.04 64bit. I managed to get my Linksys adaptor working by following the info [here]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N").

I am now able to see all available networks but I cannot connect to any of them. I disabled the security for my home network but again no luck. I managed to connect to my router using my mobile, so I guess that the problem is with the adaptor.

Here is what I get by running iwconfig :


lo        no wireless extensions.
eth0      no wireless extensions.
ra0       Ralink STA  ESSID:"Test2"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: C8:CD:72:B0:3A:38   
          Bit Rate=1 Mb/s   
          RTS thr: off   Fragment thr: off
          Encryption key: off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
vboxnet0  no wireless extensions.

Any help is appreciated.

---

### Post by kittkatt on 2011-05-05
Download the [file in this post]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85"), then follow the instructions as laid out in the comment (remember to restart after building).  You may or may not need to blacklist the following drivers in your /etc/modprobe.d/blacklist.conf file if it still doesn't work.

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800pci
blacklist rt2x00pci

---

