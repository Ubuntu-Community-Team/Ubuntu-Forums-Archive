---
title: "Freeze on network cable plugging-in HP Mini 5101"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by d-fens on 2011-05-02
Since I upgraded to Ubuntu 11.04 my system freezes when I plugging-in an ethernet cable.

My network devices:
```
#sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:82:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-8-generic firmware=N/A ip=192.168.33.53 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:e8000000-e8003fff
  *-network
       description: Ethernet interface
       product: 88E8072 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:20:00.0
       logical name: eth0
       version: 10
       serial: 00:26:55:xx:xx:xx
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:e0000000-e0003fff ioport:2000(size=256) memory:7fc00000-7fc1ffff
```Crash Syslog
```

May  2 21:23:45 minime kernel: [ 1161.043751] ------------[ cut here ]------------
May  2 21:23:45 minime kernel: [ 1161.043811] WARNING: at /build/buildd/linux-2.6.38/net/mac80211/rx.c:2881 ieee80211_rx+0x8a/0x190 [mac80211]()
May  2 21:23:45 minime kernel: [ 1161.043822] Hardware name: HP Mini 5101
May  2 21:23:45 minime kernel: [ 1161.043828] Modules linked in: cryptd aes_i586 aes_generic nls_iso8859_1 nls_cp437 vfat fat binfmt_misc parport_pc ppdev snd_hda_codec_analog snd_hda_intel i915 snd_hda_codec snd_hwdep snd_pcm arc4 snd_seq_midi drm_kms_helper joydev snd_rawmidi drm brcm80211(C) snd_seq_midi_event i2c_algo_bit mac80211 snd_seq qcserial usb_wwan usbserial snd_timer psmouse snd_seq_device serio_raw uvcvideo videodev hp_accel snd lis3lv02d cfg80211 input_polldev soundcore snd_page_alloc video hp_wmi sparse_keymap lp parport usb_storage uas ahci libahci sky2
May  2 21:23:45 minime kernel: [ 1161.043965] Pid: 0, comm: swapper Tainted: G        WC  2.6.38-8-generic #42-Ubuntu
May  2 21:23:45 minime kernel: [ 1161.043973] Call Trace:
May  2 21:23:45 minime kernel: [ 1161.043998]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
May  2 21:23:45 minime kernel: [ 1161.044044]  [<f830ff4a>] ? ieee80211_rx+0x8a/0x190 [mac80211]
May  2 21:23:45 minime kernel: [ 1161.044089]  [<f830ff4a>] ? ieee80211_rx+0x8a/0x190 [mac80211]
May  2 21:23:45 minime kernel: [ 1161.044103]  [<c104f962>] ? warn_slowpath_null+0x22/0x30
May  2 21:23:45 minime kernel: [ 1161.044149]  [<f830ff4a>] ? ieee80211_rx+0x8a/0x190 [mac80211]
May  2 21:23:45 minime kernel: [ 1161.044165]  [<c14258a0>] ? skb_dequeue+0x50/0x70
May  2 21:23:45 minime kernel: [ 1161.044203]  [<f82f8abf>] ? ieee80211_tasklet_handler+0xaf/0xc0 [mac80211]
May  2 21:23:45 minime kernel: [ 1161.044218]  [<c1509716>] ? _raw_spin_unlock_bh+0x16/0x20
May  2 21:23:45 minime kernel: [ 1161.044279]  [<f858d8a8>] ? wl_dpc+0x58/0xb0 [brcm80211]
May  2 21:23:45 minime kernel: [ 1161.044293]  [<c1055ee5>] ? tasklet_action+0x55/0xe0
May  2 21:23:45 minime kernel: [ 1161.044305]  [<c1056622>] ? __do_softirq+0x82/0x170
May  2 21:23:45 minime kernel: [ 1161.044318]  [<c10565a0>] ? __do_softirq+0x0/0x170
May  2 21:23:45 minime kernel: [ 1161.044325]  <IRQ>  [<c10567ed>] ? irq_exit+0x6d/0x80
May  2 21:23:45 minime kernel: [ 1161.044346]  [<c15107ab>] ? do_IRQ+0x4b/0xc0
May  2 21:23:45 minime kernel: [ 1161.044358]  [<c107cbca>] ? tick_notify+0x11a/0x1d0
May  2 21:23:45 minime kernel: [ 1161.044372]  [<c1003670>] ? common_interrupt+0x30/0x38
May  2 21:23:45 minime kernel: [ 1161.044386]  [<c105007b>] ? console_unlock+0xdb/0xe0
May  2 21:23:45 minime kernel: [ 1161.044400]  [<c12c2508>] ? intel_idle+0xb8/0x110
May  2 21:23:45 minime kernel: [ 1161.044414]  [<c14061fd>] ? cpuidle_idle_call+0x7d/0x160
May  2 21:23:45 minime kernel: [ 1161.044426]  [<c10019ca>] ? cpu_idle+0x8a/0xc0
May  2 21:23:45 minime kernel: [ 1161.044438]  [<c1038d2e>] ? complete+0x4e/0x60
May  2 21:23:45 minime kernel: [ 1161.044452]  [<c14f0d2d>] ? rest_init+0x5d/0x70
May  2 21:23:45 minime kernel: [ 1161.044466]  [<c178d7e1>] ? start_kernel+0x35f/0x366
May  2 21:23:45 minime kernel: [ 1161.044479]  [<c178d3d5>] ? pass_all_bootoptions+0x0/0xa
May  2 21:23:45 minime kernel: [ 1161.044492]  [<c178d0e0>] ? i386_start_kernel+0xe0/0xe8
May  2 21:23:45 minime kernel: [ 1161.044501] ---[ end trace 86a011cc6d459342 ]---
May  2 21:23:58 minime kernel: [ 1174.204586] wl0: MAC Detected a change on the RF Disable Input 0x10000
May  2 21:23:58 minime kernel: [ 1174.249280] sky2 0000:20:00.0: eth0: Link is up at 1000 Mbps, full duplex, flow control both
May  2 21:23:58 minime kernel: [ 1174.251854] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  2 21:23:58 minime NetworkManager[556]: <info> (eth0): carrier now ON (device state 2)
May  2 21:23:58 minime NetworkManager[556]: <info> (eth0): device state change: 2 -> 3 (reason 40)
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) starting connection 'Auto eth0'
May  2 21:23:58 minime NetworkManager[556]: <info> (eth0): device state change: 3 -> 4 (reason 0)
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May  2 21:23:58 minime NetworkManager[556]: <info> (eth0): device state change: 4 -> 5 (reason 0)
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May  2 21:23:58 minime NetworkManager[556]: <info> (eth0): device state change: 5 -> 7 (reason 0)
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  2 21:23:58 minime NetworkManager[556]: <info> dhclient started with pid 2683
May  2 21:23:58 minime NetworkManager[556]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May  2 21:23:58 minime dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
May  2 21:23:58 minime dhclient: Copyright 2004-2010 Internet Systems Consortium.
May  2 21:23:58 minime dhclient: All rights reserved.
May  2 21:23:58 minimMay  2 21:24:59 minime kernel: imklog 4.6.4, log source = /proc/kmsg started.
May  2 21:24:59 minime rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="423" x-info="http://www.rsyslog.com"] (re)start
May  2 21:24:59 minime rsyslogd: rsyslogd's groupid changed to 102
May  2 21:24:59 minime rsyslogd: rsyslogd's userid changed to 101
May  2 21:24:59 minime rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May  2 21:24:59 minime kernel: [    0.000000] Initializing cgroup subsys cpuset
May  2 21:24:59 minime kernel: [    0.000000] Initializing cgroup subsys cpu
May  2 21:24:59 minime kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
May  2 21:24:59 minime kernel: [    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
May  2 21:24:59 minime kernel: [    0.000000] BIOS-provided physical RAM map:

``````

#uname -a
Linux minime 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
```The live cd also freezes when the network cable is plugged-in.

---

### Post by alxgomz on 2011-05-14
I have the very same problem on my HP ProBokk 5320m:

The system crashes as when I plug an ethernet cable in the RJ45 connector.
I am running debian squeeze with the2.6.32-5-686-bigmem kernel.

here are details about the chips involved:
```
*-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: ac:81:12:2d:b4:53
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 ip=192.168.1.65 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:d0700000-d0703fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 68:b5:99:f6:27:ec
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:2000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable) memory:d0420000-d043ffff(prefetchable)
```

 Crashes do not happen immediatly when plug in as i can see the network manager applet trying to bring the eth0 up... but it crashes right after.

I haven't any good solution for this issue yet. The workaround i use is unload the brcm80211 module before pluging-in the ethernet cable... that helps but is a bit annoying.

If someone as any idea... i'd love to ear about!

---

### Post by d-fens on 2011-05-15
> **alxgomz said:**
> [...]If someone as any idea... i'd love to ear about!

We probably should report this problem as a bug.

---

### Post by alxgomz on 2011-05-16
I sent a mail to the some people at broadcom:
[http://linuxwireless.org/en/users/Drivers/brcm80211#Developer_information](http://linuxwireless.org/en/users/Drivers/brcm80211#Developer_information)

---

### Post by RolandVossen on 2011-05-17
Hi guys,

are you running a 32 bit or a 64 bit OS ? Recently a stability issue was identified concerning 64 bit platforms.

Bye, 
Roland Vossen
Broadcom

---

### Post by alxgomz on 2011-05-17
that's a 32bit kernel in my case

uname -a
Linux elronde 2.6.32-5-686-bigmem #1 SMP Tue Mar 8 22:14:55 UTC 2011 i686 GNU/Linux

---

### Post by d-fens on 2011-05-17
> **RolandVossen said:**
> are you running a 32 bit or a 64 bit OS ? Recently a stability issue was identified concerning 64 bit platforms.

> **d-fens said:**
> ```

#uname -a
Linux minime 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
```

I'm running a 32bit kernel.

---

### Post by RolandVossen on 2011-05-26
Hi guys,

so the 64 bit fix will not work for your 32 bit system. Lets see if your firmware is current. Can you do the following for all files in the /lib/firmware/broadcom directory:

md5sum *

and reply with the results ?

Bye, Roland.

---

### Post by alxgomz on 2011-05-26
Hi,

I have found an option in the HP BIOS, called LAN/WAN switching.
Disabling this feature/crap solves the issue.

I can now plug my ethernet cable, even when already connected to wifi network
Can you check you have a similar option?

---

### Post by d-fens on 2011-06-01
> **RolandVossen said:**
> Lets see if your firmware is current. 


```
user@minime:/lib/firmware/brcm$ md5sum *
c53608f5818b702c46a012c57b4196ee  bcm4329-fullmac-4.bin
b308d5bab6b373c2f1a550ed09573f3a  bcm4329-fullmac-4.txt
96cf06e4ff9f0c04a0f26ebefdf32e3d  bcm43xx-0.fw
48882412db63b4e2dd9c26571a29a799  bcm43xx_hdr-0.fw

```> **alxgomz said:**
> I have found an option in the HP BIOS, called LAN/WAN switching.
[...]
Can you check you have a similar option?

I have this option too and it's enabled. But I think it is a nice feature for netbooks with not so much battery capacity. I will check if it works with this option disabled.

---

### Post by RolandVossen on 2011-06-01
> **d-fens said:**
> ```
user@minime:/lib/firmware/brcm$ md5sum *
c53608f5818b702c46a012c57b4196ee  bcm4329-fullmac-4.bin
b308d5bab6b373c2f1a550ed09573f3a  bcm4329-fullmac-4.txt
96cf06e4ff9f0c04a0f26ebefdf32e3d  bcm43xx-0.fw
48882412db63b4e2dd9c26571a29a799  bcm43xx_hdr-0.fw

``` That firmware is current, the md5 checksums correspond to version 0-610-811.

---

### Post by d-fens on 2011-06-01
I tried to disable the lan/wlan switching feature in the bios. But after that my NIC wasn't recognized by Ubuntu anymore. So I reinstalled Ubuntu 11.04 without formatting, so I don't loose any userdata, from a live usb-stick and now the netbook doesn't freeze anymore with the lan/wlan switching enabled. Also I don't get the traces in syslog anymore.

Thank you for your help

---

### Post by RolandVossen on 2011-10-20
A problem was recently found in the area of the RF kill switch, perhaps the problem reported here is related to it. Patch set is soon posted to the community, the title of the last patch in this set is 'brcm80211: smac: removed down-on-rf-kill functionality'.

---

