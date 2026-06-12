---
title: "Need Help Getting Tv Card SSD-TV-675PLUS (saa7130) to work"
date: 2010-12-12
forum: Multimedia Software
---

### Post by charlesbandacb on 2010-12-12
Hi everyone,

I have a Dell optiplex GX260, 2.4ghz speed, 512 ram,40gb hard disk. I have installed two operating systems XP and ubuntu 9.10. My problem is getting the new Tv card to work with ubuntu. With xp it works with no problem. I tried to download prgrams like tvtime and xawtv but all amounted to nothing. tvtime fails even to launch while xawtv launches and hangs the computer and nothing responds. I have to manually shut it down using the power button. anybody is welcome to help , try to use simple language . I did run the Command ( *sudo dmesg*) to extract some info that I thought might help and is pasted below.

[   15.817800] Linux video capture interface: v2.00
[   18.680474] saa7130/34: v4l2 driver version 0.2.15 loaded
[   18.680565] saa7134 0000:01:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.680575] saa7130[0]: found at 0000:01:07.0, rev: 1, irq: 16, latency: 64, mmio: 0xff8ffc00
[   18.680585] saa7134: <rant>
[   18.680587] saa7134:  Congratulations!  Your TV card vendor saved a few
[   18.680589] saa7134:  cents for a eeprom, thus your pci board has no
[   18.680591] saa7134:  subsystem ID and I can't identify it automatically
[   18.680592] saa7134: </rant>
[   18.680594] saa7134: I feel better now.  Ok, here are the good news:
[   18.680595] saa7134: You can use the card=<nr> insmod option to specify
[   18.680597] saa7134: which board do you have.  The list:




[   18.681925] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   18.681956] saa7130[0]: board init: gpio is 804000
[   18.681968] IRQ 16/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   18.784256] saa7130[0]: Huh, no eeprom present (err=-5)?
[   18.784266] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[   18.784901] saa7130[0]: registered device video0 [v4l2]
[   18.784936] saa7130[0]: registered device vbi0
[   19.072393] saa7134 ALSA driver for DMA sound loaded
[   19.072403] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[   19.231498]   alloc irq_desc for 17 on node -1
[   19.231504]   alloc kstat_irqs on node -1
[   19.231517] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.231578] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   19.608049] intel8x0_measure_ac97_clock: measured 54214 usecs (2612 samples)
[   19.608055] intel8x0: clocking to 48000
[   54.446013] ISO 9660 Extensions: Microsoft Joliet Level 1
[   54.485719] ISOFS: changing to secondary root
charles@charles-desktop:~$

---

### Post by hansum_rahul on 2011-01-12
I have the same TV Tuner card... used to work on my 8.04 box.. worked when I tested on 9.04 too... somehow it does not work on 10.10 Maverick Meerkat... (please pardon my english.. I know it sucks :P)

I used this to make Linux recognize my Tuner:
```
sudo modprobe saa7134 card=3 tuner=69
```

It does now work now... I get this error in dmesg :
[B][14626.699243] Linux video capture interface: v2.00
[14626.710103] IR JVC protocol handler initialized
[14626.728110] IR Sony protocol handler initialized
[14626.743578] saa7134: disagrees about version of symbol __ir_input_register
[14626.743586] saa7134: Unknown symbol __ir_input_register (err -22)
[14626.760605] lirc_dev: IR Remote Control driver registered, major 247 
[14626.764523] IR LIRC bridge handler initialized[/B]

I try to 'not' load the ir module by first unloading them:
```
sudo rmmod ir_common ir_lirc_codec ir_sony_decoder ir_jvc_decoder ir_rc6_decoder ir_rc5_decoder ir_nec_decoder ir_core lirc_dev 
```

Doing this
```
lsmod | grep ir
```

I am confirmed that no IR modules remain. Then I try again with:
```
sudo modprobe saa7134 card=3 tuner=69 disable_ir=1
```

Still, the same...:(

My kernel version is: **2.6.35.24**

---

