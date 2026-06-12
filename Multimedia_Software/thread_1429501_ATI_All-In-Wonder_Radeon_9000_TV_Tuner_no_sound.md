---
title: "ATI All-In-Wonder Radeon 9000 TV Tuner no sound"
date: 2010-03-14
forum: Multimedia Software
---

### Post by pumuckly on 2010-03-14
Hi,

I have an ATI All-In-Wonder 9000 AGP4x video card with TV tuner function. I following the description on [http://ubuntuforums.org/showthread.php?t=46496](http://ubuntuforums.org/showthread.php?t=46496) where I found a how-to for enabling TV tuner.

The tuner works in xawtv and avview but without sound. I plugged the cable in from tuner to my sound card and try to increase volume and/or enable mute on/off but nothing to hear.
The sound card line-in input works correctly, because when I attaching my MP3 player I hear sound over the sound card.

I think maybe have a register accessing/writing error which handle the TV Tuner sound chips to turn on/off.
(the tuner works correctly in Windows XP).

I'm using Ubuntu 8.04.4 LTS with x86_64 (amd64) actually.

The lspci output for Video Card:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
```

In original /etc/X11/xorg.conf I append the Device with two Options:

```
Section "Device"
    Identifier      "Configured Video Device"
    Option          "AGPFastWrite"  "1"
    Option          "UseFBDev"      "true"
EndSection

```

Xorg.log output (only for ATI functions) to determine tuner chipsets:
```
(==) AIGLX enabled
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9000/PRO If (AGP/PCI) found
(II) RADEON(0): MMIO registers at 0x00000000fe9e0000: size 64KB
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "AGPFastWrite" "1"
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) RADEON(0): initializing int10
(WW) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9000/PRO If (AGP/PCI)" (ChipID = 0x4966)
(--) RADEON(0): Linear framebuffer at 0x00000000f0000000
(--) RADEON(0): BIOS at 0xfe9c0000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Default TV standard: PAL
(==) RADEON(0): Using XAA acceleration architecture
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(==) RADEON(0): Write-combining range (0xf0000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): Using R200 i2c bus access method
(II) RADEON(0): I2C bus "Radeon multimedia bus" initialized.
(II) Loading sub module "fi1236"
(II) LoadModule: "fi1236"
(II) Loading /usr/lib/xorg/modules/multimedia//fi1236_drv.so
(II) Module fi1236: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): I2C device "Radeon multimedia bus:FI12xx Tuner" registered at address 0xC6.
(II) RADEON(0): Detected Philips FI1216ME (or compatible) device at 0xc6
(II) Loading sub module "tda9885"
(II) LoadModule: "tda9885"
(II) Loading /usr/lib/xorg/modules/multimedia//tda9885_drv.so
(II) Module tda9885: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): I2C device "Radeon multimedia bus:TDA9885 Alignment-free IF-PLL" registered at address 0x86.
(II) Loading sub module "uda1380"
(II) LoadModule: "uda1380"
(II) Loading /usr/lib/xorg/modules/multimedia//uda1380_drv.so
(II) Module uda1380: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): I2C device "Radeon multimedia bus:UDA1380 Stereo audion coder-decoder" registered at address 0x30.
(II) RADEON(0): UDA1380 stereo coder-decoder detected
(II) RADEON(0): UDA1380 initialized
(II) Loading sub module "msp3430"
(II) LoadModule: "msp3430"
(II) Loading /usr/lib/xorg/modules/multimedia//msp3430_drv.so
(II) Module msp3430: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): No response from device 0 on VIP bus
(II) RADEON(0): No response from device 1 on VIP bus
(II) RADEON(0): Device 2 on VIP bus ids as 0x4d4a1002
(II) RADEON(0): No response from device 3 on VIP bus
(II) RADEON(0): Detected Rage Theatre as device 2 on VIP bus with id 0x4d4a1002
(II) RADEON(0): Detected Rage Theatre revision 00000001
(II) RADEON(0): video decoder type is 0x6978 (BIOS value) versus 0x6978 (current PLL setting)
(II) RADEON(0): Tuner is on port 0
(II) RADEON(0): Composite connector is port 1
(II) RADEON(0): SVideo connector is port 5
(II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=1, svideo=5
(II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=1, svideo=5
(II) RADEON(0): video decoder type used: 0x0006
(II) RADEON(0): Going to load the corresponding theatre module
(II) Loading sub module "theatre200"
(II) LoadModule: "theatre200"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre200_drv.so
(II) Module theatre200: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): Microcode: Use default microcode path: /usr/lib/xorg/modules/multimedia/rt2_pmem.bin
(II) RADEON(0): Microcode: Use default microcode type: BINARY
(II) RADEON(0): Microcode: device_id: 4d4a
(II) RADEON(0): Microcode: vendor_id: 1002
(II) RADEON(0): Microcode: rev_id: 1f
(II) RADEON(0): Microcode: num_seg: 4
(II) RADEON(0): Microcode: dsp_init OK
(II) RADEON(0): Microcode: dsp_download OK
(II) RADEON(0): VIP_GPIO_CNTL: 200001
(II) RADEON(0): VIP_GPIO_INOUT: e200000
(II) RADEON(0): VIP_GPIO_CNTL: 200011
(II) RADEON(0): VIP_GPIO_INOUT: e310010
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): Microcode: Use microcode path: /usr/lib/xorg/modules/multimedia/rt2_pmem.bin
(II) RADEON(0): Microcode: Use microcode type: BINARY
(II) RADEON(0): Microcode: device_id: 4d4a
(II) RADEON(0): Microcode: vendor_id: 1002
(II) RADEON(0): Microcode: rev_id: 1f
(II) RADEON(0): Microcode: num_seg: 4
(II) RADEON(0): Microcode: dsp_init OK
(II) RADEON(0): Microcode: dsp_download OK
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "UseFBDev" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 270 x 203
(WW) Configured Mouse: No Device specified, looking for one...
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Found color CRT connected to primary DAC
in RADEONProbeOutputModes
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
(II) RADEON(0): VIP_GPIO_CNTL: 200011
(II) RADEON(0): VIP_GPIO_INOUT: e300010
(II) RADEON(0): VIP_GPIO_CNTL: 200011
(II) RADEON(0): VIP_GPIO_INOUT: e300010
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): TDA9885 setparam: B data: d2, C data: 30, E data: 84
(II) RADEON(0): TDA9885 status: after_reset=0 afc_status=7 (-187.5 kHz off) fm_carrier=0 vif_level=1 afc_win=0 VCO out
(II) RADEON(0): Microcode: Use microcode path: /usr/lib/xorg/modules/multimedia/rt2_pmem.bin
(II) RADEON(0): Microcode: Use microcode type: BINARY
(II) RADEON(0): Microcode: device_id: 4d4a
(II) RADEON(0): Microcode: vendor_id: 1002
(II) RADEON(0): Microcode: rev_id: 1f
(II) RADEON(0): Microcode: num_seg: 4
(II) RADEON(0): Microcode: dsp_init OK
(II) RADEON(0): Microcode: dsp_download OK
(II) RADEON(0): Setting tuner band to 2
(II) RADEON(0): Setting tuner frequency to 3364
(II) RADEON(0): Tuner status 74
(II) RADEON(0): VIP_GPIO_CNTL: 200011
(II) RADEON(0): VIP_GPIO_INOUT: e310010
(II) RADEON(0): VIP_GPIO_CNTL: 200001
(II) RADEON(0): VIP_GPIO_INOUT: e210000
(II) RADEON(0): Rage Theatre setting standard 0x0301
(II) RADEON(0): TDA9885 setparam: B data: d2, C data: 30, E data: 89
(II) RADEON(0): TDA9885 status: after_reset=0 afc_status=8 (187.5 kHz off) fm_carrier=0 vif_level=1 afc_win=0 VCO out
(II) RADEON(0): TDA9885 status: after_reset=0 afc_status=14 (37.5 kHz off) fm_carrier=1 vif_level=1 afc_win=1 VCO in
(II) RADEON(0): AFC: FI1236_get_afc_hint: 14
(II) RADEON(0): AFC: Setting tuner frequency to 210.219
(II) RADEON(0): Setting tuner band to 2
(II) RADEON(0): Setting tuner frequency to 3363
(II) RADEON(0): Tuner status 74
(II) RADEON(0): TDA9885 status: after_reset=0 afc_status=1 (-37.5 kHz off) fm_carrier=1 vif_level=1 afc_win=1 VCO in
(II) RADEON(0): AFC: FI1236_get_afc_hint: 1
(II) RADEON(0): AFC: Setting tuner frequency to 210.25
(II) RADEON(0): Setting tuner band to 2
(II) RADEON(0): Setting tuner frequency to 3364
(II) RADEON(0): Tuner status 74
(II) RADEON(0): TDA9885 status: after_reset=0 afc_status=14 (37.5 kHz off) fm_carrier=1 vif_level=1 afc_win=1 VCO in
(II) RADEON(0): AFC: FI1236_get_afc_hint: 14
(II) RADEON(0): AFC: Setting tuner frequency to 210.219
(II) RADEON(0): Setting tuner band to 2
(II) RADEON(0): Setting tuner frequency to 3363
(II) RADEON(0): Tuner status 74
(II) RADEON(0): TDA9885 status: after_reset=0 afc_status=1 (-37.5 kHz off) fm_carrier=1 vif_level=1 afc_win=1 VCO in
(II) RADEON(0): AFC: FI1236_get_afc_hint: 1
(II) RADEON(0): AFC: Setting tuner frequency to 210.25
(II) RADEON(0): Setting tuner band to 2
(II) RADEON(0): Setting tuner frequency to 3364
(II) RADEON(0): Tuner status 74
(II) RADEON(0): Microcode: Use microcode path: /usr/lib/xorg/modules/multimedia/rt2_pmem.bin
(II) RADEON(0): Microcode: Use microcode type: BINARY
(II) RADEON(0): Microcode: device_id: 4d4a
(II) RADEON(0): Microcode: vendor_id: 1002
(II) RADEON(0): Microcode: rev_id: 1f
(II) RADEON(0): Microcode: num_seg: 4
(II) RADEON(0): Microcode: dsp_init OK
(II) RADEON(0): Microcode: dsp_download OK
disable montype: 1
(II) RADEON(0): RADEONRestoreMemMapRegisters() :
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000 0xf3fff000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV

```

**Update:**

I found some description in Gatos devel mail list. This cases not solved my problem, but some tests may have interrested results.

Firs test: I connected an analog output (mp3 player) to the Tuner Composit input. 
The result: in XAWTV: I heard the analog source correctly, and I can change volume and I can use mute too.

In the next test I tried to change video input between S-Video, Composite input and Tuner.
Results: 
- S-Video works correctly the sound use analog input. 
- Composite mode displayed the TV signal with the last selected channel. Audio come from external analog input (from mp3 player).
- Tuner: Tuner works, TV image displayed, channel can change but no sound (only from analog input, but it is not the TV audio).

I think, maybe some register or the "Audio Crossbar" not setup correctly. Maybe the PIN of the audio (and video) source not redirected to the correct PIN output with Theatre Crossbar. Xorg found only: FI1216ME, TDA9885 and UDA1380, the MSP3430 loaded, but xorg not found it on my card.

I'm trying to modify some method in ATI xorg driver (radeon_video.c, theatre200.c, radeon_mm_i2c.c) but without ATI Tuner specification it is so hard for me.

May anybody found any solution for this problem?

---

### Post by pumuckly on 2010-07-08
Has anybody found something?

---

