---
title: "Cannot connect via usb network adapter"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by wah fun on 2010-01-07
I have a Belkin N150 USB Wireless Network Adapter and a Belkin N150 Wireless Router. I cannot seem to get NetworkManager to connect to the internet. I have blacklisted the 9.10 staging driver and associated rt files. I have downloaded and built the ralink 2.3.0.0 driver. The light flashes on the usb but I cannot connect to internet.

lsusb output:
jerry@jerry-desktop:~$ lsusb
Bus 002 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:09c2 Logitech, Inc. 
Bus 001 Device 005: ID 050d:935b Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod output:
jerry@jerry-desktop:~$ sudo lsmod
Module                  Size  Used by
rt2870sta             554908  1 

iwconfig output:
jerry@jerry-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am not sure what the ra0 is telling me but what about the Access Point: Not-Associated statement? Does that mean that the network adapter is not connecting to the router?

I would appreciate any help.

thx

---

### Post by wah fun on 2010-01-08
OK. No replies? So, evidently this is a problem that no one can solve? I like ubuntu but am not liking the support. I would really appreciate any help!

thx

---

