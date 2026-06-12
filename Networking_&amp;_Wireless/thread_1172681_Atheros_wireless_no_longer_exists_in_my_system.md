---
title: "Atheros wireless no longer exists in my system"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by urban_ryoga on 2009-05-28
Hi. I'm currently running 9.04 and after doing a soft reset from using python code that froze my UI, I found that my wireless is no longer enabled or works.

The following is the read out from sudo ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:17:42:92:84:4b  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:42ff:fe92:844b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1191457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:677053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1425592571 (1.4 GB)  TX bytes:62979711 (62.9 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:125852 (125.8 KB)  TX bytes:125852 (125.8 KB)

```

The following is the printout from iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

I've tried sudo modprobe ath5k in an attempt to reload the ati drivers, but nothing happens. Can someone help me out?

---

### Post by pytheas22 on 2009-05-28
Please reboot your machine, then run the following commands and post output (some commands may have no output):
```

lsmod | grep ath
sudo modprobe ath5k
sudo modprobe ath_pci
dmesg | grep -e ath -e wlan
lshw -C Network
lspci -nn | grep -i atheros
```

That will help us figure out what's wrong.

---

### Post by urban_ryoga on 2009-05-28
lsmod | grep ath
```
ath5k                 107008  0 
mac80211              217208  1 ath5k
led_class              12036  1 ath5k
cfg80211               38032  2 ath5k,mac80211

```

sudo modprobe ath5k
no output

sudo modprobe ath_pci
no output

dmesg | grep -e ath -e wlan
```
[    2.617613] device-mapper: multipath: version 1.0.5 loaded
[    2.617616] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.424050] ath5k_pci 0000:09:00.0: enabling device (0000 -> 0002)
[   12.424062] ath5k_pci 0000:09:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   12.424153] ath5k_pci 0000:09:00.0: registered as 'phy0'
[   12.557846] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   12.562562] udev: renamed network interface wlan0 to wlan1
[   22.156505] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   24.032417] wlan1: authenticate with AP 00:12:17:34:90:09
[   24.033965] wlan1: authenticated
[   24.033968] wlan1: associate with AP 00:12:17:34:90:09
[   24.036004] wlan1: RX AssocResp from 00:12:17:34:90:09 (capab=0x401 status=0 aid=27)
[   24.036018] wlan1: associated
[   24.036338] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   24.036814] wlan1: disassociating by local choice (reason=3)
[   34.113028] wlan1: no IPv6 routers present
[   40.074311] ath5k_pci 0000:09:00.0: PCI INT A disabled
[  271.280203] ath_hal: module license 'Proprietary' taints kernel.
[  271.284026] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  271.315937] wlan: 0.9.4
[  271.334663] ath_pci: 0.9.4

```

lshw -C Network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:92:84:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:b9:8f:4c:a6:f7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

lspci -nn | grep -i atheros
no output

---

### Post by pytheas22 on 2009-05-28
There's something strange going on.  According to your 'dmesg' output, the system detected and brought up your wireless card as 'wlan1' and apparently even tried unsuccessfully to connect to your router.  But then it looks like the wireless interface disappeared for reasons that are unclear.  It's weird that 'lspci -nn | grep atheros' returns nothing and that 'lshw -C Network' doesn't list a wireless device.

I'm not sure what's wrong, but could you please post the entire output of:
```

lspci -nn
```

Also, blacklist the ath_pci module by typing:
```

echo blacklist ath_pci | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by urban_ryoga on 2009-05-28
lspci -nn
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
06:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 12)
08:08.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller [1217:7136] (rev 01)
08:08.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
08:08.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
08:08.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)

```

I blacklisted ath_pci as requested.

---

### Post by argosreality on 2009-05-28
Im actually seeing the same issue. As of Sunday my wireless worked fine, come last night when I tried to use my Acer one my Atheros wireless card is gone. I've checked the switch, nothing. My hardware doesnt even appear when checking dmesg or any of the other commands you asked for either. Did Ubuntu push a kernel update this past weekend?

---

### Post by pytheas22 on 2009-05-28
Very strange; there's no wireless hardware listed at all in your 'lspci -nn' output, urban_ryoga.  Ubuntu should at least see that the hardware exists, even if the driver can't bring it up for some reason.

You're positive you didn't disable the card in BIOS, correct?  And if there are any buttons or software switches (like function+F2) on your computer for disabling the wireless, you've tried toggling them, to no effect?

argosreality: it's very interesting that you report similar behavior.  I don't know if there was a kernel update over the weekend, but I'm also not sure why a kernel update would cause this problem.

Are you both using Ubuntu 9.04?

---

### Post by urban_ryoga on 2009-05-28
I have a physical switch to enable/disable wifi. Toggling it doesn't seem to do anything. I am running 9.04, but I've done no updates leading up to when this issue occurred.

---

### Post by pytheas22 on 2009-05-28
> I have a physical switch to enable/disable wifi. Toggling it doesn't seem to do anything. I am running 9.04, but I've done no updates leading up to when this issue occurred.

If this system is a dual-boot, does the card still work in Windows?  If you boot to the Ubuntu live CD, does it work there?

---

### Post by t0mppa on 2009-05-29
There was another thread with a problem similar to this one. The poster didn't get any sign of wireless on lspci or lshw at first, but once he unloaded the drivers that were running it, it showed back on lshw as unclaimed.

So, since your dmesg earlier said that first ath5k was loaded up, but then killed off and ath_pci loaded up instead, try doing a 'sudo modprobe -r ath_pci' and see if that helps.

---

### Post by urban_ryoga on 2009-05-31
Umm... wow. I tried using the wireless on a live cd and on windows 7 and it didn't seem to exist on either. I just got a wifi adapter from a friend to use in the expansion port. I used it for a day and today when I turned on my computer, my internal wi-fi adapter started to work.

lshw -C Network output
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:92:84:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:99:5c:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.64 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:70:e4:be:74:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

I'm glad it is working now, but really confused as to how it decided to work on its own.

---

### Post by DVANDERM on 2009-05-31
> **urban_ryoga said:**
> Umm... wow. I tried using the wireless on a live cd and on windows 7 and it didn't seem to exist on either. I just got a wifi adapter from a friend to use in the expansion port. I used it for a day and today when I turned on my computer, my internal wi-fi adapter started to work.

lshw -C Network output
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:92:84:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:99:5c:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.64 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:70:e4:be:74:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

I'm glad it is working now, but really confused as to how it decided to work on its own.

My card is the exact same thing. It worked, then didn't work, started working again, and now it doesn't work again. I hope yours is fixed because I've been trying everything I can to get this straighted out.

---

### Post by pytheas22 on 2009-05-31
If multiple people are having problems with this, someone should probably file a bug report on Launchpad (I don't have this hardware myself or I would).  I googled and couldn't find any other bug reports of the same problem (although there are some scattered forum posts that look like the same issue).

That said, urban_ryoga's mention that the wireless card also seemed to disappear under Windows 7 makes me think that this may simply be a hardware issue, not something Ubuntu can fix.

---

