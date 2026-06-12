---
title: "ATSC Tuner in KWorld PC120-U PCI Hybrid ATSC (17de:a134)"
date: 2010-11-24
forum: Multimedia Software
---

### Post by hoomanb on 2010-11-24
[I'm cross posting a message I've sent this to linux-media list. Either someone here might be able to help me, or I can post any response I get from that mailing list for reference.]

I've been trying to get the ATSC tuner in my KWorld PC120-U PCI Hybrid
ATSC (17de:a134)
to work with the latest v4l drivers from source (in Ubuntu).

Right now, everything [capture, analog, radio, even IR] works - except
the ATSC tuner (there is no
front-end device). But that's the one thing I need working :-(

Here's the output of lspci -nnvv
```

03:01.0 Multimedia controller [0480]: Philips Semiconductors
SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
Subsystem: KWorld Computer Co. Ltd. Device [17de:a134]
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 255 (63750ns min, 63750ns max)
Interrupt: pin A routed to IRQ 16
Region 0: Memory at fdaff000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: saa7134
Kernel modules: saa7134

```

This is the most similar card that I forced in saa7134-cards.c:
```

               .vendor       = PCI_VENDOR_ID_PHILIPS,
               .device       = PCI_DEVICE_ID_PHILIPS_SAA7133,
               .subvendor    = 0x17de,
               .subdevice    = 0xa134,
               .driver_data  = SAA7134_BOARD_MSI_TVATANYWHERE_PLUS,

```

The chips are : SAA7135HL/203 and TDA18271HDC2


Here's [the related portion of] my dmesg output:
```

[  110.370106] IR NEC protocol handler initialized
[  110.386675] IR RC5(x) protocol handler initialized
[  110.395994] IR RC6 protocol handler initialized
[  110.406738] IR JVC protocol handler initialized
[  110.425685] IR Sony protocol handler initialized
[  110.433223] saa7130/34: v4l2 driver version 0.2.16 loaded
[  110.433347] saa7134 0000:03:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  110.433366] saa7133[0]: found at 0000:03:01.0, rev: 209, irq: 16,
latency: 255, mmio: 0xfdaff000
[  110.433383] saa7133[0]: subsystem: 17de:a134, board: MSI
TV@Anywhere plus [card=82,autodetected]
[  110.433452] saa7133[0]: board init: gpio is 100100
[  110.584522] saa7133[0]: i2c eeprom 00: de 17 34 a1 ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584548] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584571] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584593] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584614] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584636] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584658] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584680] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584702] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584724] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584746] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584768] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584789] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584811] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584833] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.584855] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff
ff ff ff ff ff ff ff
[  110.648282] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[  110.728024] tda829x 1-004b: setting tuner address to 60
[  110.773659] tda18271 1-0060: creating new instance
[  110.820031] TDA18271HD/C2 detected @ 1-0060
[  112.152020] tda18271: performing RF tracking filter calibration
[  130.376040] tda18271: RF tracking filter calibration complete
[  130.432045] tda829x 1-004b: type set to tda8290+18271
[  135.376533] Registered IR keymap rc-msi-tvanywhere-plus
[  135.376804] input: i2c IR (MSI TV@nywhere Plus) as
/devices/virtual/rc/rc0/input5
[  135.376980] rc0: i2c IR (MSI TV@nywhere Plus) as /devices/virtual/rc/rc0
[  135.376990] ir-kbd-i2c: i2c IR (MSI TV@nywhere Plus) detected at
i2c-1/1-0030/ir0 [saa7133[0]]
[  135.464292] saa7133[0]: registered device video0 [v4l2]
[  135.464433] saa7133[0]: registered device vbi0
[  135.464590] saa7133[0]: registered device radio0
[  135.508921] saa7134 ALSA driver for DMA sound loaded
[  135.509024] saa7133[0]/alsa: saa7133[0] at 0xfdaff000 irq 16
registered as card -2
[  137.384030] tda18271_write_regs: [1-0060|M] ERROR: idx = 0x5, len =
1, i2c_transfer returned: -5
[  137.384044] tda18271_init: [1-0060|M] error -5 on line 831
[  137.384054] tda18271_tune: [1-0060|M] error -5 on line 909
[  137.384062] tda18271_set_analog_params: [1-0060|M] error -5 on line 1046
[  138.236061] tda18271_write_regs: [1-0060|M] ERROR: idx = 0x1d, len
= 1, i2c_transfer returned: -5

```

And here's the content of the .inf file from the Windows
driver:

```

; Copyright 2004, Philips Semiconductors GmbH

[Version]
signature="$CHICAGO$" ;all windows os
Class=MEDIA
ClassGUID={4d36e96c-e325-11ce-bfc1-08002be10318}
Provider=%PSH%
DriverVer=08/04/2010,1.403.10.804
CatalogFile=3xHybrid.cat
CatalogFile.NTx86   = 3xHybrid.cat
CatalogFile.NTAMD64 = 3xHybr64.cat

[Manufacturer]
%PSH%=Philips, NTx86, NTAMD64

[Philips]
%Hybrid.DeviceDescSilicon%  =3xHybridV.NTx86,PCI\VEN_1131&DEV_7130
%Hybrid.DeviceDescSilicon%  =3xHybridW.NTx86,PCI\VEN_1131&DEV_7134
%Hybrid.DeviceDescSilicon%  =3xHybrid.NTx86,PCI\VEN_1131&DEV_7133

%Hybrid.DeviceDescSilicon%
=3xHybridW.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712617DE
%Hybrid.DeviceDescSilicon%
=3xHybridW.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712717DE

%Hybrid.DeviceDescSilicon%
=3xHybridV.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712817DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712917DE

%Hybrid.DeviceDescSilicon%
=3xHybridW.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712317DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712417DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712517DE

%Hybrid.DeviceDescSilicon%
=3xHybridX.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridX.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridY.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712C17DE
%Hybrid.DeviceDescSilicon%
=3xHybridY1.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712D17DE
%Hybrid.DeviceDescSilicon%
=3xHybridZ.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_71A017DE

%Hybrid.DeviceDescSilicon%
=3xHybrid0.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_719017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid1.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_719517DE
%Hybrid.DeviceDescSilicon%
=3xHybrid2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid3.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13117DE
%Hybrid.DeviceDescSilicon%
=3xHybrid2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid3.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13117DE
%Hybrid.DeviceDescSilicon%
=3xHybrid4.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13217DE
%Hybrid.DeviceDescSilicon%
=3xHybrid5.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13317DE
%Hybrid.DeviceDescSilicon%
=3xHybrid4.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13217DE
%Hybrid.DeviceDescSilicon%
=3xHybrid5.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13317DE

%SVID_17DE&SSID_A135.DeviceDesc%
=3xHybrid2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13517DE
%SVID_17DE&SSID_A135.DeviceDesc%
=3xHybrid2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13517DE
%SVID_17DE&SSID_A134.DeviceDesc%
=3xHybrid4.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13417DE
%SVID_17DE&SSID_A134.DeviceDesc%
=3xHybrid4.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13417DE
%Hybrid.DeviceDescSilicon%
=3xHybrid6.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_D13517DE
%Hybrid.DeviceDescSilicon%
=3xHybrid7.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_B13517DE
%SVID_17DE&SSID_B136.DeviceDesc%
=3xHybrid7.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_B13617DE
%Hybrid.DeviceDescSilicon%
=3xHybrid8.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_719217DE

%Hybrid.DeviceDescSilicon%
=3xHybridW1.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712E17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW1.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712F17DE

%SVID_17DE&SSID_7140.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714017DE
%SVID_17DE&SSID_7140.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714017DE
%SVID_17DE&SSID_7141.DeviceDesc%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714117DE
%SVID_17DE&SSID_7141.DeviceDesc%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714117DE
%SVID_17DE&SSID_714C.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714C17DE
%SVID_17DE&SSID_714C.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714C17DE
%SVID_17DE&SSID_714D.DeviceDesc%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714D17DE
%SVID_17DE&SSID_714D.DeviceDesc%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714D17DE
%SVID_17DE&SSID_714E.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714E17DE
%SVID_17DE&SSID_714E.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714E17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW4.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW4.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW5.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714317DE
%Hybrid.DeviceDescSilicon%
=3xHybridW5.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714317DE



;******** Subvendors
%Hybrid.DeviceDescSilicon%
=3xHybridA.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713117DE
%Hybrid.DeviceDescSilicon%
=3xHybridA.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713517DE
%Hybrid.DeviceDescSilicon%
=3xHybridB.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713617DE
%Hybrid.DeviceDescSilicon%
=3xHybridC.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713717DE
%Hybrid.DeviceDescSilicon%
=3xHybridD.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713817DE
%Hybrid.DeviceDescSilicon%
=3xHybridE.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_720017DE
%Hybrid.DeviceDescSilicon%
=3xHybridF.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713917DE
%Hybrid.DeviceDescSilicon%
=3xHybridG.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridH.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_720117DE
%Hybrid.DeviceDescSilicon%
=3xHybridI.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_720217DE
%Hybrid.DeviceDescSilicon%
=3xHybridJ.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_720317DE
%Hybrid.DeviceDescSilicon%
=3xHybridK.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725017DE
%Hybrid.DeviceDescSilicon%
=3xHybridL.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_723017DE
%Hybrid.DeviceDescSilicon%
=3xHybridM.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725117DE
%Hybrid.DeviceDescSilicon%
=3xHybridN.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725217DE
%Hybrid.DeviceDescSilicon%
=3xHybridO.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_735017DE
%Hybrid.DeviceDescSilicon%
=3xHybridP.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_735117DE
%Hybrid.DeviceDescSilicon%
=3xHybridO.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_735217DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725317DE
%Hybrid.DeviceDescSilicon%
=3xHybridR.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725417DE
%Hybrid.DeviceDescSilicon%
=3xHybridS.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725517DE
%Hybrid.DeviceDescSilicon%
=3xHybridT.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_730017DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725617DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ1.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725717DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725817DE
%Hybrid.DeviceDescSilicon%
=3xHybridU.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_730117DE
%Hybrid.DeviceDescSilicon%
=3xHybridU.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_730217DE
%Hybrid.DeviceDescSilicon%
=3xHybridK1.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_710017DE
%Hybrid.DeviceDescSilicon%
=3xHybridK2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_710117DE
;---> 32 BIT SUPPORT <---
[Philips.NTx86]
%Hybrid.DeviceDescSilicon%  =3xHybridV.NTx86,PCI\VEN_1131&DEV_7130
%Hybrid.DeviceDescSilicon%  =3xHybridW.NTx86,PCI\VEN_1131&DEV_7134
%Hybrid.DeviceDescSilicon%  =3xHybrid.NTx86,PCI\VEN_1131&DEV_7133

%Hybrid.DeviceDescSilicon%
=3xHybridW.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712617DE
%Hybrid.DeviceDescSilicon%
=3xHybridW.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712717DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712817DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712917DE

%Hybrid.DeviceDescSilicon%
=3xHybridW.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712317DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712417DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712517DE

%Hybrid.DeviceDescSilicon%
=3xHybridX.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridX.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridY.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712C17DE
%Hybrid.DeviceDescSilicon%
=3xHybridY1.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712D17DE
%Hybrid.DeviceDescSilicon%
=3xHybridZ.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_71A017DE

%Hybrid.DeviceDescSilicon%
=3xHybrid0.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_719017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid1.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_719517DE
%Hybrid.DeviceDescSilicon%
=3xHybrid2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid3.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13117DE
%Hybrid.DeviceDescSilicon%
=3xHybrid2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid3.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13117DE
%Hybrid.DeviceDescSilicon%
=3xHybrid4.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13217DE
%Hybrid.DeviceDescSilicon%
=3xHybrid5.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13317DE
%Hybrid.DeviceDescSilicon%
=3xHybrid4.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13217DE
%Hybrid.DeviceDescSilicon%
=3xHybrid5.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13317DE
%SVID_17DE&SSID_A135.DeviceDesc%
=3xHybrid2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13517DE
%SVID_17DE&SSID_A135.DeviceDesc%
=3xHybrid2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13517DE
%SVID_17DE&SSID_A134.DeviceDesc%
=3xHybrid4.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_A13417DE
%SVID_17DE&SSID_A134.DeviceDesc%
=3xHybrid4.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_A13417DE
%Hybrid.DeviceDescSilicon%
=3xHybrid6.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_D13517DE
%Hybrid.DeviceDescSilicon%
=3xHybrid7.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_B13517DE
%SVID_17DE&SSID_B136.DeviceDesc%
=3xHybrid7.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_B13617DE
%Hybrid.DeviceDescSilicon%
=3xHybrid8.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_719217DE

%Hybrid.DeviceDescSilicon%
=3xHybridW1.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_712E17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW1.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_712F17DE

%SVID_17DE&SSID_7140.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714017DE
%SVID_17DE&SSID_7140.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714017DE
%SVID_17DE&SSID_7141.DeviceDesc%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714117DE
%SVID_17DE&SSID_7141.DeviceDesc%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714117DE
%SVID_17DE&SSID_714C.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714C17DE
%SVID_17DE&SSID_714C.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714C17DE
%SVID_17DE&SSID_714D.DeviceDesc%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714D17DE
%SVID_17DE&SSID_714D.DeviceDesc%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714D17DE
%SVID_17DE&SSID_714E.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714E17DE
%SVID_17DE&SSID_714E.DeviceDesc%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714E17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW2.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW3.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW4.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW4.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW5.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_714317DE
%Hybrid.DeviceDescSilicon%
=3xHybridW5.NTx86,PCI\VEN_1131&DEV_7134&SUBSYS_714317DE



;******** Subvendors
%Hybrid.DeviceDescSilicon%
=3xHybridA.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713117DE
%Hybrid.DeviceDescSilicon%
=3xHybridA.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713517DE
%Hybrid.DeviceDescSilicon%
=3xHybridB.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713617DE
%Hybrid.DeviceDescSilicon%
=3xHybridC.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713717DE
%Hybrid.DeviceDescSilicon%
=3xHybridD.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713817DE
%Hybrid.DeviceDescSilicon%
=3xHybridE.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_720017DE
%Hybrid.DeviceDescSilicon%
=3xHybridF.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713917DE
%Hybrid.DeviceDescSilicon%
=3xHybridG.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_713A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridH.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_720117DE
%Hybrid.DeviceDescSilicon%
=3xHybridI.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_720217DE
%Hybrid.DeviceDescSilicon%
=3xHybridJ.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_720317DE
%Hybrid.DeviceDescSilicon%
=3xHybridK.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725017DE
%Hybrid.DeviceDescSilicon%
=3xHybridL.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_723017DE
%Hybrid.DeviceDescSilicon%
=3xHybridM.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725117DE
%Hybrid.DeviceDescSilicon%
=3xHybridN.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725217DE
%Hybrid.DeviceDescSilicon%
=3xHybridO.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_735017DE
%Hybrid.DeviceDescSilicon%
=3xHybridP.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_735117DE
%Hybrid.DeviceDescSilicon%
=3xHybridO.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_735217DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725317DE
%Hybrid.DeviceDescSilicon%
=3xHybridR.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725417DE
%Hybrid.DeviceDescSilicon%
=3xHybridS.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725517DE
%Hybrid.DeviceDescSilicon%
=3xHybridT.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_730017DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725617DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ1.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725717DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_725817DE
%Hybrid.DeviceDescSilicon%
=3xHybridU.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_730117DE
%Hybrid.DeviceDescSilicon%
=3xHybridU.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_730217DE
%Hybrid.DeviceDescSilicon%
=3xHybridK1.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_710017DE
%Hybrid.DeviceDescSilicon%
=3xHybridK2.NTx86,PCI\VEN_1131&DEV_7133&SUBSYS_710117DE
;---> 64 BIT SUPPORT <---
[Philips.NTAMD64]
%Hybrid.DeviceDescSilicon%  =3xHybridV.NTAMD64,PCI\VEN_1131&DEV_7130
%Hybrid.DeviceDescSilicon%  =3xHybridW.NTAMD64,PCI\VEN_1131&DEV_7134
%Hybrid.DeviceDescSilicon%  =3xHybrid.NTAMD64,PCI\VEN_1131&DEV_7133

%Hybrid.DeviceDescSilicon%
=3xHybridW.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_712617DE
%Hybrid.DeviceDescSilicon%
=3xHybridW.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_712717DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_712817DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_712917DE

%Hybrid.DeviceDescSilicon%
=3xHybridW.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_712217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_712317DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_712417DE
%Hybrid.DeviceDescSilicon%
=3xHybridV.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_712517DE

%Hybrid.DeviceDescSilicon%
=3xHybridX.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_712A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridX.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_712B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridY.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_712C17DE
%Hybrid.DeviceDescSilicon%
=3xHybridY1.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_712D17DE
%Hybrid.DeviceDescSilicon%
=3xHybridZ.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_71A017DE

%Hybrid.DeviceDescSilicon%
=3xHybrid0.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_719017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid1.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_719517DE
%Hybrid.DeviceDescSilicon%
=3xHybrid2.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_A13017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid3.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_A13117DE
%Hybrid.DeviceDescSilicon%
=3xHybrid2.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_A13017DE
%Hybrid.DeviceDescSilicon%
=3xHybrid3.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_A13117DE
%Hybrid.DeviceDescSilicon%
=3xHybrid4.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_A13217DE
%Hybrid.DeviceDescSilicon%
=3xHybrid5.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_A13317DE
%Hybrid.DeviceDescSilicon%
=3xHybrid4.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_A13217DE
%Hybrid.DeviceDescSilicon%
=3xHybrid5.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_A13317DE
%SVID_17DE&SSID_A135.DeviceDesc%
=3xHybrid2.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_A13517DE
%SVID_17DE&SSID_A135.DeviceDesc%
=3xHybrid2.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_A13517DE
%SVID_17DE&SSID_A134.DeviceDesc%
=3xHybrid4.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_A13417DE
%SVID_17DE&SSID_A134.DeviceDesc%
=3xHybrid4.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_A13417DE
%Hybrid.DeviceDescSilicon%
=3xHybrid6.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_D13517DE
%Hybrid.DeviceDescSilicon%
=3xHybrid7.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_B13517DE
%SVID_17DE&SSID_B136.DeviceDesc%
=3xHybrid7.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_B13617DE
%Hybrid.DeviceDescSilicon%
=3xHybrid8.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_719217DE



%Hybrid.DeviceDescSilicon%
=3xHybridW1.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_712E17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW1.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_712F17DE

%SVID_17DE&SSID_7140.DeviceDesc%
=3xHybridW2.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714017DE
%SVID_17DE&SSID_7140.DeviceDesc%
=3xHybridW2.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714017DE
%SVID_17DE&SSID_7141.DeviceDesc%
=3xHybridW3.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714117DE
%SVID_17DE&SSID_7141.DeviceDesc%
=3xHybridW3.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714117DE
%SVID_17DE&SSID_714C.DeviceDesc%
=3xHybridW2.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714C17DE
%SVID_17DE&SSID_714C.DeviceDesc%
=3xHybridW2.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714C17DE
%SVID_17DE&SSID_714D.DeviceDesc%
=3xHybridW3.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714D17DE
%SVID_17DE&SSID_714D.DeviceDesc%
=3xHybridW3.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714D17DE
%SVID_17DE&SSID_714E.DeviceDesc%
=3xHybridW2.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714E17DE
%SVID_17DE&SSID_714E.DeviceDesc%
=3xHybridW2.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714E17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW2.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW2.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW3.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW3.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714B17DE
%Hybrid.DeviceDescSilicon%
=3xHybridW4.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW4.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714217DE
%Hybrid.DeviceDescSilicon%
=3xHybridW5.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_714317DE
%Hybrid.DeviceDescSilicon%
=3xHybridW5.NTAMD64,PCI\VEN_1131&DEV_7134&SUBSYS_714317DE



;******** Subvendors
%Hybrid.DeviceDescSilicon%
=3xHybridA.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_713117DE
%Hybrid.DeviceDescSilicon%
=3xHybridA.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_713517DE
%Hybrid.DeviceDescSilicon%
=3xHybridB.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_713617DE
%Hybrid.DeviceDescSilicon%
=3xHybridC.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_713717DE
%Hybrid.DeviceDescSilicon%
=3xHybridD.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_713817DE
%Hybrid.DeviceDescSilicon%
=3xHybridE.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_720017DE
%Hybrid.DeviceDescSilicon%
=3xHybridF.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_713917DE
%Hybrid.DeviceDescSilicon%
=3xHybridG.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_713A17DE
%Hybrid.DeviceDescSilicon%
=3xHybridH.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_720117DE
%Hybrid.DeviceDescSilicon%
=3xHybridI.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_720217DE
%Hybrid.DeviceDescSilicon%
=3xHybridJ.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_720317DE
%Hybrid.DeviceDescSilicon%
=3xHybridK.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725017DE
%Hybrid.DeviceDescSilicon%
=3xHybridL.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_723017DE
%Hybrid.DeviceDescSilicon%
=3xHybridM.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725117DE
%Hybrid.DeviceDescSilicon%
=3xHybridN.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725217DE
%Hybrid.DeviceDescSilicon%
=3xHybridO.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_735017DE
%Hybrid.DeviceDescSilicon%
=3xHybridP.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_735117DE
%Hybrid.DeviceDescSilicon%
=3xHybridO.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_735217DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725317DE
%Hybrid.DeviceDescSilicon%
=3xHybridR.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725417DE
%Hybrid.DeviceDescSilicon%
=3xHybridS.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725517DE
%Hybrid.DeviceDescSilicon%
=3xHybridT.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_730017DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725617DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ1.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725717DE
%Hybrid.DeviceDescSilicon%
=3xHybridQ2.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_725717DE
%Hybrid.DeviceDescSilicon%
=3xHybridU.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_730117DE
%Hybrid.DeviceDescSilicon%
=3xHybridU.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_730217DE

%Hybrid.DeviceDescSilicon%
=3xHybridK1.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_710017DE
%Hybrid.DeviceDescSilicon%
=3xHybridK2.NTAMD64,PCI\VEN_1131&DEV_7133&SUBSYS_710117DE

[DestinationDirs]
SectionX32.CopyDll.NTx86      = 11
SectionX64.CopyDll.NTAMD64    = 11
SectionX32.CopyDriver.NTx86   = 10,system32\drivers
SectionX64.CopyDriver.NTAMD64 = 10,system32\drivers

[SectionX32.CopyDll.NTx86]
34CoInstaller.dll

[SectionX64.CopyDll.NTAMD64]

[SectionX32.CopyDriver.NTx86]
3xHybrid.sys

[SectionX64.CopyDriver.NTAMD64]
3xHybr64.sys

[SourceDisksNames]
1 = %AVSTRM_INSTALLATION_DISK%,,

[SourceDisksFiles]
3xHybrid.sys           = 1
3xHybr64.sys           = 1
34CoInstaller.dll      = 1


;
;*** initialization and registry entries
;

[3xHybrid.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridA.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridB.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridC.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridD.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridE.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridF.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridG.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridH.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridI.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridJ.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridK.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridK1.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridK2.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86


[3xHybridL.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridM.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridN.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridO.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridP.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridQ.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridQ1.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridQ2.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86
[3xHybridR.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridS.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridT.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridU.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridV.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridW.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridW1.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridW2.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridW3.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridW4.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridW5.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86
[3xHybridX.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridY.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridY1.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybridZ.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid0.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid1.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid2.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid3.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid4.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid5.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid6.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid6.NTx86.CoInstallers]
CopyFiles = SectionX32.CopyDll.NTx86
AddReg = SectionX32.DllAddReg.NTx86

[3xHybrid.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridA.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridB.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridC.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridD.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridE.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridF.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridG.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridH.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridI.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridJ.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridK.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridK1.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridK2.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64


[3xHybridL.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridM.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridN.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridO.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridP.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridQ.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridQ1.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridQ2.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64
[3xHybridR.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridS.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridT.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridU.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridV.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridW.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridW1.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridW2.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridW3.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridW4.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridW5.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridX.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridY.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridY1.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybridZ.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybrid0.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64


[3xHybrid1.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybrid2.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybrid3.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybrid4.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybrid5.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybrid6.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybrid7.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[3xHybrid8.NTAMD64.CoInstallers]
CopyFiles = SectionX64.CopyDll.NTAMD64
AddReg = SectionX64.DllAddReg.NTAMD64

[SectionX32.DllAddReg.NTx86]
HKR,,CoInstallers32,0x00010000,"34CoInstaller.dll, CoInstallerEntry"

[SectionX64.DllAddReg.NTAMD64]

[3xHybrid.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridB.AddReg, Common.AddReg,
Autodetect.AddReg, VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridA.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridA.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridB.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridB.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridC.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridC.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridD.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridD.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridE.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridE.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridF.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridF.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridG.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridG.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridH.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridH.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridI.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridI.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridJ.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridJ.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridK.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridK.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridK1.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridK1.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridK2.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridK2.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86


[3xHybridL.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridL.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridM.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridM.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridN.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridN.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridO.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridO.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg

[3xHybridP.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridP.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridQ.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridQ.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridQ1.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridQ1.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridQ2.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridQ2.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86
[3xHybridR.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridR.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridS.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridS.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridT.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridT.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridU.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridU.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridV.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridV.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridW.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridW.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridW1.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridW1.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridW2.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridW2.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridW3.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridW3.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridW4.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridW4.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridW5.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridW5.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridX.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridX.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridY.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridY.AddReg, Common.AddReg,
Video3DYCDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridY1.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridY1.AddReg, Common.AddReg,
Video3DYCDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybridZ.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybridZ.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybrid0.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid0.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybrid1.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid1.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybrid2.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid2.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybrid3.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid3.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybrid4.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid4.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybrid5.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid5.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86


[3xHybrid6.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid6.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybrid7.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid7.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86

[3xHybrid8.NTx86]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX32.CopyDriver.NTx86, SectionX32.CopyDll.NTx86
AddReg=3xHybrid.AddReg.NTx86, 3xHybrid8.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX32.Register.NTx86


[3xHybrid.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridA.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridB.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridC.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridD.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridE.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridF.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridG.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridH.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridI.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridJ.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridK.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridK1.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridK2.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall


[3xHybridL.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridM.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridN.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridO.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridP.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridQ.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridQ1.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridQ2.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridR.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridS.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridT.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridU.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridV.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridW.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridW1.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridW2.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridW3.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridW4.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridW5.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridX.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridY.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridY1.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybridZ.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid0.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall


[3xHybrid1.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid2.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid3.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid4.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid5.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid6.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid7.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid8.NTx86.Services]
AddService=%SERVICE_NAME_X32%, 0x00000002, 3xHybrid32.ServiceInstall

[3xHybrid.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridB.AddReg, Common.AddReg,
Autodetect.AddReg, VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridA.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridA.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridB.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridB.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridC.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridC.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridD.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridD.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridE.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridE.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridF.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridF.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridG.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridG.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridH.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridH.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridI.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridI.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridJ.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridJ.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridK.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridK.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridK1.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridK1.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridK2.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridK2.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64


[3xHybridL.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridL.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridM.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridM.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridN.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridN.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridO.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridO.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg

[3xHybridP.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridP.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridQ.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridQ.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridQ1.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridQ1.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridQ2.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridQ2.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64
[3xHybridR.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridR.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridS.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridS.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridT.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridT.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridU.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridU.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridV.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridV.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridW.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridW.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridW1.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridW1.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridW2.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridW2.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridW3.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridW3.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridW4.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridW4.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridW5.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridW5.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridX.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridX.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridY.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridY.AddReg, Common.AddReg,
Video3DYCDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridY1.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridY1.AddReg, Common.AddReg,
Video3DYCDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybridZ.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybridZ.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid0.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid0.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid1.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid1.AddReg, Common.AddReg,
VideoDec.AddReg, CanAudio.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid2.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid2.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid3.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid3.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid4.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid4.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid5.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid5.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid6.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid6.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid7.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid7.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid8.NTAMD64]
Include=ks.inf, wdmaudio.inf, kscaptur.inf, bda.inf
Needs=KS.Registration.NT, WDMAUDIO.Registration.NT,
KSCAPTUR.Registration.NT, BDA.Installation.NT
CopyFiles     = SectionX64.CopyDriver.NTAMD64, SectionX64.CopyDll.NTAMD64
AddReg=3xHybrid.AddReg.NTAMD64, 3xHybrid8.AddReg, Common.AddReg,
VideoDec.AddReg, SiliconAudioA.AddReg
RegisterDlls  = SectionX64.Register.NTAMD64

[3xHybrid.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridA.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridB.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridC.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridD.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridE.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridF.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridG.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridH.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridI.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridJ.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridK.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridK1.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridK2.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall


[3xHybridL.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridM.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridN.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridO.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridP.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridQ.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridQ1.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridQ2.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridR.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridS.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridT.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridU.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridV.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridW.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridW1.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridW2.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridW3.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridW4.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridW5.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridX.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridY.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridY1.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybridZ.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid0.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid1.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid2.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid3.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid4.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid5.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid6.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid7.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[3xHybrid8.NTAMD64.Services]
AddService=%SERVICE_NAME_X64%, 0x00000002, 3xHybrid64.ServiceInstall

[SectionX32.Register.NTx86]
11,,34CoInstaller.dll,1 ;FLG_REGSVR_DLLREGISTER


[SectionX64.Register.NTAMD64]


[3xHybrid32.ServiceInstall]
DisplayName=%DISPLAY_NAME%
Description=%SERVICE_DESCRIPTION%
ServiceType=%SERVICE_KERNEL_DRIVER%
StartType=%SERVICE_DEMAND_START%
ErrorControl=%SERVICE_ERROR_IGNORE%
ServiceBinary=%12%\3xHybrid.sys
; [StartName=driver-object-name]
; [AddReg=add-registry-section[, add-registry-section] ...]
; [DelReg=del-registry-section[, del-registry-section] ...]
; [BitReg=bit-registry-section[,bit-registry-section] ...]
; [LoadOrderGroup=load-order-group-name]
; [Dependencies=depend-on-item-name[,depend-on-item-name]...]

[3xHybrid64.ServiceInstall]
DisplayName=%DISPLAY_NAME%
Description=%SERVICE_DESCRIPTION%
ServiceType=%SERVICE_KERNEL_DRIVER%
StartType=%SERVICE_DEMAND_START%
ErrorControl=%SERVICE_ERROR_IGNORE%
ServiceBinary=%12%\3xHybr64.sys

[3xHybrid.AddReg.NTx86]
HKR,,DevLoader,,*NTKERN
HKR,,NTMPDriver,,3xHybrid.sys

; audio capture registry entries

HKR,,AssociatedFilters,,"wdmaud,swmidi,redbook"
HKR,,Driver,,3xHybrid.SYS

HKR,Drivers,SubClasses,,"wave,mixer"

HKR,Drivers\wave\wdmaud.drv,Driver,,wdmaud.drv
HKR,Drivers\mixer\wdmaud.drv,Driver,,wdmaud.drv
HKR,Drivers\wave\wdmaud.drv,Description,,"Philips Audio Capture Device"
HKR,Drivers\mixer\wdmaud.drv,Description,,"Philips Audio Capture Device"


; Setting FM radio of the Silicon tuner via SIF (GPIO 21 in use/ 5.5MHz)
HKR, "Audio", "FM Radio IF",0x00010001,0x729555

; Enable MCE
;HKR, "Parameters", "MCE",0x00010001,0x01
; add audio input and output pinnames
HKR, "Parameters", "Syncronization disabled",0x00010001,0x0

; under MCE, IgnoreDVBParameter=1, prevents the driver to use the
DShow DVB properties.
; -1 is used instead
HKR, "Parameters", "IgnoreDVBParameter",0x00010001,0x00

; under MCE, AutoRemove60HzStd fixes the 1st run problem with analog
multi standard tuner
; like the TDA8275A. In countries with 50Hz formats, 60Hz formats are
beeing removed
HKR, "Parameters", "AutoRemove60HzStd",0x00010001,0x01
HKR, "Parameters","Prefix",,%PHILIPS_CUSTOM_TUNERNAME%
HKR, "Parameters", "SmallXBar",0x00010001,0x01
HKR, "Parameters", "TDA8275A_BlankVideo",0x00010001,0x01
HKR, "Parameters", "TDA8275A_UseTuningThread",0x00010001,0x00
HKR, "Parameters", "GetRegATSCModulationType",0x00010001,0x00
HKR, "Parameters", "ATSCDemodulatedMode",0x00010001,0x17




HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_ANLG_AUDIO_IN_PIN%,"Name",,"Analog
Audioinput"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_ANLG_AUDIO_OUT_PIN%,"Name",,"Audio"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_ANLG_VIDEO_ITU_PIN%,"Name",,"Analog
ITU Video"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_ANLG_AUDIO_I2S_PIN%,"Name",,"I2S
Audio"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_MPEG_AES_PIN%,"Name",,"MPEG
Audio ES"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_MPEG_VES_PIN%,"Name",,"MPEG
Video ES"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_MPEG_PS_PIN%,"Name",,
"MPEG2 Program"

[3xHybrid.AddReg.NTAMD64]
HKR,,DevLoader,,*NTKERN
HKR,,NTMPDriver,,3xHybr64.sys

; audio capture registry entries

HKR,,AssociatedFilters,,"wdmaud,swmidi,redbook"
HKR,,Driver,,3xHybr64.sys

HKR,Drivers,SubClasses,,"wave,mixer"

HKR,Drivers\wave\wdmaud.drv,Driver,,wdmaud.drv
HKR,Drivers\mixer\wdmaud.drv,Driver,,wdmaud.drv
HKR,Drivers\wave\wdmaud.drv,Description,,"Philips Audio Capture Device"
HKR,Drivers\mixer\wdmaud.drv,Description,,"Philips Audio Capture Device"


; Setting FM radio of the Silicon tuner via SIF (GPIO 21 in use/ 5.5MHz)
HKR, "Audio", "FM Radio IF",0x00010001,0x729555

; Enable MCE
;HKR, "Parameters", "MCE",0x00010001,0x01
; add audio input and output pinnames
HKR, "Parameters", "Syncronization disabled",0x00010001,0x0

; under MCE, IgnoreDVBParameter=1, prevents the driver to use the
DShow DVB properties.
; -1 is used instead
HKR, "Parameters", "IgnoreDVBParameter",0x00010001,0x00

; under MCE, AutoRemove60HzStd fixes the 1st run problem with analog
multi standard tuner
; like the TDA8275A. In countries with 50Hz formats, 60Hz formats are
beeing removed
HKR, "Parameters", "AutoRemove60HzStd",0x00010001,0x01
HKR, "Parameters","Prefix",,%PHILIPS_CUSTOM_TUNERNAME%
HKR, "Parameters", "SmallXBar",0x00010001,0x01
HKR, "Parameters", "TDA8275A_BlankVideo",0x00010001,0x01
HKR, "Parameters", "TDA8275A_UseTuningThread",0x00010001,0x00



HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_ANLG_AUDIO_IN_PIN%,"Name",,"Analog
Audioinput"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_ANLG_AUDIO_OUT_PIN%,"Name",,"Audio"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_ANLG_VIDEO_ITU_PIN%,"Name",,"Analog
ITU Video"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_ANLG_AUDIO_I2S_PIN%,"Name",,"I2S
Audio"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_MPEG_AES_PIN%,"Name",,"MPEG
Audio ES"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_MPEG_VES_PIN%,"Name",,"MPEG
Video ES"
HKLM,SYSTEM\CurrentControlSet\Control\MediaCategories\%VAMP_MPEG_PS_PIN%,"Name",,
"MPEG2 Program"

[Autodetect.AddReg]
HKR, "Parameters", "AutoDetect",0x00010001,0x01

[3xHybridA.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x14,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridB.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x22,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridC.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x14,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x20,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridD.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x14,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridE.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x1E,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridF.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x22,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x20,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridG.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x22,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridH.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x2B,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridI.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x1E,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x22,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridJ.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x2B,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x22,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridK.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridK1.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x90,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x9B,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridK2.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x90,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x04,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x9B,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data9",0x00010001,0x12,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1


[3xHybridL.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x02,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x50,0x00,0x00,0x00
HKR, "Parameters", "AnalogPath",0x00010001,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridM.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridN.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x22,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridO.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x18,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x86,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0xFF,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x55,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x55,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x55,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridP.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x18,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x86,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridQ.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Parameters", "DetPALN",0x00010001,1
HKR, "Decoder", "Auto Standard Detection",0x00010001,0


[3xHybridQ1.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x00,0x00,0x00,0x00
HKR, "Parameters", "CaptureCard",0x00010001,0x01
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,0

[3xHybridQ2.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
[3xHybridR.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridS.AddReg]
HKR, "Parameters", "Latency Timer",0x00010001,0x40
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x21,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x22,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridT.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x17,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x3A,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridU.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x17,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x38,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridV.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x04,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Audio", "I2S_OutputLevel",0x00010001,0xf

[3xHybridW.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x08,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Audio", "I2S_OutputLevel",0x00010001,0xf

[3xHybridW1.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x03,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Audio", "I2S_OutputLevel",0x00010001,0xf

[3xHybridW2.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x86,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x00,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Audio", "I2S_OutputLevel",0x00010001,0xf

[3xHybridW3.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x88,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x86,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x00,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Audio", "I2S_OutputLevel",0x00010001,0xf

[3xHybridW4.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x89,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x86,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x00,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Audio", "I2S_OutputLevel",0x00010001,0xf

[3xHybridW5.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x8A,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x86,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x00,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Audio", "I2S_OutputLevel",0x00010001,0xf

[3xHybridX.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x09,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridY.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x04,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC2,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridY1.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x0A,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x30,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybridZ.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x35,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x10,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x05,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0xD5,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x15,0x00,0x00,0x00
HKR, "Parameters", "Ctrl4052IC",0x00010001,0x1
HKR, "Parameters", "FMADCLevel",0x00010001,0x9
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[3xHybrid0.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x1C,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0xFF,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x1C,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x00,0x00,0x00,0x00
HKR, "Parameters", "CaptureCard",0x00010001,0x01
HKR, "Parameters", "ForceATV",0x00010001,0x01
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Parameters", "TDA8262_LNB_POWER_HIGH",0x00010001,0x01


[3xHybrid1.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x00,0x00,0x00,0x00
HKR, "Parameters", "CaptureCard",0x00010001,0x01
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,0

[3xHybrid2.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x40,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x07,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x71,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data9",0x00010001,0x12,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data10",0x00010001,0x0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data11",0x00010001,0x0E,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data12",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Parameters", "FMLockLevel",0x00010001,600000
HKR, "Parameters", "nPowerState",0x00010001,0
HKR, "Parameters", "DetPALN",0x00010001,1

[3xHybrid3.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x40,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x71,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data9",0x00010001,0x12,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data10",0x00010001,0x0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data11",0x00010001,0x0E,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Parameters", "FMLockLevel",0x00010001,600000
HKR, "Parameters", "nPowerState",0x00010001,0
HKR, "Parameters", "DetPALN",0x00010001,1

[3xHybrid4.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x8B,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x07,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x71,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data9",0x00010001,0x12,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data10",0x00010001,0x0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data11",0x00010001,0x0E,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data12",0x00010001,0x01,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Parameters", "FMLockLevel",0x00010001,600000
HKR, "Parameters", "nPowerState",0x00010001,0
HKR, "Parameters", "TDA8290_CHIPSET",0x00010001,1


[3xHybrid5.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x8B,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x71,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x15,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data9",0x00010001,0x12,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data10",0x00010001,0x0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data11",0x00010001,0x0E,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Parameters", "FMLockLevel",0x00010001,600000
HKR, "Parameters", "nPowerState",0x00010001,0
HKR, "Parameters", "TDA8290_CHIPSET",0x00010001,1

[3xHybrid6.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x8D,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x3A,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x05,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data9",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data10",0x00010001,0x12,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data11",0x00010001,0x0E,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Parameters", "DigTuner",0x00010001,1
HKR, "Parameters", "nPowerState",0x00010001,0
HKR, "Parameters", "DetPALN",0x00010001,1

[3xHybrid7.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x8F,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x96,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x20,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x06,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x32,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data7",0x00010001,0x50,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data8",0x00010001,0x05,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data9",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data10",0x00010001,0x12,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data11",0x00010001,0x0E,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "Parameters", "DigTuner",0x00010001,2
HKR, "Parameters", "nPowerState",0x00010001,0
HKR, "Parameters", "DetPALN",0x00010001,1

[3xHybrid8.AddReg]
HKR, "I2C Devices", "Device 0, Data1",0x00010001,0x2E,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data2",0x00010001,0xC0,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data3",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data4",0x00010001,0x1C,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data5",0x00010001,0x00,0x00,0x00,0x00
HKR, "I2C Devices", "Device 0, Data6",0x00010001,0x08,0x00,0x00,0x00
HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1

[VideoDec.AddReg]
HKR, "VideoDecoder", "Tuner Channel",0x00010001,1
HKR, "VideoDecoder", "CVBS Channel",0x00010001,3
HKR, "VideoDecoder", "SVHS Channel",0x00010001,8
HKR, "VideoDecoder", "FM Radio Channel",0x00010001,1

[Video3DYCDec.AddReg]
HKR, "VideoDecoder", "Tuner Channel",0x00010001,9
HKR, "VideoDecoder", "CVBS Channel",0x00010001,4
HKR, "VideoDecoder", "SVHS Channel",0x00010001,6
HKR, "VideoDecoder", "FM Radio Channel",0x00010001,9

[SiliconAudio.AddReg]
HKR, "AudioDecoder", "Tuner Channel",0x00010001,1
HKR, "AudioDecoder", "CVBS Channel",0x00010001,3
HKR, "AudioDecoder", "SVHS Channel",0x00010001,3
HKR, "AudioDecoder", "FM Radio Channel",0x00010001,1

[SiliconAudioA.AddReg]
HKR, "AudioDecoder", "Tuner Channel",0x00010001,1
HKR, "AudioDecoder", "CVBS Channel",0x00010001,2
HKR, "AudioDecoder", "SVHS Channel",0x00010001,2
HKR, "AudioDecoder", "FM Radio Channel",0x00010001,1

[CanAudio.AddReg]
HKR, "AudioDecoder", "Tuner Channel",0x00010001,1
HKR, "AudioDecoder", "CVBS Channel",0x00010001,2
HKR, "AudioDecoder", "SVHS Channel",0x00010001,2
HKR, "AudioDecoder", "FM Radio Channel",0x00010001,2

[Common.AddReg]
;HKR, "AudioDecoder", "Tuner Channel",0x00010001,1
;HKR, "AudioDecoder", "CVBS Channel",0x00010001,3
;HKR, "AudioDecoder", "SVHS Channel",0x00010001,3
;HKR, "AudioDecoder", "FM Radio Channel",0x00010001,1

; maps user setting to hardware video input
;HKR, "VideoDecoder", "Tuner Channel",0x00010001,1
;HKR, "VideoDecoder", "CVBS Channel",0x00010001,3
;HKR, "VideoDecoder", "SVHS Channel",0x00010001,8
;HKR, "VideoDecoder", "FM Radio Channel",0x00010001,1

; I2C Device settings
;HKR, "I2C Devices", "Number of I2C Devices",0x00010001,1
HKR, "I2C Devices", "Force Registry Settings",0x00010001,1

HKR,,PageOutWhenUnopened,3,0
HKR,,DontSuspendIfStreamsAreRunning,3,00


;
;*** strings, GUIDs and names
;

[Strings]

; Proxy GUIDs

KSProxy.CLSID   = "{17CCA71B-ECD7-11D0-B908-00A0C9223196}"
KSXBar.CLSID    = "{71F96460-78F3-11d0-A18C-00A0C9118956}"
KSTVAudio.CLSID = "{71F96462-78F3-11d0-A18C-00A0C9118956}"
KSTvTune.CLSID  = "{266EEE40-6C63-11cf-8A03-00AA006ECB65}"

; Category GUIDs

KSCATEGORY_CAPTURE                = "{65E8773D-8F56-11D0-A3B9-00A0C9223196}"
KSCATEGORY_VIDEO                  = "{6994AD05-93EF-11D0-A3CC-00A0C9223196}"
KSCATEGORY_AUDIO                  = "{6994AD04-93EF-11D0-A3CC-00A0C9223196}"

; Our Pin Name GUIDs

VAMP_ANLG_AUDIO_IN_PIN   = "{7BB284B9-714D-493d-A101-B1B028E782BD}"
VAMP_ANLG_AUDIO_OUT_PIN  = "{5582E657-E596-42b5-9DB3-541B27A2355F}"
VAMP_ANLG_AUDIO_I2S_PIN  = "{C2E46358-F032-4d88-B802-06B59D162730}"
VAMP_ANLG_VIDEO_ITU_PIN  = "{82631A2E-403C-4581-A4B0-EC173D004410}"

VAMP_MPEG_AES_PIN        = "{9DEC84B9-BCEF-4aac-997E-43EDD0A2D6C7}"
VAMP_MPEG_VES_PIN        = "{181CF87E-7741-47ba-8629-22347E03C64C}"
VAMP_MPEG_PS_PIN         = "{DDA87B83-65DB-4aec-82D0-79FBE67D2BB6}"

; Our Filter GUIDs

VAMP_ANLG_AUDIO_FILTER   = "{F3B951E7-8619-4ff3-91CA-03910E4BB900}"
VAMP_ANLG_CAP_FILTER     = "{BBEFB6C7-2FC4-4139-BB8B-A58BBA724000}"

; system defines

SERVICE_BOOT_START     = 0x0
SERVICE_SYSTEM_START   = 0x1
SERVICE_AUTO_START     = 0x2
SERVICE_DEMAND_START   = 0x3
SERVICE_DISABLED       = 0x4

SERVICE_KERNEL_DRIVER  = 0x1
SERVICE_ERROR_IGNORE   = 0x0
SERVICE_ERROR_NORMAL   = 0x1
SERVICE_ERROR_SEVERE   = 0x2
SERVICE_ERROR_CRITICAL = 0x3

FLG_REGSVR_DLLREGISTER = 0x00000001

;Our strings

PSH="Philips"
PHILIPS_CUSTOM_TUNERNAME      = "713x"
30Hybrid.DeviceDesc      = "Philips SAA7130, Hybrid Capture Device"
34Hybrid.DeviceDesc      = "Philips SAA7134, Hybrid Capture Device"
33Hybrid.DeviceDesc      = "Philips SAA7133/35, Hybrid Capture Device"
AVSTRM_INSTALLATION_DISK = "3xHybrid installation disk"
DISPLAY_NAME             = "3xHybrid service"
SERVICE_NAME_X32         = "3xHybrid"
SERVICE_NAME_X64         = "3xHybr64"
SERVICE_DESCRIPTION      = "Philips SAA713x BDA Capture Driver"
Hybrid.DeviceDescSilicon = "Philips SAA713X, Hybrid Capture Device"
SVID_17DE&SSID_7140.DeviceDesc ="PVR-TV PC165-A RDS"
SVID_17DE&SSID_7141.DeviceDesc ="PVR-TV PC165-A RDS"
SVID_17DE&SSID_714C.DeviceDesc ="PVR-TV PC165-A"
SVID_17DE&SSID_714D.DeviceDesc ="PVR-TV PC165-A"
SVID_17DE&SSID_714E.DeviceDesc ="PVR-TV PC155-A"
SVID_17DE&SSID_A134.DeviceDesc ="ATSC PC150-U"
SVID_17DE&SSID_A135.DeviceDesc ="ATSC PC150-U"
SVID_17DE&SSID_B136.DeviceDesc ="KW-PC135-AF"

```

I appreciate any help with this.

---

### Post by zaustin on 2011-05-11
Hi,

DId you ever get anywhere with this?  I have the Kworld PC150-U, but my lspci output is identical to the above.

Thanks,
-Z

---

### Post by hoomanb on 2011-05-11
The post title was a typo. I have the PC150-U.
I haven't got it working (thought I still have it). 
I bought the HDHomerun and it works fine.

---

### Post by Laytos on 2011-07-19
I have the PC-150U as well, I originally got it for my MythTV server. I was using firewire from an HD STB. Worked awesome!! But, unfortunately I moved and the new place didn't have HD cable, :(. So, I figured use a cable card. I found the Kworld PC-150U, figured yea, this would work. Well.... yea....

So, this is what I've found out, my dmesg and lspci are the same as you guys' btw. Since I was hitting a brick wall in trying to get it to work I started looking at previous versions and found that the PC-120U (pre-cursor) used the Conexant cx23880 from here: [http://linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://linuxtv.org/wiki/index.php/KWorld_ATSC_120) 

I am going to try using the Conexant driver and firmware and see where that gets me. Pretty much using the PC-120 instructions on installing. I'll let you know what I come up with...

---

### Post by Laytos on 2011-07-19
So, a new custom kernel and a few hours later... I realise that it's identifying itself as a Phillips SAA713x decoder... so there we go. I'm going back to the drawing board, please excuse me.

---

