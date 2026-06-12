---
title: "Using 3D / GL locks up system - Radeon  Mobility"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by marx2k on 2006-11-20
If I try to preview a screensaver, run fglrxinfo or do anything 3d related with the Radeon Mobility M7 LW, the system locks up and  requires a hard reboot.

Here is my xorg.conf:

```


Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "GLcore"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
#       Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
#       Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on" #11/20
EndSection

Section "Device"
Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
Driver "radeon"
BusID "PCI:1:0:0"
        Option    "backingstore" "true"
        Option    "EnablePageFlip" "true"
        Option    "SubPixelOrder" "none"
        Option    "AccelMethod" "XAA"
        Option    "RenderAccel" "true"
        Option    "AGPMode" "4"
        Option    "ColorTiling"   "on"
        Option    "DynamicClocks" "on"
        Option    "mtrr" "on"
        Option    "VideoOverlay" "on"
        Option    "OpenGLOverlay" "off"
        Option  "AGPFastWrite" "True"
        Option  "EnablePageFlip" "True"
        Option  "UseInternalAGPGART" "no"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse" "SendCoreEvents" #11/20
        InputDevice     "Synaptics Touchpad" "CorePointer" #11/20
        Option "AIGLX" "True"
EndSection

Section "DRI"
        Mode    0666
EndSection

```



Does anyone have any clue as to why this would be happening?

---

### Post by marx2k on 2006-11-20
Here is Xorg.0.log | grep RADEON

```

(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0x40400000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "AGPMode" "4"
(**) RADEON(0): Option "AGPFastWrite" "True"
(**) RADEON(0): Option "EnablePageFlip" "true"
(**) RADEON(0): Option "ColorTiling" "on"
(**) RADEON(0): Option "RenderAccel" "true"
(**) RADEON(0): Option "SubPixelOrder" "none"
(**) RADEON(0): Option "DynamicClocks" "on"
(**) RADEON(0): Option "AccelMethod" "XAA"
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(**) RADEON(0): Option "mtrr" "on"
(--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
(--) RADEON(0): Linear framebuffer at 0x48000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): [dri] Found DRI library version 1.2.0 and kernel module version 1.25.0
(**) RADEON(0): AGP 4x mode is configured
(**) RADEON(0): Enabling AGP Fast Write
(II) RADEON(0): Page flipping enabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=32768K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Connector0: DDCType-4, DACType-1, TMDSType-0, ConnectorType-4
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 4, Detected Type: 2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): EDID data from the display on port 1 ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 0  Serial#: 0
(II) RADEON(0): Year: 2002  Week: 0
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 29  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.315 whiteY: 0.330
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1051  v_sync_end 1055 v_blanking: 1066 v_border: 0
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN141P2-L02
(II) RADEON(0): 
(II) RADEON(0): Primary:
(II) RADEON(0): Secondary:
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12000 max=35000; xclk=18300
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: SEC                     
(II) RADEON(0): Panel Size from BIOS: 1400x1050
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Valid Mode from Detailed timing table: 1400x1050
(II) RADEON(0): Total of 1 mode(s) found.
(II) RADEON(0): Total number of valid DDC mode(s) found: 1
(II) RADEON(0): Valid mode using on-chip RMX: 1400x1050
(II) RADEON(0): Total number of valid FP mode(s) found: 1
(--) RADEON(0): Virtual size is 1400x1050 (pitch 1408)
(**) RADEON(0): *Mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1400x1050"  108.00  1400 1440 1552 1688  1050 1051 1055 1066
(**) RADEON(0):  Default mode "640x350": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x350"  108.00  640 1440 1552 1688  350 1051 1055 1066
(**) RADEON(0):  Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x400"  108.00  640 1440 1552 1688  400 1051 1055 1066
(**) RADEON(0):  Default mode "720x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "720x400"  108.00  720 1440 1552 1688  400 1051 1055 1066
(**) RADEON(0):  Default mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"  108.00  640 1440 1552 1688  480 1051 1055 1066
(**) RADEON(0):  Default mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"  108.00  800 1440 1552 1688  600 1051 1055 1066
(**) RADEON(0):  Default mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"  108.00  1024 1440 1552 1688  768 1051 1055 1066
(**) RADEON(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1440 1552 1688  864 1051 1055 1066
(**) RADEON(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x960"  108.00  1280 1440 1552 1688  960 1051 1055 1066
(**) RADEON(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1440 1552 1688  1024 1051 1055 1066
(**) RADEON(0):  Default mode "832x624": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "832x624"  108.00  832 1440 1552 1688  624 1051 1055 1066
(**) RADEON(0):  Default mode "1280x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"  108.00  1280 1440 1552 1688  768 1051 1055 1066
(**) RADEON(0):  Default mode "1280x800": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"  108.00  1280 1440 1552 1688  800 1051 1055 1066
(**) RADEON(0):  Default mode "1152x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1152x768"  108.00  1152 1440 1552 1688  768 1051 1055 1066
(--) RADEON(0): Display dimensions: (290, 210) mm
(--) RADEON(0): DPI set to (122, 126)
(**) RADEON(0): Using XAA acceleration architecture
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
(**) RADEON(0): RADEONScreenInit 48000000 0
(**) RADEON(0): Map: 0x48000000, 0x02000000
(**) RADEON(0): Write-combining range (0x48000000,0x2000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81fd480)
(**) RADEON(0): Read: 0x00000006 0x00040048 0x00000000
(**) RADEON(0): Read: rd=6, fd=72, pd=4
(**) RADEON(0): RADEONSaveMode returns 0x81fd480
(II) RADEON(0): Dynamic Clock Scaling Enabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf0c55000
(II) RADEON(0): [drm] mapped SAREA 0xf0c55000 to 0xb7932000
(II) RADEON(0): [drm] framebuffer handle = 0x48000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x1f000217 [AGP 0x8086/0x1a30; Card 0x1002/0x4c57]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0x60000000
(II) RADEON(0): [agp] Ring mapped at 0xb56fd000
(II) RADEON(0): [agp] ring read ptr handle = 0x60101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7931000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0x60102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb54fd000
(II) RADEON(0): [agp] GART texture map handle = 0x60302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb501d000
(II) RADEON(0): [drm] register handle = 0x40400000
(II) RADEON(0): [dri] Visual configs initialized
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x04000000
(**) RADEON(0):   MC_FB_LOCATION   : 0x4bff4800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
(**) RADEON(0): Pitch = 11534512 bytes (virtualX = 1400, displayWidth = 1408)
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x81fde30
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fde30)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x4bff4800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 200f5c5c to 20115c5c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1408,5957)
(II) RADEON(0): Reserved area from (0,1050) to (1408,1058)
(II) RADEON(0): Largest offscreen area available: 1408 x 4899
(II) RADEON(0): Will use back buffer at offset 0xb58000
(II) RADEON(0): Will use depth buffer at offset 0x1104000
(II) RADEON(0): Will use 9472 kb for textures at offset 0x16b0000
(**) RADEON(0): Initializing backing store
(**) RADEON(0): Option "BackingStore" "true"
(**) RADEON(0): Backing store enabled
(**) RADEON(0): DRI Finishing init !
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x4bff4800 is: 0x4bff4800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x607f6000
(**) RADEON(0): GRPH_BUFFER_CNTL from 200f5c5c to 20115c5c
(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration enabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 176
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing Page Flipping
(II) RADEON(0): ShadowFB initialized for Page Flipping
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1058)
(II) RADEON(0): Largest offscreen area available: 1408 x 4896
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): Detected Radeon Mobility M7, disabling multimedia i2c
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(WW) RADEON(0): Option "VideoOverlay" is not used
(WW) RADEON(0): Option "OpenGLOverlay" is not used
(WW) RADEON(0): Option "UseInternalAGPGART" is not used
(**) RADEON(0): RADEONScreenInit finished
(**) RADEON(0): RADEONSaveScreen(2)


```

---

### Post by marx2k on 2006-11-20
Heres something interesting:

When trying to load up 'driconf':
Driver "radeon" is not installed or does not support configuration.

And it loads up a messagebox saying:
"Could not detect any configurable direct-rendering capable devices.  DRIConf will be started in expert mode."

Once I hit OK, terminal throws out:
```

/usr/lib/python2.4/site-packages/driconf_complexui.py:843: DeprecationWarning: 
  "priv", self.configTree.saveConfig, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:846: DeprecationWarning: 
  "priv", self.configTree.reloadConfig, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:847: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:850: DeprecationWarning: 
  "priv", self.configTree.newItem, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:853: DeprecationWarning: 
  "priv", self.configTree.removeItem, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:856: DeprecationWarning: 
  "priv", self.configTree.moveUp, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:859: DeprecationWarning: 
  "priv", self.configTree.moveDown, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:862: DeprecationWarning: 
  "priv", self.configTree.properties, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:863: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:872: DeprecationWarning: 
  self.aboutHandler, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:873: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:876: DeprecationWarning: 
  self.exitHandler, None, -1)

```

NOTE: This used to not be a problem.

---

### Post by marx2k on 2006-11-20
Heres something interesting:

When trying to load up 'driconf':
Driver "radeon" is not installed or does not support configuration.

And it loads up a messagebox saying:
"Could not detect any configurable direct-rendering capable devices.  DRIConf will be started in expert mode."

Once I hit OK, terminal throws out:
```

/usr/lib/python2.4/site-packages/driconf_complexui.py:843: DeprecationWarning: 
  "priv", self.configTree.saveConfig, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:846: DeprecationWarning: 
  "priv", self.configTree.reloadConfig, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:847: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:850: DeprecationWarning: 
  "priv", self.configTree.newItem, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:853: DeprecationWarning: 
  "priv", self.configTree.removeItem, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:856: DeprecationWarning: 
  "priv", self.configTree.moveUp, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:859: DeprecationWarning: 
  "priv", self.configTree.moveDown, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:862: DeprecationWarning: 
  "priv", self.configTree.properties, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:863: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:872: DeprecationWarning: 
  self.aboutHandler, None, -1)
/usr/lib/python2.4/site-packages/driconf_complexui.py:873: DeprecationWarning: 
  self.toolbar.append_space()
/usr/lib/python2.4/site-packages/driconf_complexui.py:876: DeprecationWarning: 
  self.exitHandler, None, -1)

```

NOTE: This used to not be a problem.

---

### Post by marx2k on 2006-11-20
Does anyone know what file I would look at to see what the last errors were before the system crashes?  The problem is the system FREEZES so I dont think it writes anything to any logs :(

I've also uploaded my Xorg.0.log so you can see if there are any problems, but there are NO errors throughout the whole log.  Yet, driconf doesnt work correctly and glxinfo freezes the system completely

---

### Post by marx2k on 2006-11-20
Ok..in case anyone has the same problem, I DID fix my problem:

I followed step by step http:://help.ubuntu.com/community/RadeonDriver

removed fglrx, using "ati" driver instead of "radeon"

everything working as it should be

Here is my new xorg.conf:

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
#	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option          "SHMConfig"             "on" #11/20
EndSection

Section "Device"
Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
Driver "ati"
BusID "PCI:1:0:0"
Option  "XAANoOffscreenPixmaps"
Option	"AGPMode"	"8"
Option	"AccelMethod" 	"EXA"
Option	"ColotTiling"	"On"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse" "SendCoreEvents" #11/20
	InputDevice	"Synaptics Touchpad" "CorePointer" #11/20
	Option "AIGLX" "True"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

And the output of glxinfo:
```

name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 8x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

