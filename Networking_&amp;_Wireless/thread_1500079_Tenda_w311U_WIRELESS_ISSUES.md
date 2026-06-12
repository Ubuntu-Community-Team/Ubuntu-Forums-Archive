---
title: "Tenda w311U WIRELESS ISSUES"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by gonjaman on 2010-06-02
Hi,
I'm new to Ubuntu and am trying to get a Tenda W311u usb wireless working in 10.4:-

root@greenway-desktop:/var/log# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 005: ID 148f:3070 Ralink Technology, Corp.** 
Bus 001 Device 004: ID 14cd:8168 Super Top 
Bus 001 Device 003: ID 04b8:0007 Seiko Epson Corp. Printer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Got the Windows driver disk and it includes an rt2870.inf driver, not 3070.


root@greenway-desktop:/var/log# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"BTHomeHub2-C77S"  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: 00:8B:5D:8C:4B:4A   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-49 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Wireless is showing enabled in system/admin/network tools @ hardware address c8:3a:35:cb:1c:10 and seems to be transmitting/receiving data. 

However, wireless is showing disconnected but available.

I've searched a load of forums and tried to follow the guidance, but to no avail.

Would very much appreciate someone talking me through what's wrong.

Many thanks.

---

### Post by bkratz on 2010-06-02
See this thread, good luck

[http://ubuntuforums.org/showthread.php?t=1444925&highlight=w311U](http://ubuntuforums.org/showthread.php?t=1444925&highlight=w311U)

---

### Post by gonjaman on 2010-06-02
Hi Bkratz,

Followed it OK but still no joy. If I go top right of the screen, I get the spinning clock and it periodically asks me for my password, but still doesn't seem to connect. But when I click on the spinning clock, it allows to click 'disconnect'.

I'd be grateful for your comments.

---

