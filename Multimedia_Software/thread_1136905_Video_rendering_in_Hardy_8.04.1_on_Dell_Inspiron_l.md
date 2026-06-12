---
title: "Video rendering in Hardy 8.04.1 on Dell Inspiron laptop"
date: 2009-04-25
forum: Multimedia Software
---

### Post by Bob Hairgrove on 2009-04-25
What happened between Feisty and Hardy that would break video rendering? It was fine in all programs before; now, colors look grossly overexposed in xine, gxine and Totem. MPlayer movie player with video device set to gl2 is just about the only player that works all the time for me. Kino 1.3.3 works OK (mostly) when the video device is set to "GDK".

Also, Kino 1.3.3 has been crashing a lot lately. Another problem I have with Kino is with FX "Superimpose". The resulting video has patches (streaks) of green and colors are off. However, when I export the video to a new file, it looks OK in MPlayer.

This is on a Dell 1420 laptop. Output of lspci -vv for the video controller:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Dell Inspiron 1420
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at eff8 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+

```

Here is the output of xvinfo:

```
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Video Overlay"
    number of ports: 1
    port base: 84
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 12
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 65794)
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is -4)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 120)
      "XV_SATURATION" (range 0 to 1023)
              client settable attribute
              client gettable attribute (current value is 500)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_PIPE" (range -1 to 1)
              client settable attribute
              client gettable attribute (current value is -1)
      "XV_GAMMA0" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 526344)
      "XV_GAMMA1" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 1052688)
      "XV_GAMMA2" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 2105376)
      "XV_GAMMA3" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 4210752)
      "XV_GAMMA4" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 8421504)
      "XV_GAMMA5" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 12632256)
    maximum XvImage size: 1920 x 1088
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)

```

Thanks for any help!

---

### Post by Bob Hairgrove on 2009-04-25
bump...

---

### Post by Bob Hairgrove on 2009-04-25
bump...

---

