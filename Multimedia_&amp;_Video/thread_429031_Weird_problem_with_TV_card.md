---
title: "Weird problem with TV card"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by medeshago on 2007-04-30
I had my Lifeview Flyvideo 2000 working, but i had to reinstall. Now it won't work. If i use tvtime and i set it to get the composite, i can see what's plugged in, but if i put it in cable, i get no signal at all (with a no frequency message). The card is recognized but i can't use it to see cable-tv. 
I used: 

sudo modprobe saa7134 card=3 tuner=2 gbuffers=4

That's the one that i'm supossed to use.

lspci -v -v:
```
01:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Unknown device 5169:0138
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 16 (4000ns min, 10000ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at fdeff000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
```

dmesg | grep saa1734:

```
[   31.242877] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input4
[   31.710396] saa7134 ALSA driver for DMA sound loaded
[  344.372105] saa7134 ALSA driver for DMA sound unloaded
[  360.075908] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input7
[  360.256841] saa7134 ALSA driver for DMA sound loaded
[ 1467.768937] saa7134 ALSA driver for DMA sound unloaded
[ 1515.320970] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input8
[ 1515.671392] saa7134 ALSA driver for DMA sound loaded
[ 1695.492157] saa7134 ALSA driver for DMA sound unloaded
[ 1699.206679] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input9
[ 1699.376319] saa7134 ALSA driver for DMA sound loaded
[ 1971.862358] saa7134 ALSA driver for DMA sound unloaded
[ 1974.135714] saa7134: `' invalid for parameter `tuner'
[ 1991.367962] tuner: Unknown parameter `saa7134'
[ 1997.049753] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input10
[ 1997.219318] saa7134 ALSA driver for DMA sound loaded
[ 1998.902738] saa7134 ALSA driver for DMA sound unloaded
[ 2001.840492] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input11
[ 2002.013368] saa7134 ALSA driver for DMA sound loaded
[ 2303.444485] saa7134 ALSA driver for DMA sound unloaded
[ 2305.521528] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input12
[ 2305.769024] saa7134 ALSA driver for DMA sound loaded
[ 2327.712416] saa7134 ALSA driver for DMA sound unloaded
[ 2334.335059] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input13
[ 2334.507854] saa7134 ALSA driver for DMA sound loaded
[ 2401.496420] saa7134 ALSA driver for DMA sound unloaded
[ 2414.332484] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input14
[ 2414.505309] saa7134 ALSA driver for DMA sound loaded
[ 2423.046538] saa7134 ALSA driver for DMA sound unloaded
[ 2509.055617] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input15
[ 2509.245997] saa7134 ALSA driver for DMA sound loaded
[ 2529.732768] saa7134 ALSA driver for DMA sound unloaded
[ 2532.395823] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input16
[ 2532.584620] saa7134 ALSA driver for DMA sound loaded
[ 3662.961908] saa7134 ALSA driver for DMA sound unloaded
[ 3671.192314] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input17
[ 3671.479580] saa7134 ALSA driver for DMA sound loaded
[ 3815.554670] saa7134 ALSA driver for DMA sound unloaded
[ 3825.695541] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input18
[ 3825.864226] saa7134 ALSA driver for DMA sound loaded
[ 4193.644695] saa7134 ALSA driver for DMA sound unloaded
[ 4198.055762] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input19
[ 4198.224615] saa7134 ALSA driver for DMA sound loaded
[ 4273.700020] saa7134 ALSA driver for DMA sound unloaded
[ 4275.849523] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input20
[ 4276.109349] saa7134 ALSA driver for DMA sound loaded
[ 5187.353949] saa7134 ALSA driver for DMA sound unloaded
[ 5197.599414] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input21
[ 5197.851994] saa7134 ALSA driver for DMA sound loaded
[ 6022.195931] saa7134 ALSA driver for DMA sound unloaded
[ 6026.994235] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input22
[ 6027.226837] saa7134 ALSA driver for DMA sound loaded
[ 7255.797753] saa7134 ALSA driver for DMA sound unloaded
[ 7264.808559] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input23
[ 7265.162824] saa7134 ALSA driver for DMA sound loaded
[ 8415.152986] saa7134 ALSA driver for DMA sound unloaded
[ 8427.418093] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input24
[ 8427.713251] saa7134 ALSA driver for DMA sound loaded
[ 9572.441676] saa7134 ALSA driver for DMA sound unloaded
[ 9579.484805] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input25
[ 9579.742311] saa7134 ALSA driver for DMA sound loaded
[11635.035710] saa7134 ALSA driver for DMA sound unloaded
[11644.043063] input: saa7134 IR (LifeView/Typhoon Fl as /class/input/input26
[11644.501136] saa7134 ALSA driver for DMA sound loaded
```

---

