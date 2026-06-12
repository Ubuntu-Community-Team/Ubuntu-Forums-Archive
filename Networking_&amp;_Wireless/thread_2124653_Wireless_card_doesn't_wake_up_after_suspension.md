---
title: "Wireless card doesn't wake up after suspension"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by PChialastri on 2013-03-11
Hi to all, my problem is almost described in subject.

This is my configuration: Ubuntu 12.04 (i386) on Sony Vaio VGN-FZ21E, wireless card (integrated) is **Intel PRO/Wireless 3945ABG [Golan]**. Here is the command otuput of **lshw -C network**command**[B]:**[/B]
```
description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:f3:eb:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=iwl3945  driverversion=3.5.0-23-generic firmware=15.32.2.9 ip=192.168.1.65  latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:fa000000-fa000fff

```
Sometimes (not always, but most of the times) after suspension the wireless card doesn't wake up. I tried both with Network-manager and WiCD. The issue doesn't change.
Then I had a look at the syslog (when the problem occurred after suspension) and I noticed the following lines:
```
Mar 11 17:33:25 pablo-laptop kernel: [ 5225.608061] sky2 0000:08:00.0: eth0: disabling interface
Mar 11 17:33:25 pablo-laptop kernel: [ 5225.619189] sky2 0000:08:00.0: eth0: enabling interface
Mar 11 17:33:25 pablo-laptop kernel: [ 5225.619706] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar  11 17:33:26 pablo-laptop kernel: [ 5226.637161] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:26 pablo-laptop kernel: [ 5226.637171] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:26 pablo-laptop kernel: [ 5226.764525] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:26 pablo-laptop kernel: [ 5226.764531] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:26 pablo-laptop kernel: [ 5226.891926] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:26 pablo-laptop kernel: [ 5226.891932] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:26 pablo-laptop kernel: [ 5227.019321] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:26 pablo-laptop kernel: [ 5227.019326] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:26 pablo-laptop kernel: [ 5227.146696] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:26 pablo-laptop kernel: [ 5227.146701] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar 11 17:33:26 pablo-laptop kernel: [ 5227.147044] iwl3945 0000:06:00.0: Unable to initialize device after 5 attempts.
Mar  11 17:33:31 pablo-laptop kernel: [ 5231.965726] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:31 pablo-laptop kernel: [ 5231.965735] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:31 pablo-laptop kernel: [ 5232.093091] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:31 pablo-laptop kernel: [ 5232.093097] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:31 pablo-laptop kernel: [ 5232.220442] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:31 pablo-laptop kernel: [ 5232.220447] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:32 pablo-laptop kernel: [ 5232.347782] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:32 pablo-laptop kernel: [ 5232.347787] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:32 pablo-laptop kernel: [ 5232.475196] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:32 pablo-laptop kernel: [ 5232.475201] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar 11 17:33:32 pablo-laptop kernel: [ 5232.475555] iwl3945 0000:06:00.0: Unable to initialize device after 5 attempts.
Mar  11 17:33:36 pablo-laptop kernel: [ 5236.981027] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:36 pablo-laptop kernel: [ 5236.981040] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:36 pablo-laptop kernel: [ 5237.111258] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:36 pablo-laptop kernel: [ 5237.111267] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:37 pablo-laptop kernel: [ 5237.241510] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:37 pablo-laptop kernel: [ 5237.241517] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:37 pablo-laptop kernel: [ 5237.371699] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:37 pablo-laptop kernel: [ 5237.371706] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:37 pablo-laptop kernel: [ 5237.501865] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:37 pablo-laptop kernel: [ 5237.501873] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar 11 17:33:37 pablo-laptop kernel: [ 5237.502352] iwl3945 0000:06:00.0: Unable to initialize device after 5 attempts.
Mar  11 17:33:44 pablo-laptop kernel: [ 5245.165294] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:44 pablo-laptop kernel: [ 5245.165302] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:45 pablo-laptop kernel: [ 5245.292676] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:45 pablo-laptop kernel: [ 5245.292681] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:45 pablo-laptop kernel: [ 5245.420165] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:45 pablo-laptop kernel: [ 5245.420171] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:45 pablo-laptop kernel: [ 5245.547518] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:45 pablo-laptop kernel: [ 5245.547523] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar  11 17:33:45 pablo-laptop kernel: [ 5245.675049] iwl3945 0000:06:00.0:  BSM uCode verification failed at addr 0x00003800+0 (of 900), is  0xffffffff, s/b 0xf802020
Mar 11 17:33:45 pablo-laptop kernel: [ 5245.675054] iwl3945 0000:06:00.0: Unable to set up bootstrap uCode: -5
Mar 11 17:33:45 pablo-laptop kernel: [ 5245.675425] iwl3945 0000:06:00.0: Unable to initialize device after 5 attempts.
```

Any idea ?! :(

---

### Post by PChialastri on 2013-03-12
UP !!! :confused:

---

### Post by chili555 on 2013-03-12
> **PChialastri said:**
> UP !!! :confused:I've responded at askubuntu.

---

### Post by PChialastri on 2013-03-12
Many thanks ! Im' going to view your answer !

[LINK TO ASK UBUNTU ANSWER]("http://askubuntu.com/questions/266857/ubuntu-12-04-wifi-not-working-after-suspension")

---

