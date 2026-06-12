---
title: "Using dd to rip a dvd movie to an iso file - seriously slow"
date: 2009-04-10
forum: Multimedia Software
---

### Post by graysky on 2009-04-10
Basically, I want to take a DVD movie and rip it to an ISO file.

```
dd if=/dev/scd0 of=/home/user1/image.iso
557177+0 records in
557176+0 records out
285274112 bytes (285 MB) copied, 76.3168 s, 3.7 MB/s
```
For some reason is goes very slowly!  I have also done a simple 'cat /dev/scd0 > image.iso' and it too is very slow.  The DVDROM drive never spins up.

I can do this w/ DVD-Decrypter and WINE, but DVD Decrypter goes very slowly (1.7x-2.0x) too.  I know it's not my hardware because this same machine booted into XP does this operation around 12-14x in DVD-Decrypter.  Also, k3b is dog-slow writing an iso.

Any ideas why it's so slow?  Thanks all!

---

### Post by mc4man on 2009-04-10
Maybe check your various logs to see if your drive is being soft reset to a pio mode

grep 'UDMA' /var/log/dmesg
grep 'UDMA' /var/log/kern.log

Also check it's dma setting in hdparm (adjust red if needed, should see *udma2 or *udma4 as active mode

sudo hdparm -i /dev/scd[COLOR="Red"]0[/COLOR]

---

### Post by graysky on 2009-04-10
Thanks for the reply.  I believe UDMA is enabled.  I posted the output to your suggestions below.  What do you think?

```
$ sudo hdparm -i /dev/scd0

/dev/scd0:

 Model=BENQ    DVD DD DW1640                   , FwRev=BSRB    , SerialNo=9JC5U150C353364133SP
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode
```

```
$ grep 'UDMA' /var/log/dmesg
[    1.156127] ata1: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
[    1.156129] ata2: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
[    1.168597] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 30
[    1.168600] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 30
[    1.168602] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 30
[    1.168604] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 30
[    1.168606] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 30
[    1.168608] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 30
[    1.317818] ata1.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
[    1.334498] ata1.00: configured for UDMA/33
[    1.655009] ata3.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
[    1.656604] ata3.00: configured for UDMA/133
[    2.134664] ata4.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
[    2.136346] ata4.00: configured for UDMA/133
[    3.481061] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
[    3.481065] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
```

```
$ grep 'UDMA' /var/log/kern.log
Apr  5 07:22:35 hope kernel: [    1.124573] ata7: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  5 07:22:35 hope kernel: [    1.124575] ata8: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  5 07:22:35 hope kernel: [    1.130333] ata1: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 30
Apr  5 07:22:35 hope kernel: [    1.130336] ata2: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 30
Apr  5 07:22:35 hope kernel: [    1.130338] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 30
Apr  5 07:22:35 hope kernel: [    1.130340] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 30
Apr  5 07:22:35 hope kernel: [    1.130342] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 30
Apr  5 07:22:35 hope kernel: [    1.130344] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 30
Apr  5 07:22:35 hope kernel: [    1.285034] ata7.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  5 07:22:35 hope kernel: [    1.298299] ata7.00: configured for UDMA/33
Apr  5 07:22:35 hope kernel: [    1.611263] ata1.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  5 07:22:35 hope kernel: [    1.612860] ata1.00: configured for UDMA/133
Apr  5 07:22:35 hope kernel: [    2.091365] ata2.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  5 07:22:35 hope kernel: [    2.093045] ata2.00: configured for UDMA/133
Apr  5 07:22:35 hope kernel: [    3.426894] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  5 07:22:35 hope kernel: [    3.426897] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  5 18:35:38 hope kernel: [    1.175561] ata1: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  5 18:35:38 hope kernel: [    1.175563] ata2: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  5 18:35:38 hope kernel: [    1.181367] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 30
Apr  5 18:35:38 hope kernel: [    1.181370] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 30
Apr  5 18:35:38 hope kernel: [    1.181372] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 30
Apr  5 18:35:38 hope kernel: [    1.181374] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 30
Apr  5 18:35:38 hope kernel: [    1.181376] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 30
Apr  5 18:35:38 hope kernel: [    1.181378] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 30
Apr  5 18:35:38 hope kernel: [    1.337977] ata1.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  5 18:35:38 hope kernel: [    1.351182] ata1.00: configured for UDMA/33
Apr  5 18:35:38 hope kernel: [    1.661267] ata3.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  5 18:35:38 hope kernel: [    1.662881] ata3.00: configured for UDMA/133
Apr  5 18:35:38 hope kernel: [    2.141345] ata4.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  5 18:35:38 hope kernel: [    2.143029] ata4.00: configured for UDMA/133
Apr  5 18:35:38 hope kernel: [    3.433561] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  5 18:35:38 hope kernel: [    3.433564] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  6 03:01:52 hope kernel: [    1.189547] ata7: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  6 03:01:52 hope kernel: [    1.189549] ata8: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  6 03:01:52 hope kernel: [    1.189784] ata1: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 31
Apr  6 03:01:52 hope kernel: [    1.189786] ata2: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 31
Apr  6 03:01:52 hope kernel: [    1.189788] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 31
Apr  6 03:01:52 hope kernel: [    1.189790] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 31
Apr  6 03:01:52 hope kernel: [    1.189791] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 31
Apr  6 03:01:52 hope kernel: [    1.189793] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 31
Apr  6 03:01:52 hope kernel: [    1.350789] ata7.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  6 03:01:52 hope kernel: [    1.360764] ata7.00: configured for UDMA/33
Apr  6 03:01:52 hope kernel: [    1.667918] ata1.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  6 03:01:52 hope kernel: [    1.669512] ata1.00: configured for UDMA/133
Apr  6 03:01:52 hope kernel: [    2.549237] ata2.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  6 03:01:52 hope kernel: [    2.550945] ata2.00: configured for UDMA/133
Apr  6 03:01:52 hope kernel: [    3.843560] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  6 03:01:52 hope kernel: [    3.843563] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  6 03:37:32 hope kernel: [    1.178813] ata1: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 31
Apr  6 03:37:32 hope kernel: [    1.178815] ata2: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 31
Apr  6 03:37:32 hope kernel: [    1.178818] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 31
Apr  6 03:37:32 hope kernel: [    1.178820] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 31
Apr  6 03:37:32 hope kernel: [    1.178822] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 31
Apr  6 03:37:32 hope kernel: [    1.178824] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 31
Apr  6 03:37:32 hope kernel: [    1.179227] ata7: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  6 03:37:32 hope kernel: [    1.179228] ata8: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  6 03:37:32 hope kernel: [    1.337412] ata7.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  6 03:37:32 hope kernel: [    1.350796] ata7.00: configured for UDMA/33
Apr  6 03:37:32 hope kernel: [    1.657929] ata1.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  6 03:37:32 hope kernel: [    1.659541] ata1.00: configured for UDMA/133
Apr  6 03:37:32 hope kernel: [    2.139252] ata2.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  6 03:37:32 hope kernel: [    2.140937] ata2.00: configured for UDMA/133
Apr  6 03:37:32 hope kernel: [    3.486895] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  6 03:37:32 hope kernel: [    3.486899] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  6 15:32:42 hope kernel: [    1.117289] ata1: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  6 15:32:42 hope kernel: [    1.117291] ata2: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  6 15:32:42 hope kernel: [    1.119127] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 29
Apr  6 15:32:42 hope kernel: [    1.119130] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 29
Apr  6 15:32:42 hope kernel: [    1.119132] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 29
Apr  6 15:32:42 hope kernel: [    1.119134] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 29
Apr  6 15:32:42 hope kernel: [    1.119136] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 29
Apr  6 15:32:42 hope kernel: [    1.119139] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 29
Apr  6 15:32:42 hope kernel: [    1.281306] ata1.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  6 15:32:42 hope kernel: [    1.297416] ata1.00: configured for UDMA/33
Apr  6 15:32:42 hope kernel: [    1.597955] ata3.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  6 15:32:42 hope kernel: [    1.599568] ata3.00: configured for UDMA/133
Apr  6 15:32:42 hope kernel: [    2.094676] ata4.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  6 15:32:42 hope kernel: [    2.096341] ata4.00: configured for UDMA/133
Apr  6 15:32:42 hope kernel: [    2.993383] ata5.00: ATA-8: WDC WD7501AALS-00J7B0, 05.00K05, max UDMA/133
Apr  6 15:32:42 hope kernel: [    2.994356] ata5.00: configured for UDMA/133
Apr  6 15:32:42 hope kernel: [    4.023562] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  6 15:32:42 hope kernel: [    4.023565] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  6 16:21:15 hope kernel: [    1.160573] ata1: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 31
Apr  6 16:21:15 hope kernel: [    1.160576] ata2: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 31
Apr  6 16:21:15 hope kernel: [    1.160578] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 31
Apr  6 16:21:15 hope kernel: [    1.160580] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 31
Apr  6 16:21:15 hope kernel: [    1.160582] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 31
Apr  6 16:21:15 hope kernel: [    1.160584] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 31
Apr  6 16:21:15 hope kernel: [    1.160675] ata7: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  6 16:21:15 hope kernel: [    1.160677] ata8: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  6 16:21:15 hope kernel: [    1.318651] ata7.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  6 16:21:15 hope kernel: [    1.331999] ata7.00: configured for UDMA/33
Apr  6 16:21:15 hope kernel: [    1.637921] ata1.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  6 16:21:15 hope kernel: [    1.639532] ata1.00: configured for UDMA/133
Apr  6 16:21:15 hope kernel: [    2.118022] ata2.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  6 16:21:15 hope kernel: [    2.119737] ata2.00: configured for UDMA/133
Apr  6 16:21:15 hope kernel: [    2.997535] ata3.00: ATA-8: WDC WD7501AALS-00J7B0, 05.00K05, max UDMA/133
Apr  6 16:21:15 hope kernel: [    2.998486] ata3.00: configured for UDMA/133
Apr  6 16:21:15 hope kernel: [    3.996892] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  6 16:21:15 hope kernel: [    3.996895] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  7 03:23:12 hope kernel: [    1.123758] ata1: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  7 03:23:12 hope kernel: [    1.123760] ata2: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  7 03:23:12 hope kernel: [    1.131916] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 31
Apr  7 03:23:12 hope kernel: [    1.131918] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 31
Apr  7 03:23:12 hope kernel: [    1.131920] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 31
Apr  7 03:23:12 hope kernel: [    1.131922] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 31
Apr  7 03:23:12 hope kernel: [    1.131925] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 31
Apr  7 03:23:12 hope kernel: [    1.131927] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 31
Apr  7 03:23:12 hope kernel: [    1.281685] ata1.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  7 03:23:12 hope kernel: [    1.294893] ata1.00: configured for UDMA/33
Apr  7 03:23:12 hope kernel: [    1.611276] ata3.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  7 03:23:12 hope kernel: [    1.612874] ata3.00: configured for UDMA/133
Apr  7 03:23:12 hope kernel: [    2.104692] ata4.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  7 03:23:12 hope kernel: [    2.106351] ata4.00: configured for UDMA/133
Apr  7 03:23:12 hope kernel: [    3.007964] ata5.00: ATA-8: WDC WD7501AALS-00J7B0, 05.00K05, max UDMA/133
Apr  7 03:23:12 hope kernel: [    3.008912] ata5.00: configured for UDMA/133
Apr  7 03:23:12 hope kernel: [    3.993564] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  7 03:23:12 hope kernel: [    3.993567] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  8 07:18:14 hope kernel: [    1.169084] ata1: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  8 07:18:14 hope kernel: [    1.169086] ata2: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  8 07:18:14 hope kernel: [    1.172102] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 31
Apr  8 07:18:14 hope kernel: [    1.172104] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 31
Apr  8 07:18:14 hope kernel: [    1.172106] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 31
Apr  8 07:18:14 hope kernel: [    1.172108] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 31
Apr  8 07:18:14 hope kernel: [    1.172110] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 31
Apr  8 07:18:14 hope kernel: [    1.172112] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 31
Apr  8 07:18:14 hope kernel: [    1.327413] ata1.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  8 07:18:14 hope kernel: [    1.340844] ata1.00: configured for UDMA/33
Apr  8 07:18:14 hope kernel: [    1.652111] ata3.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  8 07:18:14 hope kernel: [    1.653736] ata3.00: configured for UDMA/133
Apr  8 07:18:14 hope kernel: [    2.145494] ata4.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  8 07:18:14 hope kernel: [    2.147181] ata4.00: configured for UDMA/133
Apr  8 07:18:14 hope kernel: [    3.048360] ata5.00: ATA-8: WDC WD7501AALS-00J7B0, 05.00K05, max UDMA/133
Apr  8 07:18:14 hope kernel: [    3.049324] ata5.00: configured for UDMA/133
Apr  8 07:18:14 hope kernel: [    4.020230] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  8 07:18:14 hope kernel: [    4.020233] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  8 16:27:28 hope kernel: [    1.165565] ata1: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 31
Apr  8 16:27:28 hope kernel: [    1.165567] ata2: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 31
Apr  8 16:27:28 hope kernel: [    1.165569] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 31
Apr  8 16:27:28 hope kernel: [    1.165571] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 31
Apr  8 16:27:28 hope kernel: [    1.165573] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 31
Apr  8 16:27:28 hope kernel: [    1.165574] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 31
Apr  8 16:27:28 hope kernel: [    1.166200] ata7: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  8 16:27:28 hope kernel: [    1.166201] ata8: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  8 16:27:28 hope kernel: [    1.325598] ata7.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  8 16:27:28 hope kernel: [    1.337438] ata7.00: configured for UDMA/33
Apr  8 16:27:28 hope kernel: [    1.644603] ata1.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  8 16:27:28 hope kernel: [    1.646218] ata1.00: configured for UDMA/133
Apr  8 16:27:28 hope kernel: [    2.124698] ata2.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  8 16:27:28 hope kernel: [    2.126376] ata2.00: configured for UDMA/133
Apr  8 16:27:28 hope kernel: [    3.007336] ata3.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Apr  8 16:27:28 hope kernel: [    3.008093] ata3.00: configured for UDMA/133
Apr  8 16:27:28 hope kernel: [    3.980226] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  8 16:27:28 hope kernel: [    3.980230] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr  8 16:27:28 hope kernel: [    4.461284] ata9.00: ATA-8: WDC WD7501AALS-00J7B0, 05.00K05, max UDMA/133
Apr  8 16:27:28 hope kernel: [    4.463148] ata9.00: configured for UDMA/133
Apr  9 12:54:27 hope kernel: [    1.158206] ata1: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr  9 12:54:27 hope kernel: [    1.158208] ata2: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr  9 12:54:27 hope kernel: [    1.191919] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 31
Apr  9 12:54:27 hope kernel: [    1.191922] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 31
Apr  9 12:54:27 hope kernel: [    1.191924] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 31
Apr  9 12:54:27 hope kernel: [    1.191926] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 31
Apr  9 12:54:27 hope kernel: [    1.191928] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 31
Apr  9 12:54:27 hope kernel: [    1.191931] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 31
Apr  9 12:54:27 hope kernel: [    1.317412] ata1.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr  9 12:54:27 hope kernel: [    1.331614] ata1.00: configured for UDMA/33
Apr  9 12:54:27 hope kernel: [    1.667944] ata3.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  9 12:54:27 hope kernel: [    1.669543] ata3.00: configured for UDMA/133
Apr  9 12:54:27 hope kernel: [    2.152162] ata4.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr  9 12:54:27 hope kernel: [    2.153847] ata4.00: configured for UDMA/133
Apr  9 12:54:27 hope kernel: [    3.047325] ata5.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
Apr  9 12:54:27 hope kernel: [    3.048087] ata5.00: configured for UDMA/133
Apr  9 12:54:27 hope kernel: [    4.020230] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr  9 12:54:27 hope kernel: [    4.020233] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
Apr 10 10:26:58 hope kernel: [    1.156127] ata1: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
Apr 10 10:26:58 hope kernel: [    1.156129] ata2: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
Apr 10 10:26:58 hope kernel: [    1.168597] ata3: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd100 irq 30
Apr 10 10:26:58 hope kernel: [    1.168600] ata4: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd180 irq 30
Apr 10 10:26:58 hope kernel: [    1.168602] ata5: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd200 irq 30
Apr 10 10:26:58 hope kernel: [    1.168604] ata6: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd280 irq 30
Apr 10 10:26:58 hope kernel: [    1.168606] ata7: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd300 irq 30
Apr 10 10:26:58 hope kernel: [    1.168608] ata8: SATA max UDMA/133 abar m2048@0xfdffd000 port 0xfdffd380 irq 30
Apr 10 10:26:58 hope kernel: [    1.317818] ata1.00: ATAPI: BENQ    DVD DD DW1640, BSRB, max UDMA/33
Apr 10 10:26:58 hope kernel: [    1.334498] ata1.00: configured for UDMA/33
Apr 10 10:26:58 hope kernel: [    1.655009] ata3.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr 10 10:26:58 hope kernel: [    1.656604] ata3.00: configured for UDMA/133
Apr 10 10:26:58 hope kernel: [    2.134664] ata4.00: ATA-8: ST3640323AS, SD1B, max UDMA/133
Apr 10 10:26:58 hope kernel: [    2.136346] ata4.00: configured for UDMA/133
Apr 10 10:26:58 hope kernel: [    3.481061] ata9: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 16
Apr 10 10:26:58 hope kernel: [    3.481065] ata10: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe180 irq 16
```

---

### Post by iduriduridur on 2009-05-01
I am willing to bet that DMA is correctly setup on on your machine. I have the same problem on different working hardware. I have tested on different hardware like a Dell latitude d620 and d610 to a  AMD home built desktop. Something I have noticed is that I get slow DVD reads on ubuntu setups. If I take the same hardware install centos or debian it copies fine around 40-60 MB/s. I have not figured out why ubuntu is slow though. Something with libata setup in ubuntu?

---

### Post by graysky on 2009-05-01
I just broken down and am using k3b to do it; speed is better now for some reason I can't explain.

---

### Post by SuperSonic4 on 2009-05-01
k9copy is a better ripper than k3b ;)

---

### Post by mc4man on 2009-05-01
Seems hard to figure, isn't the dvd drive itself. (what you posted is perfect

Have the same drive (using BSMB firmware) and even though it's showing some age still reads very fast (maxs out at 15+x

Screen shows a graph of a dvd5 dump to .iso of a dvd movie (disk is a little scuffed on outer edge, notice speed drops.

For playback solely from a hdd and no shrinking, editing, ect. I use dvdisaster to 'read' the disk.

Maybe give it a try
(you need to authenticate the disk/drive first before attempting 'read', just open disc first in a player, pause, start the dvdisaster read and close the player

---

