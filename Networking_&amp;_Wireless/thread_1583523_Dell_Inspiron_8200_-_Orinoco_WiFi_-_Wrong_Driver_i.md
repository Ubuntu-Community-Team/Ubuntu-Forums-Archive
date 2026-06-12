---
title: "Dell Inspiron 8200 - Orinoco WiFi - Wrong Driver in Kernel ????"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by QTip on 2010-09-28
Lost post twice .......... Now the extra short version ...........

Have a Dell Inspiron 8200 Notebook with minipci wifi True Mobile (orinoco v.15).  Work fine w/ XP.  With Ubuntu the kernel loads the orinoco_cs driver, I can see my routers, but will not connect to any of them (even when unsecured no WEP, etc).  After looking on line it appeared that the driver should have been orinoco_pci instead of orinoco_cs.  Is that true ??  Was able to BlackList the Orinoco_cs driver but could not determine how to load the Orinoco_pci driver to test it.

Can anyone help a newby to Linux ?? 

Here are the commands that I ran:

[SIZE=4]lshw -C network[/SIZE]
*-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:84:71:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b

[SIZE=4]lspci -nn[/SIZE]
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 440 Go] [10de:0174] (rev a3)
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4451 IEEE-1394 Controller [104c:8027]
02:03.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)

[SIZE=4]PCCARDCTL IDENT[/SIZE]
Socket 0:
  no product info available
Socket 1:
  no product info available
Socket 2:
  product info: "Dell", "TrueMobile 1150 Series PC Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

[SIZE=4]ifconfig[/SIZE]
eth0      Link encap:Ethernet  HWaddr 00:08:74:06:b6:c1  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe06:b6c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10024 (10.0 KB)  TX bytes:9898 (9.8 KB)
          Interrupt:11 Base address:0xcc00 

eth1      Link encap:Ethernet  HWaddr 00:02:2d:84:71:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xe100 

[SIZE=4]DMESG[/SIZE]
[   19.512138] pcmcia_socket pcmcia_socket2: pccard: PCMCIA card inserted into slot 2
[   19.731879] ppdev: user-space parallel port driver
[   19.768098] pcmcia_socket pcmcia_socket2: cs: memory probe 0xf4000000-0xfbffffff: excluding 0xf4000000-0xf8ffffff
[   19.775741] pcmcia 2.0: pcmcia: registering new device pcmcia2.0
[   19.781781] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   19.783045] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   19.783618] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   19.783706] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   19.788944] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   19.826720] cfg80211: Calling CRDA to update world regulatory domain
[   19.850858] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.857249] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.936914] orinoco_cs 2.0: Hardware identity 0005:0002:0001:0002
[   19.937023] orinoco_cs 2.0: Station identity  001f:0001:0006:000e
[   19.937029] orinoco_cs 2.0: Firmware determined as Lucent/Agere 6.14
[   19.940102] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1)
[   19.940112] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 2)
[   19.962093] cfg80211: World regulatory domain updated:
[   19.962101]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.962107]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.962112]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.962118]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.962123]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.962128]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.969602] orinoco_cs 2.0: firmware: requesting agere_sta_fw.bin
[   19.992090] intel8x0_measure_ac97_clock: measured 54331 usecs (2612 samples)
[   19.992098] intel8x0: clocking to 48000
[   20.139661] orinoco_cs 2.0: Hardware identity 0005:0002:0001:0002
[   20.139785] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[   20.139792] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[   20.139796] orinoco_cs 2.0: Ad-hoc demo mode supported
[   20.139800] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[   20.139805] orinoco_cs 2.0: WEP supported, 104-bit key
[   20.139808] orinoco_cs 2.0: WPA-PSK supported
[   20.160468] [drm] nouveau 0000:01:00.0: allocated 1400x1050 fb: 0x49000, bo ee343200
[   20.160648] fb0: nouveaufb frame buffer device
[   20.160653] registered panic notifier
[   20.160665] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[   20.178870] vga16fb: initializing
[   20.178882] vga16fb: mapped to 0xc00a0000
[   20.178890] vga16fb: not registering due to another framebuffer present
[   20.297035] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 1 using output A
[   20.297043] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[   20.297049] [drm] nouveau 0000:01:00.0: 0xD780: Parsing digital output script table
[   20.376124] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 0)
[   20.376132] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[   20.376138] [drm] nouveau 0000:01:00.0: 0xD662: Parsing digital output script table
[   20.473334] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   20.600110] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 1 using output A
[   20.605646] Console: switching to colour frame buffer device 175x65
[   21.676084] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   21.677368] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   29.752083] eth0: no IPv6 routers present
[   46.712320] eth1: Lucent/Agere firmware doesn't support manual roaming
[   51.855796] eth1: Lucent/Agere firmware doesn't support manual roaming
[   57.034812] eth1: Lucent/Agere firmware doesn't support manual roaming
[   62.181477] eth1: Lucent/Agere firmware doesn't support manual roaming
[   67.337056] eth1: Lucent/Agere firmware doesn't support manual roaming
[   72.541110] eth1: Lucent/Agere firmware doesn't support manual roaming
[   77.692208] eth1: Lucent/Agere firmware doesn't support manual roaming
[   82.844084] eth1: Lucent/Agere firmware doesn't support manual roaming
[   87.988959] eth1: Lucent/Agere firmware doesn't support manual roaming
[   93.147356] eth1: Lucent/Agere firmware doesn't support manual roaming
[   98.303124] eth1: Lucent/Agere firmware doesn't support manual roaming
[  103.462322] eth1: Lucent/Agere firmware doesn't support manual roaming

---

### Post by QTip on 2010-09-28
Any advice ???

---

### Post by QTip on 2010-09-28
No one else had this problem??

Should I use orinoco_cs or orinoco_pci ???

If orinoco_pci how do I load the driver ??

---

### Post by astrobob.tk on 2010-09-28
did you try 1st System > Administration > Hardware Drivers ?

if not check it (requires root) & check of the drivers are enabled & activated. Also check the description of the driver to make sure its the one for ur card.

anyways, I am not of great help in this particular situation but I think you might find a solution [here]("http://ubuntuforums.org/showthread.php?t=304217&highlight=Lucent+IEEE").

---

### Post by QTip on 2010-09-28
Thanks for the Reply

did you try 1st System > Administration > Hardware Drivers ?  YES JUST FOUND A PROBLEM WITH THE NVIDIA DRIVER 

if not check it (requires root) & check of the drivers are enabled  & activated. Also check the description of the driver to make sure  its the one for ur card.  NOT SURE WHAT YOU MEAN, DO WHAT IN THE ROOT FOLDER AND HOW TO CHECK IF DRIVERS ARE ENABLED OR ACTIVATED.

anyways, I am not of great help in this particular situation but I think you might find a solution [here]("http://ubuntuforums.org/showthread.php?t=304217&highlight=Lucent+IEEE"). 	
LOOKED AT POST DID NOT SEEM TO HELP

THANKS AGAIN
QTIP

---

