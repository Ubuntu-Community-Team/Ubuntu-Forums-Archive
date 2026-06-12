---
title: "Ubuntu doesn't detect some wireless networks"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by Nathan_M on 2009-09-16
I've had no wireless problems most of the time in 9.04 with by Broadcom 43xx wireless hardware, but sometimes when I try to connect to a new network, the network isn't even detected. It's not that it's hidden, and I can try entering the settings and still get nothing. One of the networks I managed to connect to just fine with 8.10, but I can't guarantee that the channel and things haven't changed since then, as I don't have access to the router. Windows computers can connect to it normally.

Does anyone have any ideas why this might be, and how I can fix it?

---

### Post by Ayuthia on 2009-09-16
It is most likely due to the signal noise.  The drivers in Linux are different than Windows so the signal ranges differ a little.

I am not for sure which Broadcom card you have.  You can always try a different wireless module (b43, wl, or NDISwrapper) and see if it works better.  They all vary slightly so sometimes a different driver might work better in a different situation.

The next time you have a chance, please try:
```
sudo iwlist scan
```
and check to see if other sites are using the same channel.  It could be that there is enough traffic to not get the signal.

---

### Post by Nathan_M on 2009-09-16
I'm typing this out from a different computer, hence the unusual format of the iwlist scan output:

Scan completed :
Cell 01 - Address: 00:1B:2F:A5:BE:DC
ESSID:"FreeSpirit"
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality: 4/5 Signal level:-62 dBm Noise level:-92 dBm
IE: WPA version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s

FreeSpirit isn't the network I'm trying to connect to... that one isn't listed because that's the problem! ;)

---

