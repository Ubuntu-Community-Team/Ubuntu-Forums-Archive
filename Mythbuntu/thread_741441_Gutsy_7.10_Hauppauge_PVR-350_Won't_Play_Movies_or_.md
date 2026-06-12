---
title: "Gutsy 7.10 Hauppauge PVR-350 Won't Play Movies or Xwindow through TV Out"
date: 2008-03-31
forum: Mythbuntu
---

### Post by pokeys on 2008-03-31
Tried just about everything I can thing of - over the last week to get the PVR-350 to play media and Xconsole.  I have no problem playing "live video" - it works great - even the sound is good which was always a major problem with Knoppmyth.

I'll try and give you what others have provided when they had problems:
-----------------
lsmod | grep ivtv_fb
ivtv_fb                19104  0 
ivtv                  134928  2 ivtv_fb
------------------------
Video device info

ls /dev | grep video
video0
video1
video16
video24
video32
video48

<<<Why does this come up with all these video settings?  Shouldn't I just have one?>>>> video16????

----------------------
sudo rmmod saa7127
sudo modprobe saa7127

These work fine!  - V-bars on the TV Screen.  Live video too.  Nothing else is ported to the screen, however.

-----------------------
I followed the instructions as displayed at:

[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

but had no luck.  Suggestions would be most welcome!!!!

Tom


xorg.conf

Section "Files"
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

# Specific modules needed *this is important.*
Section "Module"
        Load "dbe"
        Load "v4l"
        Load "extmod"
        Load "type1"
        Load "freetype"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
        Driver          "sis"
        Busid           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed - in Gutsy, this is NOT "ivtvdev".
        Driver "ivtv" 

        # frame buffer we found above
        Option "fbdev" "/dev/fb0"    
     
        # below settings are optional I've seen lots of people with them commented out.
        # I believe that pal users should just comment below line out.
        Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        # Not optional setting
        # BusID we found with lspci converted as shown above
        BusID "PCI:1:8:0"           

        Screen 0

EndSection


Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection
# these settings are generic (for TVs) but are specifically for TV

Section "Monitor"
        Identifier "TV"
        HorizSync 30-68
        VertRefresh 50-120
        DisplaySize 183 122
        Mode "720x480"
        DotClock 34.564
        HTimings 720 752 840 928
        VTimings 480 484 488 504
        Flags "-HSync" "-VSync"
        EndMode

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option          "SecurityTypes" "VncAuth"
        Option          "UserPasswdVerifier"    "VncAuth"
        Option          "PasswordFile"  "/root/.vnc/passwd"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "vnc"
EndSection
Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed.
        Driver "ivtv" #WATCH IT not called ivtvdev anymore!!

        # frame buffer we found above
        Option "fbdev" "/dev/fb0"

        # below settings are optional I've seen lots of people with them commented out.
        # I believe that pal users should just comment below line out.
        #Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        # Not optional setting
        # BusID we found with lspci converted as shown above
        BusID "PCI:0:8:0"

        Screen 0

EndSection
# Our PVR-350 Driver entry
Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
              Depth 24
              FbBpp 32
              Modes "720x480"
        EndSubsection
EndSection
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "TV Screen"

        # There is other ways to get rid of keyboard and mouse, but you can these settings as is.
        # This setup is designed to run without keyboard and mouse plugged in.
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666 # Not specifically needed as far as I know. 
                     # I think it's specific to my computer's hardware
                     # That said all my ubuntu boxes have this line.

EndSection

---------------------------
---------------------------
xorg.log

IR transmitter
[   38.816637] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   38.847070] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   38.847119] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   38.850104] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   38.909357] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   39.070802] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   39.096979] msp3400 0-0040: MSP4448G-B3 found @ 0x80 (ivtv i2c driver #0)
[   39.096983] msp3400 0-0040: MSP4448G-B3 supports radio, mode is autodetect and autoselect
[   39.097221] tuner 0-0061: type set to 47 (LG NTSC (TAPE series))
[   39.365418] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   39.365609] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   39.365799] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   39.365904] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   39.366132] ivtv0: Registered device radio0 for encoder radio
[   39.366177] ivtv0: Registered device video16 for decoder MPEG (1 MB)
[   39.366291] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
[   39.366591] ivtv0: Registered device vbi16 for decoder VOUT
[   39.366635] ivtv0: Registered device video48 for decoder YUV (1 MB)
[   39.426264] ivtv0: loaded v4l-cx2341x-init.mpg firmware (3616992432 bytes)
[   39.633281] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[   39.633321] ivtv:  ====================  END INIT IVTV  ====================
[   39.634092] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[   39.960330] intel8x0_measure_ac97_clock: measured 52932 usecs
[   39.960335] intel8x0: clocking to 48000
[   40.488723] lp0: using parport0 (interrupt-driven).
[   40.538823] ivtv0-fb: Framebuffer at 0xe1510000, mapped to 0xdd810000, size 1665k
[   40.621673] ivtv0-fb: === Validated display mode  ===
[   40.621680] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   40.621682] ivtv0-fb: Display position 1,1
[   40.621684] ivtv0-fb: Display filter : on
[   40.621685] ivtv0-fb: Color space : RGB
[   40.654576] ivtv0-fb: === Display mode change ===
[   40.654582] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   40.654584] ivtv0-fb: Display position 1,1
[   40.654585] ivtv0-fb: Display filter : on
[   40.654587] ivtv0-fb: Color space : RGB
[   40.662526] ivtv0-fb: Running in compatibility mode. Display resize & mode change disabled
[   40.662529] ivtv0-fb: Framebuffer registered on ivtv card id 0
[   40.922134] Adding 1309256k swap on /dev/sda5.  Priority:-1 extents:1 across:1309256k
[   41.226678] EXT3 FS on sda1, internal journal
[   42.865711] usb-storage: device scan complete
[   42.872687] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   42.879660] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   42.886636] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   42.893617] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   42.904668] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   42.904729] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   42.916556] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[   42.916615] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   42.927617] sd 4:0:0:2: [sde] Attached SCSI removable disk
[   42.927676] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   42.938579] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   42.938644] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   43.103923] APIC error on CPU0: 00(40)
[   43.237043] APIC error on CPU0: 40(40)
[   43.286929] APIC error on CPU0: 40(40)
[   43.320204] APIC error on CPU0: 40(40)
[   44.351970] No dock devices found.
[   44.436377] input: Power Button (FF) as /class/input/input3
[   44.436740] ACPI: Power Button (FF) [PWRF]
[   44.448365] input: Power Button (CM) as /class/input/input4
[   44.448717] ACPI: Power Button (CM) [PWRB]
[   44.456329] input: Sleep Button (CM) as /class/input/input5
[   44.456698] ACPI: Sleep Button (CM) [FUTS]
[   46.148957] APIC error on CPU0: 40(40)
[   46.947674] APIC error on CPU0: 40(40)
[   47.064180] APIC error on CPU0: 40(40)
[   47.459057] NET: Registered protocol family 10
[   47.459492] lo: Disabled Privacy Extensions
[   48.969276] eth0: Media Link On 100mbps full-duplex 
[   49.027665] APIC error on CPU0: 40(40)
[   49.377074] APIC error on CPU0: 40(40)
[   51.473676] APIC error on CPU0: 40(40)
[   52.022817] APIC error on CPU0: 40(40)
[   54.718722] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   54.875571] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   54.886802] NFSD: starting 90-second grace period
[   55.750121] APIC error on CPU0: 40(40)
[   58.412480] APIC error on CPU0: 40(40)
[   58.928275] APIC error on CPU0: 40(40)
[   60.009889] APIC error on CPU0: 40(40)
[   60.762801] NET: Registered protocol family 17
[   61.956709] APIC error on CPU0: 40(40)
[   62.173052] APIC error on CPU0: 40(40)
[   62.295365] lirc_dev: IR Remote Control driver registered, at major 61 
[   62.436897] bttv: driver version 0.9.17 loaded
[   62.436905] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   62.519917] cx2388x v4l2 driver version 0.0.6 loaded
[   62.534422] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[   62.534766] lirc_dev: lirc_register_plugin: sample_rate: 10
[   64.053316] APIC error on CPU0: 40(40)
[   65.800524] APIC error on CPU0: 40(40)
[   67.015193] APIC error on CPU0: 40(40)
[   70.509535] APIC error on CPU0: 40(40)
[   70.925562] APIC error on CPU0: 40(40)
[   71.940548] APIC error on CPU0: 40(40)
[   72.373691] eth0: no IPv6 routers present
[   72.839096] APIC error on CPU0: 40(40)
[   73.953989] APIC error on CPU0: 40(40)

---

### Post by pokeys on 2008-03-31
Oh, and another thing.  The TV screen will show the Mythbuntu splash screen just before shutting down!!!  It's the only time anything displays that's not "live TV" . Talk about taunting me every step of the way!!!!

---

### Post by trubblemaker on 2008-04-13
I'm totally having the same issue.  As Mythbuntu has an automatic fail over it's hard to see what the actual error message from X is.

Anyone know how to get the failure message from X ?

the issue revolves around the frame buffer not being loaded early enough in the boot sequence(hence it working properly on shutdown but not on start up.)

Might be worth filing a bug against Mythbuntu once we get some more info.

---

### Post by trubblemaker on 2008-04-13
It appears that none of the changes I"m making to xorg.conf are taking effect.  It's got someother file it's reading values from..... 

Anyone know if how to make xorg.conf changes stick in Gutsy?

---

### Post by trubblemaker on 2008-04-19
Looks like rebooting was my issue.  Had to power off and on to get changes to take effect.

After that I selected recovery console from grub.
I manually started X wtih
```
X
```
That when I used <ctrl>+<alt>+<backspave> it killed X and I got the error messages from mistakes in my Xorg.conf.

I had a copy paste error that once fixed made everything work fine.

Hope this helps someone else.

---

