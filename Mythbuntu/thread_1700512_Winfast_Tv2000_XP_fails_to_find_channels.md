---
title: "Winfast Tv2000 XP fails to find channels"
date: 2011-03-05
forum: Mythbuntu
---

### Post by Fuzzyducky on 2011-03-05
Hi Guys,

Look I am seriously stressed out about this and becoming quite fixated about it that i feel i need help.
I have try to set up a HTPC for my folks using a old comp left for dead. I must admit this is my first attept and I have never used Linux before. 

Specs

P4 2.8Ghz
MSI 7005 MB
512 Ram
64mb Geforce4 Nivida MX 440
20 gb Seagate HD
80 gb Western digital HD
Winfast TV2000 XP RM Capture card


I have install Win 7 on the 80 gb and Mythbuntu 10.10 on the 20gb.  I have updated everything via auto updates on Mythbuntu install. 

My problem is when i try and set up the mythbackend it just never finds any channels. I believe my capture card is supported from all that I have researched and am still trying to figure out if it is configured correctly with "bttv"  ? The following is what I get related to my capture card. 

dmesg

[SIZE=1][   19.609795] IR RC5(x) protocol handler initialized
[   19.764165] Linux video capture interface: v2.00
[   19.990727] bttv: driver version 0.9.18 loaded
[   19.990732] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   19.991859] bttv: Bt8xx card found (0).
[   19.991888]   alloc irq_desc for 18 on node -1
[   19.991891]   alloc kstat_irqs on node -1
[   19.991902] bttv 0000:00:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.991919] bttv0: Bt878 (rev 17) at 0000:00:07.0, irq: 18, latency: 32, mmio: 0xe7004000
[   19.991960] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   19.991965] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   19.992051] bttv0: gpio: en=00000000, out=00000000 in=003ff182 [init]
[   19.993215] bttv0: tuner type=5
[   20.525254] IR RC6 protocol handler initialized
[   20.726518] type=1400 audit(1299320179.241:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=626 comm="apparmor_parser"
[   20.823908] Slow work thread pool: Starting up
[   20.823999] Slow work thread pool: Ready
[   20.824141] FS-Cache: Loaded
[   20.868842] cfg80211: World regulatory domain updated:
[   20.868849]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.868853]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.868857]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.868860]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.868864]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.868867]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[/SIZE][SIZE=1][   21.032636] IR JVC protocol handler initialized
[   21.472162] IR Sony protocol handler initialized
[   21.664794] lirc_dev: IR Remote Control driver registered, major 250 
[   21.666638] bttv0: audio absent, no audio device found!
[   21.959769] IR LIRC bridge handler initialized
[   22.003805] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   22.206802] FS-Cache: Netfs 'nfs' registered for caching
[   22.694604] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[   22.942631] usb 1-3: ath9k_htc: Transferred FW: ar9271.fw, size: 51280
[   23.141329] tuner-simple 1-0061: creating new instance
[   23.141337] tuner-simple 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   23.142322] bttv0: registered device video0
[   23.142419] bttv0: registered device vbi0
[   23.142620] bttv0: registered device radio0
[   23.142642] bttv0: PLL: 28636363 => 35468950 .. ok
[   23.784017] Registered IR keymap rc-winfast
[   23.784192] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:07.0/rc/rc0/input5
[   23.784297] rc0: bttv IR (card=34) as /devices/pci0000:00/0000:00:07.0/rc/rc0
[   23.784956] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[/SIZE]
I hope someone might have the solution to this as I have just poured a good couple of days into it and am just about to quit. 


Thanks in advance

Fuzzyducky

---

