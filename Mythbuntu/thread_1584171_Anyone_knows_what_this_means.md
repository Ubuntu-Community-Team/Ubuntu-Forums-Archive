---
title: "Anyone knows what this means?"
date: 2010-09-28
forum: Mythbuntu
---

### Post by Mad_Professor on 2010-09-28
I recently swap motherboards twice over, due to the old one dying via  bad capacitors, second board having kernel issues with the pci and nforce2  chipset and the current one which is via based.

I'm not having any problems, actually it's running more smoothly then the second MSI board I had before this gigabyte board.

But when I watch TV I get these in dmesg.
```

[  490.284248] cx88[0]/0: [f5bdf240/2] timeout - dma=0x35bc2000
[  490.284252] cx88[0]/0: [f5bdf6c0/3] timeout - dma=0x35b50000
[  491.916025] cx88[0]: video y / packed - dma channel status dump
[  491.916037] cx88[0]:   cmds: initial risc: 0x35a0e000
[  491.916042] cx88[0]:   cmds: cdt base    : 0x00180440
[  491.916046] cx88[0]:   cmds: cdt size    : 0x0000000c
[  491.916050] cx88[0]:   cmds: iq base     : 0x00180400
[  491.916054] cx88[0]:   cmds: iq size     : 0x00000010
[  491.916058] cx88[0]:   cmds: risc pc     : 0x35a0e034
[  491.916062] cx88[0]:   cmds: iq wr ptr   : 0x00000106
[  491.916066] cx88[0]:   cmds: iq rd ptr   : 0x0000010a
[  491.916070] cx88[0]:   cmds: cdt current : 0x00000488
[  491.916074] cx88[0]:   cmds: pci target  : 0x35bb0800
[  491.916078] cx88[0]:   cmds: line / byte : 0x02f00000
[  491.916082] cx88[0]:   risc0: 0x80008000 [ sync resync count=0 ]
[  491.916089] cx88[0]:   risc1: 0x1c0003c0 [ write sol eol count=960 ]
[  491.916097] cx88[0]:   risc2: 0x35acc000 [ arg #1 ]
[  491.916101] cx88[0]:   risc3: 0x1c0003c0 [ write sol eol count=960 ]
[  491.916112] cx88[0]:   iq 0: 0x140002c0 [ write eol count=704 ]
[  491.916118] cx88[0]:   iq 1: 0x35be0000 [ arg #1 ]
[  491.916122] cx88[0]:   iq 2: 0x1c0003c0 [ write sol eol count=960 ]
[  491.916129] cx88[0]:   iq 3: 0x35be0680 [ arg #1 ]
[  491.916133] cx88[0]:   iq 4: 0x18000200 [ write sol count=512 ]
[  491.916139] cx88[0]:   iq 5: 0x35be0e00 [ arg #1 ]
[  491.916143] cx88[0]:   iq 6: 0x1c0003c0 [ write sol eol count=960 ]
[  491.916150] cx88[0]:   iq 7: 0x35bb0440 [ arg #1 ]
[  491.916153] cx88[0]:   iq 8: 0x71010000 [ jump irq1 cnt0 count=0 ]
[  491.916160] cx88[0]:   iq 9: 0x80008000 [ arg #1 ]
[  491.916164] cx88[0]:   iq a: 0x1c0003c0 [ write sol eol count=960 ]
[  491.916171] cx88[0]:   iq b: 0x35acc000 [ arg #1 ]
[  491.916174] cx88[0]:   iq c: 0x1c0003c0 [ write sol eol count=960 ]
[  491.916181] cx88[0]:   iq d: 0x35acc780 [ arg #1 ]
[  491.916185] cx88[0]:   iq e: 0x18000100 [ write sol count=256 ]
[  491.916191] cx88[0]:   iq f: 0x35accf00 [ arg #1 ]
[  491.916195] cx88[0]: fifo: 0x00180c00 -> 0x183400
[  491.916198] cx88[0]: ctrl: 0x00180400 -> 0x180460
[  491.916202] cx88[0]:   ptr1_reg: 0x00180c00
[  491.916205] cx88[0]:   ptr2_reg: 0x00180448
[  491.916208] cx88[0]:   cnt1_reg: 0x00000000
[  491.916212] cx88[0]:   cnt2_reg: 0x00000000
[  491.916222] cx88[0]/0: [f5bdfa80/0] timeout - dma=0x35a0e000
[  491.916226] cx88[0]/0: [f5bdf900/1] timeout - dma=0x35b50000
[  491.916230] cx88[0]/0: [f5bdf240/2] timeout - dma=0x35bc2000
[  491.916234] cx88[0]/0: [f5bdf6c0/3] timeout - dma=0x36a90000
[  491.916238] cx88[0]/0: [f5bdf9c0/4] timeout - dma=0x36b66000
[  492.768027] cx88[0]: video y / packed - dma channel status dump
[  492.768038] cx88[0]:   cmds: initial risc: 0x36b66000
[  492.768043] cx88[0]:   cmds: cdt base    : 0x00180440
[  492.768047] cx88[0]:   cmds: cdt size    : 0x0000000c
[  492.768051] cx88[0]:   cmds: iq base     : 0x00180400
[  492.768055] cx88[0]:   cmds: iq size     : 0x00000010
[  492.768059] cx88[0]:   cmds: risc pc     : 0x35bc2958
[  492.768067] cx88[0]:   cmds: iq wr ptr   : 0x00000100
[  492.768071] cx88[0]:   cmds: iq rd ptr   : 0x00000104
[  492.768075] cx88[0]:   cmds: cdt current : 0x00000448
[  492.768078] cx88[0]:   cmds: pci target  : 0x36a32440
[  492.768082] cx88[0]:   cmds: line / byte : 0x00f00000
[  492.768086] cx88[0]:   risc0: 0x80008200 [ sync resync count=512 ]
[  492.768094] cx88[0]:   risc1: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768101] cx88[0]:   risc2: 0x369a43c0 [ arg #1 ]
[  492.768106] cx88[0]:   risc3: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768113] cx88[0]:   iq 0: 0x36a31900 [ INVALID eol irq2 23 21 cnt1 cnt0 12 count=2304 ]
[  492.768123] cx88[0]:   iq 1: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768130] cx88[0]:   iq 2: 0x36a32080 [ arg #1 ]
[  492.768134] cx88[0]:   iq 3: 0x80008200 [ sync resync count=512 ]
[  492.768140] cx88[0]:   iq 4: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768147] cx88[0]:   iq 5: 0x369a43c0 [ arg #1 ]
[  492.768150] cx88[0]:   iq 6: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768158] cx88[0]:   iq 7: 0x369a4b40 [ arg #1 ]
[  492.768161] cx88[0]:   iq 8: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768168] cx88[0]:   iq 9: 0x369a52c0 [ arg #1 ]
[  492.768172] cx88[0]:   iq a: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768179] cx88[0]:   iq b: 0x369a5a40 [ arg #1 ]
[  492.768183] cx88[0]:   iq c: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768190] cx88[0]:   iq d: 0x369a61c0 [ arg #1 ]
[  492.768193] cx88[0]:   iq e: 0x1c0003c0 [ write sol eol count=960 ]
[  492.768200] cx88[0]:   iq f: 0x369a6940 [ arg #1 ]
[  492.768204] cx88[0]: fifo: 0x00180c00 -> 0x183400
[  492.768207] cx88[0]: ctrl: 0x00180400 -> 0x180460
[  492.768211] cx88[0]:   ptr1_reg: 0x00181740
[  492.768214] cx88[0]:   ptr2_reg: 0x00180478
[  492.768217] cx88[0]:   cnt1_reg: 0x00000000
[  492.768221] cx88[0]:   cnt2_reg: 0x00000000
[  492.768231] cx88[0]/0: [f5bdf240/2] timeout - dma=0x35bc2000
[  492.768235] cx88[0]/0: [f5bdf6c0/3] timeout - dma=0x35b50000
[  492.768239] cx88[0]/0: [f5bdf9c0/4] timeout - dma=0x35a0e000
[  492.768243] cx88[0]/0: [f5bdfa80/0] timeout - dma=0x36b66000
[  492.768247] cx88[0]/0: [f5bdf900/1] timeout - dma=0x36a90000
[  495.396019] cx88[0]: video y / packed - dma channel status dump
[  495.396031] cx88[0]:   cmds: initial risc: 0x35a0e000
[  495.396035] cx88[0]:   cmds: cdt base    : 0x00180440
[  495.396040] cx88[0]:   cmds: cdt size    : 0x0000000c
[  495.396044] cx88[0]:   cmds: iq base     : 0x00180400
[  495.396048] cx88[0]:   cmds: iq size     : 0x00000010
[  495.396051] cx88[0]:   cmds: risc pc     : 0x36b66958
[  495.396055] cx88[0]:   cmds: iq wr ptr   : 0x0000010c
[  495.396059] cx88[0]:   cmds: iq rd ptr   : 0x00000100
[  495.396063] cx88[0]:   cmds: cdt current : 0x00000468
[  495.396067] cx88[0]:   cmds: pci target  : 0x35bb0440
[  495.396071] cx88[0]:   cmds: line / byte : 0x00f00000
[  495.396075] cx88[0]:   risc0: 0x80008200 [ sync resync count=512 ]
[  495.396083] cx88[0]:   risc1: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396090] cx88[0]:   risc2: 0x35afe3c0 [ arg #1 ]
[  495.396103] cx88[0]:   risc3: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396110] cx88[0]:   iq 0: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396117] cx88[0]:   iq 1: 0x35afe3c0 [ arg #1 ]
[  495.396120] cx88[0]:   iq 2: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396127] cx88[0]:   iq 3: 0x35afeb40 [ arg #1 ]
[  495.396131] cx88[0]:   iq 4: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396138] cx88[0]:   iq 5: 0x35aff2c0 [ arg #1 ]
[  495.396141] cx88[0]:   iq 6: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396148] cx88[0]:   iq 7: 0x35affa40 [ arg #1 ]
[  495.396152] cx88[0]:   iq 8: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396159] cx88[0]:   iq 9: 0x35b401c0 [ arg #1 ]
[  495.396162] cx88[0]:   iq a: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396169] cx88[0]:   iq b: 0x35b40940 [ arg #1 ]
[  495.396173] cx88[0]:   iq c: 0x35baf900 [ INVALID eol irq1 23 21 20 19 cnt1 resync 14 13 12 count=2304 ]
[  495.396185] cx88[0]:   iq d: 0x1c0003c0 [ write sol eol count=960 ]
[  495.396192] cx88[0]:   iq e: 0x35bb0080 [ arg #1 ]
[  495.396196] cx88[0]:   iq f: 0x80008200 [ sync resync count=512 ]
[  495.396201] cx88[0]: fifo: 0x00180c00 -> 0x183400
[  495.396205] cx88[0]: ctrl: 0x00180400 -> 0x180460
[  495.396209] cx88[0]:   ptr1_reg: 0x00182078
[  495.396212] cx88[0]:   ptr2_reg: 0x00180498
[  495.396215] cx88[0]:   cnt1_reg: 0x00000047
[  495.396219] cx88[0]:   cnt2_reg: 0x00000000
[  495.396229] cx88[0]/0: [f5bdf9c0/4] timeout - dma=0x36b66000
[  495.396233] cx88[0]/0: [f5bdfa80/0] timeout - dma=0x35a0e000
[  495.396237] cx88[0]/0: [f5bdf900/1] timeout - dma=0x35b50000
[  495.396241] cx88[0]/0: [f5bdf240/2] timeout - dma=0x35bc2000
[  495.396245] cx88[0]/0: [f5bdf6c0/3] timeout - dma=0x36a90000
[  496.516020] cx88[0]: video y / packed - dma channel status dump
[  496.516031] cx88[0]:   cmds: initial risc: 0x36b66000
[  496.516036] cx88[0]:   cmds: cdt base    : 0x00180440
[  496.516040] cx88[0]:   cmds: cdt size    : 0x0000000c
[  496.516044] cx88[0]:   cmds: iq base     : 0x00180400
[  496.516048] cx88[0]:   cmds: iq size     : 0x00000010
[  496.516052] cx88[0]:   cmds: risc pc     : 0x35bc2958
[  496.516056] cx88[0]:   cmds: iq wr ptr   : 0x00000100
[  496.516060] cx88[0]:   cmds: iq rd ptr   : 0x00000104
[  496.516064] cx88[0]:   cmds: cdt current : 0x00000498
[  496.516068] cx88[0]:   cmds: pci target  : 0x36a32440
[  496.516071] cx88[0]:   cmds: line / byte : 0x00f00000
[  496.516075] cx88[0]:   risc0: 0x80008200 [ sync resync count=512 ]
[  496.516083] cx88[0]:   risc1: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516094] cx88[0]:   risc2: 0x369a43c0 [ arg #1 ]
[  496.516099] cx88[0]:   risc3: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516106] cx88[0]:   iq 0: 0x36a31900 [ INVALID eol irq2 23 21 cnt1 cnt0 12 count=2304 ]
[  496.516116] cx88[0]:   iq 1: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516123] cx88[0]:   iq 2: 0x36a32080 [ arg #1 ]
[  496.516127] cx88[0]:   iq 3: 0x80008200 [ sync resync count=512 ]
[  496.516133] cx88[0]:   iq 4: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516140] cx88[0]:   iq 5: 0x369a43c0 [ arg #1 ]
[  496.516144] cx88[0]:   iq 6: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516151] cx88[0]:   iq 7: 0x369a4b40 [ arg #1 ]
[  496.516154] cx88[0]:   iq 8: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516162] cx88[0]:   iq 9: 0x369a52c0 [ arg #1 ]
[  496.516165] cx88[0]:   iq a: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516172] cx88[0]:   iq b: 0x369a5a40 [ arg #1 ]
[  496.516176] cx88[0]:   iq c: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516183] cx88[0]:   iq d: 0x369a61c0 [ arg #1 ]
[  496.516186] cx88[0]:   iq e: 0x1c0003c0 [ write sol eol count=960 ]
[  496.516194] cx88[0]:   iq f: 0x369a6940 [ arg #1 ]
[  496.516197] cx88[0]: fifo: 0x00180c00 -> 0x183400
[  496.516200] cx88[0]: ctrl: 0x00180400 -> 0x180460
[  496.516204] cx88[0]:   ptr1_reg: 0x00181300
[  496.516207] cx88[0]:   ptr2_reg: 0x00180468
[  496.516210] cx88[0]:   cnt1_reg: 0x00000000
[  496.516214] cx88[0]:   cnt2_reg: 0x00000000
[  496.516224] cx88[0]/0: [f5bdf240/2] timeout - dma=0x35bc2000
[  496.516229] cx88[0]/0: [f5bdf6c0/3] timeout - dma=0x35b50000
[  496.516233] cx88[0]/0: [f5bdf9c0/4] timeout - dma=0x35a0e000
[  496.516237] cx88[0]/0: [f5bdfa80/0] timeout - dma=0x36b66000
[  496.516240] cx88[0]/0: [f5bdf900/1] timeout - dma=0x36a90000
[  497.252021] cx88[0]: video y / packed - dma channel status dump
[  497.252032] cx88[0]:   cmds: initial risc: 0x35a0e000
[  497.252036] cx88[0]:   cmds: cdt base    : 0x00180440
[  497.252041] cx88[0]:   cmds: cdt size    : 0x0000000c
[  497.252045] cx88[0]:   cmds: iq base     : 0x00180400
[  497.252049] cx88[0]:   cmds: iq size     : 0x00000010
[  497.252053] cx88[0]:   cmds: risc pc     : 0x35b50958
[  497.252056] cx88[0]:   cmds: iq wr ptr   : 0x0000010b
[  497.252060] cx88[0]:   cmds: iq rd ptr   : 0x0000010f
[  497.252064] cx88[0]:   cmds: cdt current : 0x00000458
[  497.252068] cx88[0]:   cmds: pci target  : 0x36abb440
[  497.252072] cx88[0]:   cmds: line / byte : 0x00f00000
[  497.252076] cx88[0]:   risc0: 0x80008200 [ sync resync count=512 ]
[  497.252084] cx88[0]:   risc1: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252091] cx88[0]:   risc2: 0x3595e3c0 [ arg #1 ]
[  497.252096] cx88[0]:   risc3: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252103] cx88[0]:   iq 0: 0x3595e3c0 [ INVALID eol irq1 23 20 18 cnt0 resync 14 13 count=960 ]
[  497.252114] cx88[0]:   iq 1: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252121] cx88[0]:   iq 2: 0x3595eb40 [ arg #1 ]
[  497.252124] cx88[0]:   iq 3: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252132] cx88[0]:   iq 4: 0x3595d2c0 [ arg #1 ]
[  497.252135] cx88[0]:   iq 5: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252142] cx88[0]:   iq 6: 0x3595da40 [ arg #1 ]
[  497.252146] cx88[0]:   iq 7: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252153] cx88[0]:   iq 8: 0x3595c1c0 [ arg #1 ]
[  497.252156] cx88[0]:   iq 9: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252164] cx88[0]:   iq a: 0x3595c940 [ arg #1 ]
[  497.252167] cx88[0]:   iq b: 0x36aba900 [ INVALID eol irq2 23 21 19 cnt1 cnt0 resync 13 count=2304 ]
[  497.252178] cx88[0]:   iq c: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252186] cx88[0]:   iq d: 0x36abb080 [ arg #1 ]
[  497.252189] cx88[0]:   iq e: 0x80008200 [ sync resync count=512 ]
[  497.252195] cx88[0]:   iq f: 0x1c0003c0 [ write sol eol count=960 ]
[  497.252202] cx88[0]:   iq 10: 0x00180c00 [ arg #1 ]
[  497.252206] cx88[0]: fifo: 0x00180c00 -> 0x183400
[  497.252209] cx88[0]: ctrl: 0x00180400 -> 0x180460
[  497.252212] cx88[0]:   ptr1_reg: 0x001819f0
[  497.252216] cx88[0]:   ptr2_reg: 0x00180478
[  497.252219] cx88[0]:   cnt1_reg: 0x00000065
[  497.252223] cx88[0]:   cnt2_reg: 0x00000000
[  497.252233] cx88[0]/0: [f5bdf900/1] timeout - dma=0x35b50000
[  497.252237] cx88[0]/0: [f5bdf240/2] timeout - dma=0x35bc2000
[  497.252241] cx88[0]/0: [f5bdf6c0/3] timeout - dma=0x36a90000
[  497.252245] cx88[0]/0: [f5bdf9c0/4] timeout - dma=0x36b66000
[  497.252249] cx88[0]/0: [f5bdfa80/0] timeout - dma=0x35a0e000

```Any idea what these mean?

I'm wondering if it has something to do with all PCI slots being taken. 

AGP: 7800GS
PCI 1: Audigy 2 sound card
PCI 2: Gigabit NIC
PCI 3: ASUS PVR 416
PCI 4: ASUS 7134
PCI 5: Rocketraid 1740 controller



Any information appreciated.

---

