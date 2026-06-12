---
title: "Wireless no longer works"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by ~LoKe on 2011-02-13
My wireless worked fine in Ubuntu 10.10 when I installed it.  Within the past week I've screwed around and installed some things (which things, I can't remember).  I rebooted today just because, and now my wireless no longer works.  I assume it's because of something I did before, and rebooting triggered it.

Anyway..

> n0c@monkey:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:4a:2d:c8
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe4a:2dc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:830812 (830.8 KB)  TX bytes:177225 (177.2 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19123 (19.1 KB)  TX bytes:19123 (19.1 KB)

virbr0    Link encap:Ethernet  HWaddr ea:2f:d3:33:a2:a4
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::e82f:d3ff:fe33:a2a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:25449 (25.4 KB)

> n0c@monkey:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
virbr0    no wireless extensions.
> n0c@monkey:~$ dmesg|grep iwl3945
[   19.119629] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   19.119633] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   19.119726] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.119741] iwl3945 0000:0b:00.0: setting latency timer to 64
[   19.174811] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   19.174815] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.174968] iwl3945 0000:0b:00.0: irq 46 for MSI/MSI-X
[  120.021225] iwl3945 0000:0b:00.0: iwlwifi-3945-2.ucode firmware file req failed: -2
[  120.029137] iwl3945 0000:0b:00.0: iwlwifi-3945-1.ucode firmware file req failed: -2
[  120.029142] iwl3945 0000:0b:00.0: Could not read microcode: -2


Any ideas/  I've tried downloading the firmware packages (linux-firmware, and firmware-iwlwifi) but that didn't help.  I also compiled the nightly build of iwlwifi-3945-ucode, but that didn't help either.  I switched from nm-applet to wicd and that still leaves me in the same situation.

I'm stumped.

---

### Post by ~LoKe on 2011-02-14
Bump.

---

### Post by ~LoKe on 2011-02-14
No ideas?

---

