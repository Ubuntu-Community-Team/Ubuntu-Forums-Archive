---
title: "[SOLVED] Erratic Wi-Fi issue (setting essid failed)"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by BB2008 on 2009-01-06
Hi All:

I am using ubuntu for about 3 months now. I really like the OS, it has improved in functionality by leaps and bounds since I last laid my hands in a linux flavor back in 2005.

That said, I do have a strange issue - my wireless connection is erratic. About 50% of the time I boot the PC and it works fine. About 15% of the time, I will boot up and I will have no internet, but after waiting for anywhre between 5~30 minutes, internet will start working. And for about 35% of the time, I will have no internet and no amount of waiting will help, I will have to restart and hope it will pick up wireless.

When I do not have a connection - this is what I see in the syslog:

Jan  6 18:10:07 SomeName kernel: [ 9806.536731] ndiswrapper (set_essid:53): setting essid failed (C0000001)
Jan  6 18:10:17 SomeName kernel: [ 9816.544733] ndiswrapper (set_essid:53): setting essid failed (C0000001)
Jan  6 18:10:27 SomeName kernel: [ 9826.552745] ndiswrapper (set_essid:53): setting essid failed (C0000001)
Jan  6 18:10:37 SomeName kernel: [ 9836.560738] ndiswrapper (set_essid:53): setting essid failed (C0000001)
Jan  6 18:10:47 SomeName kernel: [ 9846.568739] ndiswrapper (set_essid:53): setting essid failed (C0000001)
Jan  6 18:10:57 SomeName kernel: [ 9856.576741] ndiswrapper (set_essid:53): setting essid failed (C0000001)
Jan  6 18:11:07 SomeName kernel: [ 9866.584742] ndiswrapper (set_essid:53): setting essid failed (C0000001)
Jan  6 18:11:17 SomeName kernel: [ 9876.592711] ndiswrapper (set_essid:53): setting essid failed (C0000001)

Can anyone help please? I am a decent techie guy, not deep into linux. Let me know if I need to post any further information.

Thanx!

---

### Post by pytheas22 on 2009-01-06
It looks like you're using ndiswrapper.  Depending on what kind of wireless card you have, you may be able to get a more stable connection by using native Linux drivers.  Could you please post the output of these commands:
```

lshw -C Network
lspci -nn
lsusb
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

If ndiswrapper is really the only way to make your card work on Ubuntu, we can try to troubleshoot it.  But in general, since ndiswrapper depends on closed-source Windows drivers, it's harder to fix than native drivers.

---

### Post by BB2008 on 2009-01-06
pytheas22, thanks for the quick response, it is truly appreciated!

Yes, you are right, I am using ndiswrapper as at the time of installation, there was no native linux driver available for my card. It is a trendnet TEW-423PI PCI card.

Below are the results of all the commands you asked for. **The connection is working currently**, so if you were expecting to see any errors, you might not.

```
lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:5a:0b:e1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 03
       serial: 00:40:f4:d5:3e:85
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8000c driverversion=1.53+Marvell,09/17/2004,3.1.0.19 ip=192.168.1.100 latency=32 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:e7:59:49:1d:f7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```
lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) [1022:9609]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
03:07.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
03:0e.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
```

```
lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
dmesg | grep -e ndis -e wlan
[   14.194359] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.317330] ndiswrapper: driver mrv8000c (Marvell,09/17/2004,3.1.0.19) loaded
[   14.317525] ndiswrapper 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.317896] ndiswrapper: using IRQ 21
[   14.576330] wlan0: ethernet device 00:40:f4:d5:3e:85 using NDIS driver: mrv8000c, version: 0x3000027, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[   14.576341] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[   14.576346] wlan0: encryption modes supported: WEP; TKIP with WPA
[   14.576575] usbcore: registered new interface driver ndiswrapper
[   55.268517] wlan0: no IPv6 routers present
```

```

ndiswrapper -l
mrv8000c : driver installed
	device (11AB:1FAA) present
```

---

### Post by pytheas22 on 2009-01-06
Thanks for that information.

Your card has a libertas chipset.  There is a native Linux driver for these chips, although I get the sense from Google that it probably doesn't yet support your particular card (according to [kernel.org]("http://wireless.kernel.org/en/users/Drivers/libertas"), only the 88W8385 and 88W8386 models are supported, but lshw reports your chip as 88w8335).  However, giving it a try is simple enough, so let's unload ndiswrapper by typing:
```

sudo modprobe -r ndiswrapper
```

then load the libertas driver:
```

sudo modprobe libertas
```

If neither of these commands gives an error, wait a few seconds, then type:
```

iwconfig
```

Does it list any wireless interfaces?  If so, can you connect to your network?  If this works, we can make libertas drive the card permanently.

If this doesn't work and you want ndiswrapper back, either reboot your computer, or type:
```

sudo modprobe -r libertas
sudo modprobe ndiswrapper
```

---

If the native driver won't work, then the only option is to try to deal with ndiswrapper.  In that case, I'd recommend first that you try using different Windows drivers.  A lot of ndiswrapper instability comes down to flaky Windows drivers, and loading a different version of the Windows driver often solves the problem.  You can uninstall your current drivers by typing:
```

sudo ndiswrapper -r mrv8000c
```

Then install the drivers from [this page]("http://drop.io/88w8335").  On [this site]("http://www.linuxquestions.org/questions/linux-hardware-18/88w8335-libertas-ndiswrapper-or-native-in-2008-652879/"), someone mentions using those Windows drivers for the 88w8335 chip with no problem.

If new Windows drivers don't seem to make a difference, it may help to compile ndiswrapper from source.  For instructions on that, see step #7 of this [ndiswrapper-troubleshooting page]("http://ubuntuforums.org/showthread.php?t=885847") that I wrote a while ago.  Note that if you're on Ubuntu 8.10, you need to apply a patch to compile ndiswrapper, as explained in that thread.

If none of the above helps, we can try some other things, but for now please just let me know how these suggestions work.

---

### Post by BB2008 on 2009-01-07
Thanx pytheas22. I was thinking of trying the libertas native driver, but chickened out because this machine is not near a wired point and i did not want to risk losing total connectivity. So sorry, did not try that!

I tried out the second option you suggested - th alternative driver for windows for my wireless chipset, and that seems to be working ok so far, but it has only been one reboot. So I will keep my fingers crossed and will report back in a week if I am still troublefree at that point...or earlier if not :-(.

I appreciate your help and quick responses, you are very knowledgeable in these matters, and it is rare to find folks who are willing to share their knowledge, except in this open source world...GO FOSS GO!

I do have some other networking issues, but not related to NDISWRAPPER (at least not on the surface), so I will not pollute this thread with that issue and will open a new thread.

---

### Post by BB2008 on 2009-01-09
:D :D :D :D :D :D :D
Yes, I can say that this solution works as I have rebooted at a dozen times since the above changes and not a single instance of any waiting for the connection.

Thanx!

---

### Post by 73ckn797 on 2009-01-19
> **pytheas22 said:**
> Thanks for that information.

Your card has a libertas chipset.  There is a native Linux driver for these chips, although I get the sense from Google that it probably doesn't yet support your particular card (according to [kernel.org]("http://wireless.kernel.org/en/users/Drivers/libertas"), only the 88W8385 and 88W8386 models are supported, but lshw reports your chip as 88w8335).  However, giving it a try is simple enough, so let's unload ndiswrapper by typing:
```

sudo modprobe -r ndiswrapper
```then load the libertas driver:
```

sudo modprobe libertas
```If neither of these commands gives an error, wait a few seconds, then type:
```

iwconfig
```Does it list any wireless interfaces?  If so, can you connect to your network?  If this works, we can make libertas drive the card permanently.

If this doesn't work and you want ndiswrapper back, either reboot your computer, or type:
```

sudo modprobe -r libertas
sudo modprobe ndiswrapper
```---

If the native driver won't work, then the only option is to try to deal with ndiswrapper.  In that case, I'd recommend first that you try using different Windows drivers.  A lot of ndiswrapper instability comes down to flaky Windows drivers, and loading a different version of the Windows driver often solves the problem.  You can uninstall your current drivers by typing:
```

sudo ndiswrapper -r mrv8000c
```Then install the drivers from [this page]("http://drop.io/88w8335").  On [this site]("http://www.linuxquestions.org/questions/linux-hardware-18/88w8335-libertas-ndiswrapper-or-native-in-2008-652879/"), someone mentions using those Windows drivers for the 88w8335 chip with no problem.

If new Windows drivers don't seem to make a difference, it may help to compile ndiswrapper from source.  For instructions on that, see step #7 of this [ndiswrapper-troubleshooting page]("http://ubuntuforums.org/showthread.php?t=885847") that I wrote a while ago.  Note that if you're on Ubuntu 8.10, you need to apply a patch to compile ndiswrapper, as explained in that thread.

If none of the above helps, we can try some other things, but for now please just let me know how these suggestions work.

I have the same wireless card on an 8.10 install. It works but shows a weak (one bar) signal. It is only 10 feet from the router. The funny thing is that it does not seem to be slow just appears weak. I will look into this following your tips here.

---

### Post by pytheas22 on 2009-01-19
> I have the same wireless card on an 8.10 install. It works but shows a weak (one bar) signal. It is only 10 feet from the router. The funny thing is that it does not seem to be slow just appears weak. I will look into this following your tips here.

Are you using ndiswrapper with it or did you somehow get the native driver to work?  If you're using the native driver, try ndiswrapper.  If you're using ndiswrapper, try using the Windows drivers that I link to above, since it apparently works well.

---

### Post by 73ckn797 on 2009-01-19
> **pytheas22 said:**
> Are you using ndiswrapper with it or did you somehow get the native driver to work?  If you're using the native driver, try ndiswrapper.  If you're using ndiswrapper, try using the Windows drivers that I link to above, since it apparently works well.


I will look into that but for now it is working and does not seem to be slow. I am on cable modem. Actually the neighbors system shows a stronger signal than mine so I do not know what is going on there. Maybe I ought to connect to his?

---

### Post by pytheas22 on 2009-01-20
> 
I will look into that but for now it is working and does not seem to be slow. I am on cable modem. Actually the neighbors system shows a stronger signal than mine so I do not know what is going on there. Maybe I ought to connect to his?

It could just be that your neighbor has a stronger router than yours, or that because of the way things are positioned, his comes in stronger in the particular area where your Ubuntu computer is.  On the other hand, maybe your router is having issues.  Do any other wirelessly connected computers on your network have trouble, or is it just Ubuntu?

---

### Post by murlig on 2009-01-21
Hi BB2008,

I'm exactly having the same erratic problem with ndiswrapper for mrv8335. 

I've tried multiple suggestions from pytheas22 and am at point where i might go back to 8.04.1 if the erratic behaviour continues.

extremely disasspointed with 8.10 with this aspect. To be more accurate, there is some sort of a conflict between 2.6.27.9 kernel and ndiswrapper.

---

### Post by pytheas22 on 2009-01-21
> Hi BB2008,

I'm exactly having the same erratic problem with ndiswrapper for mrv8335.

I've tried multiple suggestions from pytheas22 and am at point where i might go back to 8.04.1 if the erratic behaviour continues.

extremely disasspointed with 8.10 with this aspect. To be more accurate, there is some sort of a conflict between 2.6.27.9 kernel and ndiswrapper.

I'd forgotten that you also had this card, murlig.  I wonder if you'd have better luck using the Windows driver from [here]("http://drop.io/88w8335").  It seems to have solved the problem for the original poster in this thread.

---

### Post by murlig on 2009-01-21
Hi Pytheas22,

I downloaded and diff'ed the drivers and they are mostly identical. 

The version matches in the inf files and only thing different is a text that shows the card manufacturer.(E-home in my case).

The *.sys files are identical

thanks for your help again.

---

### Post by pytheas22 on 2009-01-21
> Hi Pytheas22,

I downloaded and diff'ed the drivers and they are mostly identical.

The version matches in the inf files and only thing different is a text that shows the card manufacturer.(E-home in my case).

The *.sys files are identical

thanks for your help again. 

Sorry to hear that didn't help.  I suspect that the heart of your problem is not actually the same as that of the original poster's, since his or her dmesg mentions 'setting essid failed' several times, but I haven't seen that in any of the information that you've posted.

Unfortunately, I still don't have any suggestions for you beyond what we've already tried, but I'll keep thinking on it...

---

### Post by 73ckn797 on 2009-02-01
> **pytheas22 said:**
> It could just be that your neighbor has a stronger router than yours, or that because of the way things are positioned, his comes in stronger in the particular area where your Ubuntu computer is.  On the other hand, maybe your router is having issues.  Do any other wirelessly connected computers on your network have trouble, or is it just Ubuntu?


The problem is only in Ubuntu. 2 other computers connected wireless have strong signals and are further away from the router.

I have connected a CAT 5 cable and do not have to deal with the issue for now.

---

