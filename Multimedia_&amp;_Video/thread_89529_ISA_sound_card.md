---
title: "ISA sound card"
date: 2005-11-12
forum: Multimedia &amp; Video
---

### Post by PhoenixP3K on 2005-11-12
I know this issue has been addressed before, I have been reading a lot on the forums and Wiki but I still can't make it work :(

I have this modem/soundcard combo on ISA, It's a "Crystal CS4237" design, I tryed to add it but it's not working. :confused: 

I've used modconf to add it, then alsaconf to configure it, no error messages. But in the end Ubuntu still tells me I have no sound card. I'm on Breezy with an old machine (PII-266Mhz, 128MB RAM, and a da*n ISA sound card).

If someone could help me out with this I'd sure learn a lot. Thank you.

---

### Post by az on 2005-11-12
What module are you using?  snd-cs4236?

Load it and then post the output of
dmesg

---

### Post by PhoenixP3K on 2005-11-13
See this is the weird thing, when I do *sudo modprobe snd-cs4236* I get *FATAL: Module snd_cs4236 not found.*

Now that module is supposed to be working because this is the chipset metionned on my ISA card:  [http://usa.aopen.com/products/modem/mp56.htm](http://usa.aopen.com/products/modem/mp56.htm)

Then I also tryed *sudo modconf* to make sure I did enable. So I browsed to **kernel/sound/oss**. I only found cs4232 and cs46xx in the list cs4232 did not want to work, and cs46xx can be added but the was still no sound.

dmesg output:
> 4082] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1803.631621] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1803.631657] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1803.695305] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1803.695343] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1805.663011] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1805.663048] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1810.358571] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1810.358607] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1810.458395] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1810.458431] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1810.692327] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1810.692363] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1810.761184] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1810.761220] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1810.855814] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1810.855849] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1810.967259] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1810.967295] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1811.027021] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1811.027057] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1811.126858] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1811.126893] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1818.426626] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1818.426663] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1818.557433] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1818.557468] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1818.628847] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1818.628883] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1818.744129] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1818.744165] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1819.221958] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1819.221995] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1819.368219] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1819.368255] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1819.609933] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1819.609969] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1819.732967] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1819.733004] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1819.835312] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1819.835349] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1819.977742] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1819.977778] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1822.912703] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1822.912739] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1823.059005] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1823.059040] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1823.122653] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1823.122690] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1823.222446] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1823.222482] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1828.258702] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1828.258738] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1829.055694] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1829.055731] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1831.146947] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1831.146984] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1831.780312] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1831.780348] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1832.463135] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1832.463172] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1833.471421] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1833.471457] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1833.627927] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1833.627963] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1833.789681] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1833.789717] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1833.953909] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1833.953946] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1834.193121] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1834.193156] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1834.442564] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1834.442601] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1835.206727] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1835.206764] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1836.129424] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1836.129460] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1836.853125] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1836.853163] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1837.257228] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1837.257265] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1837.403559] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1837.403595] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1837.498172] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1837.498209] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1837.594095] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1837.594132] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1842.348051] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1842.348089] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1842.424666] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1842.424702] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1843.459716] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1843.459753] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1843.559511] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1843.559547] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1843.634841] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1843.634878] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1843.730722] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1843.730758] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1848.690077] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1848.690114] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1849.146029] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1849.146065] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1849.484448] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1849.484485] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1849.599773] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1849.599810] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1849.717597] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1849.717633] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1849.798063] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1849.798099] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1849.939142] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1849.939179] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1850.066048] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1850.066084] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1850.199362] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1850.199398] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1850.314613] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1850.314649] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1850.409258] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1850.409295] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1850.540052] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1850.540089] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1850.781730] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1850.781766] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1850.943520] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1850.943557] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1851.889572] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1851.889609] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1852.028124] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1852.028161] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1852.107241] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1852.107277] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1852.191593] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1852.191630] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1852.286211] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1852.286247] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1852.370618] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1852.370654] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1856.041083] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1856.041119] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1856.125398] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1856.125434] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1856.227715] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1856.227751] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1856.319840] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1856.319875] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1856.426066] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1856.426103] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1856.506509] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1856.506545] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1856.616614] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1856.616651] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1856.697077] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1856.697112] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1860.785598] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1860.785635] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1860.916408] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1860.916444] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1861.599304] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1861.599340] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1861.730133] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1861.730170] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1876.849672] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1876.849709] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1877.935534] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1877.935573] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1878.738338] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1878.738374] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1878.822661] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1878.822697] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1878.932812] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1878.932849] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1878.997837] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1878.997872] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1879.115612] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 1879.115648] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1879.230915] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 1879.230951] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 1892.895757] ad1848/cs4248 codec driver Copyright (C) by Hannu Savolainen 1993-1996
[ 1892.899349] pnp: Device 01:01.00 activated.
[ 1892.899382] ad1848: PnP reports 'Magic MP56 3D Res 1.0 - D7' at i/o 0x534, irq 5, dma 1, 3
[ 1892.976099] cs4232: set synthio and synthirq to use the wavefront facilities.[ 1893.043312] cs4232: probe of 01:01.00 failed with error -16
[ 1893.043365] cs4232: Must set io, irq and dma.
[ 2100.497647] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[ 2100.497683] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 2100.961437] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[ 2100.961473] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.


---

### Post by az on 2005-11-13
snd-cs4236 is part of the stock kernel.  Are you sure it is not balking because there is already another sound module falsely loaded?  

lsmod

What version of Ubunt are you running?

uname -a

---

### Post by sb73542 on 2005-11-13
All ISA cards are **very** poorly supported on Ubuntu.  I have an IBM Thinkpad 600 that contains this soundcard, and it absolutely does not work to simply modprobe snd-cs4236.  You need to pass it a million irq and port parameters.  Search these forums for "modprobe snd-cs4236".  It is possible to make it work, but it's even more difficult than usual on Ubuntu.

---

### Post by zman58 on 2005-11-13
If you can avoid ISA adapters, you should. Use PCI adapters. I just picked up a great little 3D sound PCI card from Comp USA for $14.95. ISA cards do not provide automated interrupt management. You must manage the interrupts for those cards (jumpers and/or card setup). Even if you do get it working, you may have problems with interrupts.:???:

---

### Post by PhoenixP3K on 2005-11-13
Well, this is sure not encouraging one bit. Anyway I do understand how Linux should focus on being compatible with up-to-date material in order to still be in the big picture of things... 

As I said earlier it's an old machine and you can't get much out of it anyway. I'll keep Ubuntu on my newer machine (problem free :D) and see what happens.

(Perhaps I shouldn't quit that easy, but I might not be worth it after all, sorry for the inconvenience)

---

### Post by az on 2005-11-14
[QUOTE=PhoenixP3K]Well, this is sure not encouraging one bit. Anyway I do understand how Linux should focus on being compatible with up-to-date material in order to still be in the big picture of things... [/QUOTE]

The problem is with the architecture of the isa system.  Remeber that even Windows which has drivers written by the manufacturer can make your computer crash by probing the isa bus.  That is why support for probing the isa bus by the kernel cannot be implemented.

Perhaps, in this case, you can change some settings in your bios to reserve the IRQ used by your sound card to the isa bus (if your system has both pci and isa)?  Maybe that will help?

---

### Post by Huike on 2005-11-14
Just a thought, have you tried to reserve irq, io and dma for the isa card in the bios?

---

### Post by PhoenixP3K on 2005-11-14
I'm no where that advanced in the understanding of a computers architecture. Understanding to the electronics level, I'm not there yet :( 

Learning step by step... But I don't think beating the crap out of that ISA sound card might to be the right way.

Thanks for the help and the concern, truly thanks all of you.:rolleyes:

---

