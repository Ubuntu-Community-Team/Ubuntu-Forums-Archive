---
title: "Slow DVD-Playback"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by Mauleye on 2005-10-25
Hi all

I've got some problems with dvd-playback on Breezy: Totem needs 20 secs to play 3 secs of the dvd ... OKOK I know what you wanna say: "DMA activated?" - answer is yes - as far as I can say.

hdparm -i /dev/hda outputs the following
```

/dev/hda:

 Model=PLEXTOR DVD-ROM PX-116A2 0100, FwRev=1.00, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

```

hdparm -i /dev/hdc outputs the following:
```

/dev/hdc:

 Model=PLEXTOR DVDR PX-716A, FwRev=1.08, SerialNo=195491
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

```

As far as I know that means DMA is activated for both my optical drives.

Here's my /etc/modules:
```

amd74xx
lp
mousedev
psmouse
sbp2
sr_mod
nvidia

```

I had to add the amd74xx-thing to enable DMA - that's btw specific for AMD64/nForce4.

Hope some of you guys can say why I still have that really slow dvd-playback. Thanks.

---

### Post by tseliot on 2005-10-25
Please post the output of:

sudo hdparm -d /dev/hda

and

sudo hdparm -d /dev/hdc

---

### Post by Mauleye on 2005-10-26
```
/dev/hda:
 using_dma    =  1 (on)
```

and

```
/dev/hdc:
 using_dma    =  1 (on)
```

---

### Post by tseliot on 2005-10-26
Another thing:

Open System Monitor (make sure you haven't any other application running) and post the percentage the CPU usage (you can find it under "Resources")

---

