---
title: "iwlagn extreme lags with lucid"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by maulbongo on 2010-05-21
Hello folks,

This I have to show the world:
I use three Laptops at home, two with Intel Wireless WiFi Link 4965AGN and one with Intel Wireless WiFi Link 5100AGN.
All machines have been set up clean (without taking over home from old installation).
The WLAN connection lags extreme.
I stream for example Mythtv from one machine to other, with Karmic there were no problems using N-Mode.
Since Lucid it's getting on my nerves, periodicly the connection hangs up and watching TV is not really possible anymore.
As soon as I install linux-backports-modules-wireless-lucid-generic and restart the machines (already checked this with all three machines) kann WLAN can't be activated anymore. In dmesg these errors appears:

> [   11.616868] iwlagn: disagrees about version of symbol compat_request_firmware
[   11.616873] iwlagn: Unknown symbol compat_request_firmware

But they should look like this:

> [   10.964004] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   10.964007] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   10.964115] iwlagn 0000:06:00.0: enabling device (0000 -> 0002)
[   10.964129] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.964161] iwlagn 0000:06:00.0: setting latency timer to 64
[   10.964241] iwlagn 0000:06:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   11.023029] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels

When I uninstall linux-backports-modules-wireless-lucid-generic all WLAN modules are recognized again.
If I compile the latest compat wireless driver it is working for a short moment, but then no ping is going out anymore and the only possibility is to deactivate networking and activate it again.
I also tested everything with wicd, sadly with same results.
I have searched a lot and found out that a lot of people have these problems.
The only solution at the moment seems to be deactivating wireless N mode and use wireless G mode only.
This works stabel and I don't get lags or disconnections.
Generally  wireless N with Ubuntu for me is still not fast enough, if it's running good, I get a max speed 3 MB/s but most of the times it's 1,8 MB/s, which is even compared to Windows XP with most of the times is 4 MB/S and with max of 6 MB/s way too slow.
A lot of work has to be done here.
Who has got same problems, or even good working solutions ?
edit: when I tested wicd I also uninstalled networkmanager and I have also ipv6 deactivated.

---

### Post by maulbongo on 2010-05-23
Ok, solved.
Did another clean install to systems and now all working fine.
Perhaps those probs appeared because of all those wireless testings, but can't really tell why.

---

