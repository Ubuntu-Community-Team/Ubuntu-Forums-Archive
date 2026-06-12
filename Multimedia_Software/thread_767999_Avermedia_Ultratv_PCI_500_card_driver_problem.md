---
title: "Avermedia Ultratv PCI 500 card driver problem"
date: 2008-04-26
forum: Multimedia Software
---

### Post by michalski64 on 2008-04-26
Hey everyone. I'm not entirely new to linux but I'm building up my knowledge as I go. I've been using Ubuntu Gutsy for a while now and love it. I'd make the total switch from a dual boot if it wasn't for my tv-card.

I have an Avermedia Ultratv PCI 500 card, which is supported by the cx88 driver as card # 32. (Actually card 32 is for the PCI 550, but I've read that it doesn't really matter since both are the same).

I've followed commands like modprobe cx88_dvb as suggested by others but that has no effect.

Now I've tried xawtv -remote and I get a black screen with 4 composites available. The first 3 have nothing but the 4th has static. However no tv, nothing. 

I've tried VLC but it crashes.

TvTime also crashes without a single whisper.

I don't like MythTV simply because I want a small window for tv while I do whatever else on the my computer. Also, I doubt it would matter either which prog I use to watch tv with, since this looks like a driver issue to me.

This is the result of doing xawtv -hwscan

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l
    name : Qtec Webcam 100
    flags:  capture  

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : UNKNOWN/GENERIC
    flags:  capture  

This is the contracted dmesg result:

[ 8073.605861] [fglrx] enable ID = 0x00000009
[ 8073.605870] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[ 8499.818468] bttv: driver version 0.9.17 loaded
[ 8499.818480] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 9187.958393] cx88[0]: video y / packed - dma channel status dump
[ 9187.958404] cx88[0]:   cmds: initial risc: 0x27228000
[ 9187.958408] cx88[0]:   cmds: cdt base    : 0x00180440
[ 9187.958413] cx88[0]:   cmds: cdt size    : 0x0000000c
[ 9187.958417] cx88[0]:   cmds: iq base     : 0x00180400
[ 9187.958422] cx88[0]:   cmds: iq size     : 0x00000010
[ 9187.958426] cx88[0]:   cmds: risc pc     : 0x27942034
[ 9187.958431] cx88[0]:   cmds: iq wr ptr   : 0x00000103
[ 9187.958435] cx88[0]:   cmds: iq rd ptr   : 0x00000107
[ 9187.958439] cx88[0]:   cmds: cdt current : 0x00000488
[ 9187.958444] cx88[0]:   cmds: pci target  : 0x27940000
[ 9187.958448] cx88[0]:   cmds: line / byte : 0x03200000
[ 9187.958453] cx88[0]:   risc0: 0x80008200 [ sync resync count=512 ]
[ 9187.958461] cx88[0]:   risc1: 0x1c000480 [ write sol eol count=1152 ]
[ 9187.958469] cx88[0]:   risc2: 0x27926000 [ skip eol irq2 irq1 23 20 cnt1 14 13 count=0 ]
[ 9187.958483] cx88[0]:   risc3: 0x1c000480 [ write sol eol count=1152 ]
[ 9187.958491] cx88[0]:   iq 0: 0x2793e000 [ skip eol irq2 irq1 23 20 cnt1 cnt0 resync 14 13 count=0 ]
[ 9187.958507] cx88[0]:   iq 1: 0x1c000480 [ write sol eol count=1152 ]
[ 9187.958516] cx88[0]:   iq 2: 0x2793e200 [ arg #1 ]
[ 9187.958520] cx88[0]:   iq 3: 0x1c000480 [ write sol eol count=1152 ]
[ 9187.958529] cx88[0]:   iq 4: 0x2793fb80 [ arg #1 ]
[ 9187.958533] cx88[0]:   iq 5: 0x71010000 [ jump irq1 cnt0 count=0 ]
[ 9187.958542] cx88[0]:   iq 6: 0x80008200 [ arg #1 ]
[ 9187.958546] cx88[0]:   iq 7: 0x1c000480 [ write sol eol count=1152 ]
[ 9187.958555] cx88[0]:   iq 8: 0x27926000 [ arg #1 ]
[ 9187.958559] cx88[0]:   iq 9: 0x1c000480 [ write sol eol count=1152 ]
[ 9187.958568] cx88[0]:   iq a: 0x27926480 [ arg #1 ]
[ 9187.958572] cx88[0]:   iq b: 0x1c000480 [ write sol eol count=1152 ]
[ 9187.958581] cx88[0]:   iq c: 0x27926900 [ arg #1 ]
[ 9187.958585] cx88[0]:   iq d: 0x18000280 [ write sol count=640 ]
[ 9187.958593] cx88[0]:   iq e: 0x27926d80 [ arg #1 ]
[ 9187.958597] cx88[0]:   iq f: 0x14000200 [ write eol count=512 ]
[ 9187.958605] cx88[0]:   iq 10: 0x00180c00 [ arg #1 ]
[ 9187.958609] cx88[0]: fifo: 0x00180c00 -> 0x183400
[ 9187.958612] cx88[0]: ctrl: 0x00180400 -> 0x180460
[ 9187.958616] cx88[0]:   ptr1_reg: 0x001813b8
[ 9187.958620] cx88[0]:   ptr2_reg: 0x00180458
[ 9187.958624] cx88[0]:   cnt1_reg: 0x0000007d
[ 9187.958628] cx88[0]:   cnt2_reg: 0x00000000
[ 9187.958637] cx88[0]/0: [eb47c240/1] timeout - dma=0x27942000
[ 9187.958642] cx88[0]/0: [eb47cf00/0] timeout - dma=0x27228000
[ 9193.017702] cx88[0]: video y / packed - dma channel status dump
[ 9193.017711] cx88[0]:   cmds: initial risc: 0x27140000
[ 9193.017714] cx88[0]:   cmds: cdt base    : 0x00180440
[ 9193.017718] cx88[0]:   cmds: cdt size    : 0x0000000c
[ 9193.017721] cx88[0]:   cmds: iq base     : 0x00180400
[ 9193.017725] cx88[0]:   cmds: iq size     : 0x00000010
[ 9193.017728] cx88[0]:   cmds: risc pc     : 0x2722f034
[ 9193.017731] cx88[0]:   cmds: iq wr ptr   : 0x0000010f
[ 9193.017734] cx88[0]:   cmds: iq rd ptr   : 0x00000103
[ 9193.017738] cx88[0]:   cmds: cdt current : 0x00000468
[ 9193.017741] cx88[0]:   cmds: pci target  : 0x27142000
[ 9193.017745] cx88[0]:   cmds: line / byte : 0x03200000
[ 9193.017748] cx88[0]:   risc0: 0x80008200 [ sync resync count=512 ]
[ 9193.017754] cx88[0]:   risc1: 0x1c000480 [ write sol eol count=1152 ]
[ 9193.017761] cx88[0]:   risc2: 0x27953000 [ skip eol irq2 irq1 23 20 18 cnt0 13 12 count=0 ]
[ 9193.017773] cx88[0]:   risc3: 0x1c000480 [ write sol eol count=1152 ]
[ 9193.017779] cx88[0]:   iq 0: 0x27141b80 [ skip eol irq2 irq1 20 18 12 count=2944 ]
[ 9193.017789] cx88[0]:   iq 1: 0x71010000 [ jump irq1 cnt0 count=0 ]
[ 9193.017796] cx88[0]:   iq 2: 0x80008200 [ arg #1 ]
[ 9193.017799] cx88[0]:   iq 3: 0x1c000480 [ write sol eol count=1152 ]
[ 9193.017806] cx88[0]:   iq 4: 0x27953000 [ arg #1 ]
[ 9193.017809] cx88[0]:   iq 5: 0x1c000480 [ write sol eol count=1152 ]
[ 9193.017816] cx88[0]:   iq 6: 0x27953480 [ arg #1 ]
[ 9193.017819] cx88[0]:   iq 7: 0x1c000480 [ write sol eol count=1152 ]
[ 9193.017826] cx88[0]:   iq 8: 0x27953900 [ arg #1 ]
[ 9193.017829] cx88[0]:   iq 9: 0x18000280 [ write sol count=640 ]
[ 9193.017835] cx88[0]:   iq a: 0x27953d80 [ arg #1 ]
[ 9193.017838] cx88[0]:   iq b: 0x14000200 [ write eol count=512 ]
[ 9193.017844] cx88[0]:   iq c: 0x27952000 [ arg #1 ]
[ 9193.017847] cx88[0]:   iq d: 0x1c000480 [ write sol eol count=1152 ]
[ 9193.017854] cx88[0]:   iq e: 0x27952200 [ arg #1 ]
[ 9193.017857] cx88[0]:   iq f: 0x1c000480 [ write sol eol count=1152 ]
[ 9193.017864] cx88[0]:   iq 10: 0x00180c00 [ arg #1 ]
[ 9193.017867] cx88[0]: fifo: 0x00180c00 -> 0x183400
[ 9193.017869] cx88[0]: ctrl: 0x00180400 -> 0x180460
[ 9193.017872] cx88[0]:   ptr1_reg: 0x00182178
[ 9193.017875] cx88[0]:   ptr2_reg: 0x00180488
[ 9193.017878] cx88[0]:   cnt1_reg: 0x0000007f
[ 9193.017881] cx88[0]:   cnt2_reg: 0x00000000
[ 9193.017888] cx88[0]/0: [f2beb840/1] timeout - dma=0x2722f000
[ 9193.017891] cx88[0]/0: [f2beb600/0] timeout - dma=0x27140000
[ 9198.967487] cx88[0]: video y / packed - dma channel status dump
[ 9198.967496] cx88[0]:   cmds: initial risc: 0x29f4a000
[ 9198.967499] cx88[0]:   cmds: cdt base    : 0x00180440
[ 9198.967503] cx88[0]:   cmds: cdt size    : 0x0000000c
[ 9198.967506] cx88[0]:   cmds: iq base     : 0x00180400
[ 9198.967510] cx88[0]:   cmds: iq size     : 0x00000010
[ 9198.967513] cx88[0]:   cmds: risc pc     : 0x29f4a034
[ 9198.967516] cx88[0]:   cmds: iq wr ptr   : 0x00000101
[ 9198.967520] cx88[0]:   cmds: iq rd ptr   : 0x00000105
[ 9198.967523] cx88[0]:   cmds: cdt current : 0x00000498
[ 9198.967526] cx88[0]:   cmds: pci target  : 0x29255000
[ 9198.967530] cx88[0]:   cmds: line / byte : 0x02900000
[ 9198.967533] cx88[0]:   risc0: 0x80008000 [ sync resync count=0 ]
[ 9198.967539] cx88[0]:   risc1: 0x1c000480 [ write sol eol count=1152 ]
[ 9198.967546] cx88[0]:   risc2: 0x29459000 [ skip sol irq1 22 18 cnt0 resync 12 count=0 ]
[ 9198.967556] cx88[0]:   risc3: 0x1c000480 [ write sol eol count=1152 ]
[ 9198.967563] cx88[0]:   iq 0: 0x2945bd00 [ skip sol irq1 22 18 cnt0 resync 13 12 count=3328 ]
[ 9198.967574] cx88[0]:   iq 1: 0x1c000480 [ write sol eol count=1152 ]
[ 9198.967581] cx88[0]:   iq 2: 0x29254b80 [ arg #1 ]
[ 9198.967585] cx88[0]:   iq 3: 0x71010000 [ jump irq1 cnt0 count=0 ]
[ 9198.967592] cx88[0]:   iq 4: 0x80008000 [ arg #1 ]
[ 9198.967595] cx88[0]:   iq 5: 0x1c000480 [ write sol eol count=1152 ]
[ 9198.967602] cx88[0]:   iq 6: 0x29459000 [ arg #1 ]
[ 9198.967605] cx88[0]:   iq 7: 0x1c000480 [ write sol eol count=1152 ]
[ 9198.967612] cx88[0]:   iq 8: 0x29459900 [ arg #1 ]
[ 9198.967615] cx88[0]:   iq 9: 0x1c000480 [ write sol eol count=1152 ]
[ 9198.967622] cx88[0]:   iq a: 0x2945a200 [ arg #1 ]
[ 9198.967625] cx88[0]:   iq b: 0x1c000480 [ write sol eol count=1152 ]
[ 9198.967631] cx88[0]:   iq c: 0x2945ab00 [ arg #1 ]
[ 9198.967634] cx88[0]:   iq d: 0x1c000480 [ write sol eol count=1152 ]
[ 9198.967641] cx88[0]:   iq e: 0x2945b400 [ arg #1 ]
[ 9198.967644] cx88[0]:   iq f: 0x18000300 [ write sol count=768 ]
[ 9198.967651] cx88[0]:   iq 10: 0x00180c00 [ arg #1 ]
[ 9198.967653] cx88[0]: fifo: 0x00180c00 -> 0x183400
[ 9198.967656] cx88[0]: ctrl: 0x00180400 -> 0x180460
[ 9198.967659] cx88[0]:   ptr1_reg: 0x00181350
[ 9198.967662] cx88[0]:   ptr2_reg: 0x00180458
[ 9198.967665] cx88[0]:   cnt1_reg: 0x0000006b
[ 9198.967668] cx88[0]:   cnt2_reg: 0x00000000
[ 9198.967675] cx88[0]/0: [f2beb840/0] timeout - dma=0x29f4a000
[ 9198.967678] cx88[0]/0: [f2beb600/1] timeout - dma=0x292bc000
[12146.138624] cx2388x dvb driver version 0.0.6 loaded
[12146.138632] cx8802_register_driver() ->registering driver type=dvb access=shared
[12992.836863] [fglrx:firegl_lock] *ERROR* Process 26521 is using illegal context 0x00000010


I've been trying everything and looking everywhere for anything to help me on this for months. If anyone knows how to fix it I will give you a puppy! :)

Michal

---

### Post by michalski64 on 2008-05-28
bump

---

### Post by prshah on 2008-05-29
> **michalski64 said:**
> 

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : UNKNOWN/GENERIC
    flags:  capture  



The fact that it's showing UNKNOWN/GENERIC means that the card has not been properly setup; I had the same problem with my Mercury PCTV/FM card, until I found the correct modprobe params. Can you post the output of ```
dmesg | grep -i -A 5 -B 5 "unknown/generic"
```

or, if that is blank, the entire dmesg as an attachment?

---

### Post by michalski64 on 2008-06-12
Hey, thanks for the reply. Last week I had a complete meltdown. My hdd went the way of the dinosaurs so I've had to start from scratch. The problem is still there, but at least everything else works as it should.

As a reply to your question, here is the result of the dmesg command.

dmesg | grep -i -A 5 -B 5 "unknown/generic"
[   47.475281] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   47.475285] cx88[0]: try to pick one of the existing card configs via
[   47.475288] cx88[0]: card=<n> insmod option.  Updating to the latest
[   47.475291] cx88[0]: version might help as well.
[   47.475296] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   47.475301] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   47.475305] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   47.475310] cx88[0]:    card=2 -> GDI Black Gold
[   47.475314] cx88[0]:    card=3 -> PixelView
[   47.475318] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   47.475323] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
--
[   47.475499] cx88[0]:    card=52 -> Geniatech DVB-S
[   47.475503] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   47.475507] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   47.475511] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   47.475516] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   47.475522] CORE cx88[0]: subsystem: 1461:8010, board: UNKNOWN/GENERIC [card=0,autodetected]
[   47.475527] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[   47.485011] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   47.537541] cx2388x alsa driver version 0.0.6 loaded
[   47.570150] usb 5-5: reset high speed USB device using ehci_hcd and address 4
[   47.632373] cx88[0]/0: found at 0000:02:01.0, rev: 5, irq: 22, latency: 32, mmio: 0xf8000000


Hope this means something, even with the little knowledge I have of linux and the way drivers work, to me it doesn't look to helpful. Although I could be wrong. Thanks again :)

---

### Post by prshah on 2008-06-13
> **michalski64 said:**
> 

[   47.475281] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   47.475285] cx88[0]: try to pick one of the existing card configs via
[   47.475288] cx88[0]: card=<n> insmod option.  Updating to the latest
[   47.475291] cx88[0]: version might help as well.


Try the following```

sudo modprobe -r cx88
sudo modprobe cx88 card=32
dmesg | tail
```

If you get an error with the first command, there is no point continuing. The first command removes (unloads) the driver used by your tvcard. The next command reloads it, passing it a recognized card number (as in your first post) and the third command tells us the result.

If you get an error in the first command, it will be because the module cx88 is in use by some other module; you need to remove that module first. Eg, if the error messages goes "cx88 is used by cx88b" then you need to remove cx88b first, then cx88. Post back with error messages if you have any doubts.

---

### Post by michalski64 on 2008-06-30
Thanks for trying, the first command told me FATAL: Module cx88 not found. A while ago I was thinking that it used the other drivers but that didnt work either. I may have to just bite the bullet and buy a better card.

---

