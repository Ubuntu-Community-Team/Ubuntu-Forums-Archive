---
title: "eeePC 901 dropping wifi connection - need new driver?"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by BrendanM on 2010-01-05
Here's the situation: I've got an eee pc 901 running Ubuntu 9.10 netbook remix. I'm using it to connect to a WPA-encrypted wireless network on a WRT54GL running dd-wrt. It mostly connects and works ok, but sometimes it just stops working for no apparent reason (the netbook still shows itself as connected), but you can't get anywhere until you manually disconnect and reconnect. Other times, it will drop the connection, and then quickly reconnect (or sometimes not). Obviously, this behavior is pretty irritating. At first I thought the problem was with the router, but I checked the logs there and they all seem fine, and other computers on the same router don't have this problem.

Looking at "dmesg | tail" on my netbook, I see a lot of instances of the following error, which I'm thinking is probably the problem: 

```

[11137.762233] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[11142.872797] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 440
[11152.883274] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 556
[11152.883529] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[11163.952056] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!

```

I searched for that error message and I found this Ubuntu bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376577](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/376577) that describes symptoms that match mine.

In that report, a poster mentions that he compiled and installed a new version of the wireless driver from the Ralink website, and it fixed his problem. Do you think installing a new driver would help me? Or has that updated driver already been added to the kernel since that bug report was filed?

If I should install that driver, could somebody please tell me the steps I'd need to take to do that? I've never compiled a kernel module before.

One other thing, I also see repeated instances of these lines (or similar ones) in dmesg, which look like they could be related.

```

[44096.275923] RX DESC f30ca000  size = 2048
[44096.276885] <-- RTMPAllocTxRxRingMemory, Status=0
[44096.281404] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[44096.281424] 1. Phy Mode = 0
[44096.281435] 2. Phy Mode = 0
[44096.309841] 3. Phy Mode = 0
[44096.314533] MCS Set = 00 00 00 00 00
[44096.316196] <==== RTMPInitialize, Status=0
[44096.316280] 0x1300 = 000a4260
[44096.401269] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[44096.472502] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 116
[44096.472977] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[44106.768056] ra0: no IPv6 routers present

```

---

### Post by CarlAdam on 2010-01-15
Same problem here but with an Aspire One. Will get back if I find any solution. My dmesg | tail looks like this:

[ 1194.471451] ath5k phy0: unsupported jumbo
[ 1366.728668] wlan0: disassociating by local choice (reason=3)
[ 1378.261784] wlan0: authenticate with AP 00:21:91:ec:a7:c1
[ 1378.263913] wlan0: authenticated
[ 1378.263925] wlan0: associate with AP 00:21:91:ec:a7:c1
[ 1378.267482] wlan0: RX AssocResp from 00:21:91:ec:a7:c1 (capab=0x421 status=0 aid=2)
[ 1378.267494] wlan0: associated
[ 1405.640084] ath5k phy0: unsupported jumbo
[ 1465.132848] ath5k phy0: unsupported jumbo
[ 1629.500229] ath5k phy0: unsupported jumbo

---

