---
title: "Slow internet (not IPV6 / DNS related) on 10.10"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by cullion on 2011-02-12
Hi guys,

Have searched these forums up and down, and though a lot of people have experienced degraded internet access, none of them seem to be experiencing exactly my issue.

I'm running Ubuntu 10.10 on an old Thinkpad R40. Using wireless on my mac, speedtest.net reports my bandwidth at about 19Mbit. The same test on the Ubuntu machine (wired, this time) comes back as about 3Mbit. Initial connection speed is ok; it's still a 3Mbit connection so pages load quickly. But why is it 6x slower than on the Mac?

The Thinkpad's onboard NIC is broken, so I've been using a USB Nic. The sticker on it says it's a Dynamode, but lsusb reports it as *Realtek Semiconductor Corp. RTL8150 Fast Ethernet Adapter*.

I've tried disabling IPV6, but this had no effect.

This is what iwconfig reports:

```

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth2      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Does anyone have an idea what's going on? Any other information I can provide?

**Edit:** Ran speedtest.net on my Mac again this time using the same cable I'm using on the Thinkpad (but not the USB NIC)... the results are also around 19Mbit, which indicates the problem is either with the NIC or my Ubuntu setup.

---

