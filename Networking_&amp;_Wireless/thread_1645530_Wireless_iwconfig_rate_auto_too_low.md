---
title: "Wireless iwconfig rate auto too low"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by JamieKitson on 2010-12-14
Hi,

left to its own devices my wireless connects at too low a speed. I have a 20meg internet connection and my wireless is slowing it down to like 3meg. When I reboot into windows it's fine. When I run iwconfig eth1 rate 11M or even 24M the connection is much faster and runs fine, why won't it automatically go higher? Is this the fault of the driver? I am running Broadcom's driver compiled from source. Also, how can I set it to 24M at boot?

Thanks, Jamie

Edit: I guess I can put iwconfig eth1 rate 24M in rc.local, but I'd still like to get auto running higher, especially as my signal should be pretty good.

Output from iwconfig white rate=auto:

eth1      IEEE 802.11  ESSID:"honeypot"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: xxx   
          Bit Rate=1 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-47 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by JamieKitson on 2010-12-16
Found a bug report:

[https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/384920](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/384920)

---

