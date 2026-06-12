---
title: "Please save my hair (WPA broken on wireless)"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by RonObvious on 2010-03-21
Ubuntu 9.10
HP Pavillion zv6000

I think my wireless interface itself is working but any network that needs authentication fails, meaning my network.  I can connect to unsecured networks all day except my own.  :frown:

I'm using NetworkManager and I have my passkey in correctly but stuff just fails.  If I try to connect via "Connect to Hidden Wireless Network" and type in my SSID, it sits for a few seconds then a dialog pops up saying "Authentication required by wireless" even though I already entered my passkey.  The dialog doesn't give you any options either either.  The Wireless security drop down is empty and therefore unselectable, so your only option is Cancel.

I've tried some things like this [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) but nothing.

I'm at my wits end, but I'll keep plugging away in the interim.  Thanks!

```
dmesg | grep -e ndis -e wlan
----------------------------
[   20.534368] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   20.721643] ndiswrapper: driver bcmwl5 (ASUS,03/22/2004, 3.60.7.0) loaded
[   20.721892] ndiswrapper 0000:03:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.727314] ndiswrapper: using IRQ 21
[   21.080662] wlan0: ethernet device 00:90:4b:ac:79:b4 using NDIS driver: bcmwl5, version: 0x33c0700, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   21.080691] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   21.109766] usbcore: registered new interface driver ndiswrapper
[   21.760954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.900342] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   36.900359] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[   37.411019] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.168019] wlan0: no IPv6 routers present
[   49.813758] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[   54.814569] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   54.814585] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[   56.882062] Modules linked in: binfmt_misc ppdev joydev iptable_filter ip_tables x_tables sdhci_pci sdhci led_class snd_atiixp tifm_7xx1 tifm_core snd_seq_dummy psmouse serio_raw k8temp i2c_piix4 snd_atiixp_modem snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc shpchp ndiswrapper lp parport radeon ttm drm i2c_algo_bit ohci1394 ieee1394 8139too 8139cp mii video output ati_agp agpgart
[   56.882149]  [<f811be7b>] NdisAllocateBuffer+0x3b/0x140 [ndiswrapper]
[   56.882172]  [<f811ec6d>] ? KeSynchronizeExecution+0x3d/0x70 [ndiswrapper]
[   56.882186]  [<f811b8d1>] ? NdisMSynchronizeWithInterrupt+0x21/0x30 [ndiswrapper]
[   56.882214]  [<f8121be8>] ? kdpc_worker+0xb8/0x120 [ndiswrapper]
[   56.882234]  [<f8121b30>] ? kdpc_worker+0x0/0x120 [ndiswrapper]

lshw -C network
---------------
  *-network:0
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:ac:79:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+ASUS,03/22/2004, 3.60.7.0 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:b0204000-b0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:6d:1b:06
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:a000(size=256) memory:b0209400-b02094ff

cat /etc/modprobe.d/blacklist
-----------------------------
blacklist bcm43xx
blacklist wl
blacklist b43

lspci -nn
---------
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 10)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 01)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 01)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
03:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
03:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
03:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
03:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
03:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

ndiswrapper -l
--------------
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)

```

---

### Post by bkratz on 2010-03-21
> **RonObvious said:**
> Ubuntu 9.10
HP Pavillion zv6000

I think my wireless interface itself is working but any network that needs authentication fails, meaning my network.  I can connect to unsecured networks all day except my own.  :frown:

I'm using NetworkManager and I have my passkey in correctly but stuff just fails.  If I try to connect via "Connect to Hidden Wireless Network" and type in my SSID, it sits for a few seconds then a dialog pops up saying "Authentication required by wireless" even though I already entered my passkey.  The dialog doesn't give you any options either either.  The Wireless security drop down is empty and therefore unselectable, so your only option is Cancel.

I've tried some things like this [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) but nothing.

I'm at my wits end, but I'll keep plugging away in the interim.  Thanks!

```
dmesg | grep -e ndis -e wlan
----------------------------
[   20.534368] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   20.721643] ndiswrapper: driver bcmwl5 (ASUS,03/22/2004, 3.60.7.0) loaded
[   20.721892] ndiswrapper 0000:03:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.727314] ndiswrapper: using IRQ 21
[   21.080662] wlan0: ethernet device 00:90:4b:ac:79:b4 using NDIS driver: bcmwl5, version: 0x33c0700, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   21.080691] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   21.109766] usbcore: registered new interface driver ndiswrapper
[   21.760954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.900342] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   36.900359] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[   37.411019] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.168019] wlan0: no IPv6 routers present
[   49.813758] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[   54.814569] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   54.814585] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)
[   56.882062] Modules linked in: binfmt_misc ppdev joydev iptable_filter ip_tables x_tables sdhci_pci sdhci led_class snd_atiixp tifm_7xx1 tifm_core snd_seq_dummy psmouse serio_raw k8temp i2c_piix4 snd_atiixp_modem snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc shpchp ndiswrapper lp parport radeon ttm drm i2c_algo_bit ohci1394 ieee1394 8139too 8139cp mii video output ati_agp agpgart
[   56.882149]  [<f811be7b>] NdisAllocateBuffer+0x3b/0x140 [ndiswrapper]
[   56.882172]  [<f811ec6d>] ? KeSynchronizeExecution+0x3d/0x70 [ndiswrapper]
[   56.882186]  [<f811b8d1>] ? NdisMSynchronizeWithInterrupt+0x21/0x30 [ndiswrapper]
[   56.882214]  [<f8121be8>] ? kdpc_worker+0xb8/0x120 [ndiswrapper]
[   56.882234]  [<f8121b30>] ? kdpc_worker+0x0/0x120 [ndiswrapper]

lshw -C network
---------------
  *-network:0
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:ac:79:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+ASUS,03/22/2004, 3.60.7.0 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:b0204000-b0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:6d:1b:06
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:a000(size=256) memory:b0209400-b02094ff

cat /etc/modprobe.d/blacklist
-----------------------------
blacklist bcm43xx
blacklist wl
blacklist b43

lspci -nn
---------
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 10)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 01)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 01)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
03:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
03:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
03:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
03:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
03:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

ndiswrapper -l
--------------
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)

```

See this thread for additional information

[http://ubuntuforums.org/showthread.php?t=1343847](http://ubuntuforums.org/showthread.php?t=1343847)

---

### Post by RonObvious on 2010-03-21
Yeah this looks like it's a non-starter.  Looks like no one who applied these patches and did the recompile got it to work.  I followed the steps anyway but no luck.  Weird thing is my wireless was working then an update came through then it was hosed.  Wish I could go back a la a Restore Point.

---

### Post by bkratz on 2010-03-21
> **RonObvious said:**
> Yeah this looks like it's a non-starter.  Looks like no one who applied these patches and did the recompile got it to work.  I followed the steps anyway but no luck.  Weird thing is my wireless was working then an update came through then it was hosed.  Wish I could go back a la a Restore Point.




Well the good news is that I have used the upcoming version 10.04 and it is all back to working.  I did get it to work with 9.10 eventually, but it required a different kernel and building my own ndiswrapper. If you can wait for the next release that is what I would do.  I would be happy to send you the details of how I did it but it was a long process, just PM me.

---

### Post by RonObvious on 2010-03-22
I built my own ndiswrapper from the referenced post but it didn't work.  I guess I need to include the other kernel, whatever that is.  Another kernel would mean it's not 9.10 from my point of view.

Some consolation is that samba worked straightaway to my Win7 machine with 0 headaches.  I couldn't say that about trying to get XP networked to that machine.

---

### Post by bkratz on 2010-03-22
> **RonObvious said:**
> I built my own ndiswrapper from the referenced post but it didn't work.  I guess I need to include the other kernel, whatever that is.  Another kernel would mean it's not 9.10 from my point of view.

Some consolation is that samba worked straightaway to my Win7 machine with 0 headaches.  I couldn't say that about trying to get XP networked to that machine.

You are right the kernel I used was  V2.6.32/9 dated February 24, 2010

The ndiswrapper was 1.56.

---

### Post by RonObvious on 2010-03-22
> **bkratz said:**
> You are right the kernel I used was  V2.6.32/9 dated February 24, 2010

The ndiswrapper was 1.56.

I guess when I built the ndiswrapper it became 1.56.  I used the sourceforge version which was 1.55.

1.  How do you find out what version of the kernel you're using (a uname option?)
2.  How do you get another version of the kernel and get it installed?

---

### Post by bkratz on 2010-03-22
> **RonObvious said:**
> I guess when I built the ndiswrapper it became 1.56.  I used the sourceforge version which was 1.55.

1.  How do you find out what version of the kernel you're using (a uname option?)
2.  How do you get another version of the kernel and get it installed?

No, I downloaded it as version 1.56--the latest stable version. I will PM you with the procedure I used.


oh, and it is 

uname -mr

---

