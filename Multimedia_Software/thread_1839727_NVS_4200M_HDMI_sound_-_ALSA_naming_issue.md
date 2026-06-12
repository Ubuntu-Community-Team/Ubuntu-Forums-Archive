---
title: "NVS 4200M HDMI sound - ALSA naming issue"
date: 2011-09-06
forum: Multimedia Software
---

### Post by shaolintl on 2011-09-06
I have both Intel and the above cards installed:

sudo cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf5320000 irq 45
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf3000000 irq 17
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw unknown

I can get sound only from the intel card. Is it a naming issue as:

sudo cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel
29 thinkpad_acpi

gives me for both cards the same name, taken probably from the first part of the name of the card. Therefore I cannot switch between them as default cards.

Does anybody know how to solve this?

---

### Post by BicyclerBoy on 2011-09-07
I guess this is an optimus laptop ?

The same name is the driver module snd_intel_hda which is used for all HDA codecs.

I think you have a chipset HDA & a HDA codec in the nvidia graphics (which contains an intel HDA compliant codec).

aplay -l
aplay -L
What ubuntu distro are you running ?

speaker-test
what alsa version does that return?

---

### Post by shaolintl on 2011-09-07
Hi BicyclerBoy,

I am running Kubuntu 11.04 and yes, it is an Optimus card with integrated graphics turned off in BIOS.

I have spoken with NVidia some months ago and was told the current kernel does not support their audio driver and that I should install the newer kernel. It did not solve the problem though.

The output for the commands is below,
Thank you for your help

uname -a 
Linux cactus 2.6.39-0-generic #5~20110427-Ubuntu SMP Wed Apr 27 15:27:41 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


speaker-test
speaker-test 1.0.24.2
Playback device is default

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=PCH,DEV=0
    HDA Intel PCH, CONEXANT Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers                                                                                                           
surround41:CARD=PCH,DEV=0                                                                                                                                    
    HDA Intel PCH, CONEXANT Analog                                                                                                                           
    4.1 Surround output to Front, Rear and Subwoofer speakers                                                                                                
surround50:CARD=PCH,DEV=0                                                                                                                                    
    HDA Intel PCH, CONEXANT Analog                                                                                                                           
    5.0 Surround output to Front, Center and Rear speakers                                                                                                   
surround51:CARD=PCH,DEV=0                                                                                                                                    
    HDA Intel PCH, CONEXANT Analog                                                                                                                           
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers                                                                                        
surround71:CARD=PCH,DEV=0                                                                                                                                    
    HDA Intel PCH, CONEXANT Analog                                                                                                                           
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers                                                                                     
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, CONEXANT Analog                                                                                                                           
    Direct sample mixing device                                                                                                                              
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, CONEXANT Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, CONEXANT Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, CONEXANT Analog
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions


> **BicyclerBoy said:**
> I guess this is an optimus laptop ?

The same name is the driver module snd_intel_hda which is used for all HDA codecs.

I think you have a chipset HDA & a HDA codec in the nvidia graphics (which contains an intel HDA compliant codec).

aplay -l
aplay -L
What ubuntu distro are you running ?

speaker-test
what alsa version does that return?

---

### Post by BicyclerBoy on 2011-09-07
With X server active..HDMI display connected. no HT amp in series.

speaker-test -c 2 -r 48000 -D hw:1,3

cat /proc/asound/card1/codec#0

cat /proc/asound/card1/eld#0.0

Because this PC is an Optimus setup this is a guess.
If this was a nVidia discrete graphics setup, HDMI audio would **not** work without the nVidia driver running the X server. 
I don't know what happens here..

---

### Post by shaolintl on 2011-09-08
speaker-test -c 2 -r 48000 -D hw:1,3

no sound is heard

Below are the two other outputs. I have noticed that the eld_valid is 0. it is so also with 0.1 and 0.2 (the two other options).

As I turned off the integrated option I think the OS consider it as a discrete graphics setup. I get the logo of nvidia when the x-server starts.

thanks.

cat /proc/asound/card1/eld#0.0
monitor_present         0
eld_valid               0
monitor_name
connection_type         HDMI
eld_version             [0x0] reserved
edid_version            [0x0] no CEA EDID Timing Extension block present
manufacture_id          0x0
product_id              0x0
port_id                 0x0
support_hdcp            0
support_ai              0
audio_sync_delay        0
speakers                [0xffff] FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
sad_count               0


cat /proc/asound/card1/codec#0
Codec: Nvidia GPU 1c HDMI/DP
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de001c
Subsystem Id: 0x17aa21cf
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x08* 0x09
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 2
     0x08* 0x09
Node 0x06 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=06, enabled=1
  Connection: 2
     0x08* 0x09
Node 0x07 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=07, enabled=1
  Connection: 2
     0x08* 0x09
Node 0x08 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x09 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0

---

### Post by BicyclerBoy on 2011-09-08
Sorry I misread the bit about integrated graphics disabled in BIOS.. 
In a normal computer...
If you are using the nvidia graphics & want HDMI audio, you **have to** use the nvidia proprietary driver ( X server driver).

I was not sure if this was the case with optimus & shared HDMI output connectors etc but it most likely is..

Your video card (very good HTPC GPU) is supported by 275.xxx.x & maybe earlier.

After installing the nvidia driver I think you will get 2 -4 HDMI audio subdevices.
We can then go thru' aplay, speaker-test, cat /proc/../eld#x.0  stuff again..

---

### Post by shaolintl on 2011-09-09
The ubuntu package nvidia-current installs the 280.xx but I tried to install both the proprietary 275 and 280 drivers from the nvidia website. All returned the same values and no sound was produced using this device.

As I dont understand anything in these matters, I thought it might be just changing some lines in a configuration file but it seems the nvidia driver just do not support their own audio card (video works perfect).

Many thanks for your time and help though. I will contact nvidia again.

---

### Post by BicyclerBoy on 2011-09-09
I would seriously doubt it is nVidia's fault.
The NVS4200M is basically a GT520 & that works okay..

Trying to install driver from nVidia website is a bad idea unless you understand the process..
Maybe you should post the /var/log/Xorg.0.log to confirm the driver..

It is most likely the alsa drivers are to blame.
Or BIOS settings..
or snd_hda_intel module probe_mask set wrong..

Did 
aplay -l
return the same info ?

Other options:
Find later kernel & alsa user-space drivers from a launchpad ppa..
Find someone else with same PC..

---

### Post by shaolintl on 2011-09-13
Hi BicyclerBoy,

Thanks again for the reply. I reverted back to the ubuntu nvidia-current package but aplay -l returned the same info. Below is the Xorg.0.log output. I tried to install the latest kernel (3.1.0) but as I dont understand much about these issues, it did not work and I revereted back to 2.39. I think I have the latest alsa drivers.

Thanks again for all your help


cat /var/log/Xorg.0.log                                                                                                                                                         
[    28.718]                                                                                                                                                                                              
X.Org X Server 1.10.1                                                                                                                                                                                     
Release Date: 2011-04-15
[    28.718] X Protocol Version 11, Revision 0                                                                                                                                                            
[    28.718] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu                                                                                                                                 
[    28.718] Current Operating System: Linux cactus 2.6.39-0-generic #5~20110427-Ubuntu SMP Wed Apr 27 15:27:41 UTC 2011 x86_64
[    28.718] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.39-0-generic root=UUID=3944477a-59be-4cd5-bfb7-a1e35fe58cf6 ro quiet splash vt.handoff=7
[    28.718] Build Date: 11 August 2011  03:43:05PM
[    28.718] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    28.718] Current version of pixman: 0.20.2
[    28.718]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    28.718] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.719] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 13 09:27:10 2011
[    28.719] (==) Using config file: "/etc/X11/xorg.conf"
[    28.719] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.719] (==) ServerLayout "Layout0"
[    28.719] (**) |-->Screen "Screen0" (0)
[    28.719] (**) |   |-->Monitor "Monitor0"
[    28.719] (**) |   |-->Device "Device0"
[    28.719] (**) |-->Input Device "Keyboard0"
[    28.719] (**) |-->Input Device "Mouse0"
[    28.719] (**) Option "Xinerama" "0"
[    28.719] (==) Automatically adding devices
[    28.719] (==) Automatically enabling devices
[    28.719] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.719]    Entry deleted from font path.
[    28.719] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.719]    Entry deleted from font path.
[    28.719] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.719]    Entry deleted from font path.
[    28.719] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.719]    Entry deleted from font path.
[    28.719] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.719]    Entry deleted from font path.
[    28.719] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    28.719] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.719] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    28.719] (WW) Disabling Keyboard0
[    28.719] (WW) Disabling Mouse0
[    28.719] (II) Loader magic: 0x7e17e0
[    28.719] (II) Module ABI versions:
[    28.719]    X.Org ANSI C Emulation: 0.4
[    28.719]    X.Org Video Driver: 10.0
[    28.719]    X.Org XInput driver : 12.3
[    28.719]    X.Org Server Extension : 5.0
[    28.720] (--) PCI:*(0:1:0:0) 10de:1057:17aa:21cf rev 161, Mem @ 0xf2000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x00005000/128, BIOS @ 0x????????/524288
[    28.720] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.720] (II) LoadModule: "extmod"
[    28.722] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.722] (II) Module extmod: vendor="X.Org Foundation"
[    28.722]    compiled for 1.10.1, module version = 1.0.0
[    28.722]    Module class: X.Org Server Extension
[    28.722]    ABI class: X.Org Server Extension, version 5.0
[    28.722] (II) Loading extension MIT-SCREEN-SAVER
[    28.722] (II) Loading extension XFree86-VidModeExtension
[    28.722] (II) Loading extension XFree86-DGA
[    28.722] (II) Loading extension DPMS
[    28.722] (II) Loading extension XVideo
[    28.722] (II) Loading extension XVideo-MotionCompensation
[    28.722] (II) Loading extension X-Resource
[    28.722] (II) LoadModule: "dbe"
[    28.722] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.722] (II) Module dbe: vendor="X.Org Foundation"
[    28.722]    compiled for 1.10.1, module version = 1.0.0
[    28.722]    Module class: X.Org Server Extension
[    28.722]    ABI class: X.Org Server Extension, version 5.0
[    28.722] (II) Loading extension DOUBLE-BUFFER
[    28.722] (II) LoadModule: "glx"
[    28.722] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    28.730] (II) Module glx: vendor="NVIDIA Corporation"
[    28.730]    compiled for 4.0.2, module version = 1.0.0
[    28.730]    Module class: X.Org Server Extension
[    28.730] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[    28.730] (II) Loading extension GLX
[    28.730] (II) LoadModule: "record"
[    28.730] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.730] (II) Module record: vendor="X.Org Foundation"
[    28.730]    compiled for 1.10.1, module version = 1.13.0
[    28.730]    Module class: X.Org Server Extension
[    28.730]    ABI class: X.Org Server Extension, version 5.0
[    28.730] (II) Loading extension RECORD
[    28.730] (II) LoadModule: "dri"
[    28.730] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.730] (II) Module dri: vendor="X.Org Foundation"
[    28.730]    compiled for 1.10.1, module version = 1.0.0
[    28.730]    ABI class: X.Org Server Extension, version 5.0
[    28.730] (II) Loading extension XFree86-DRI
[    28.730] (II) LoadModule: "dri2"
[    28.731] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.731] (II) Module dri2: vendor="X.Org Foundation"
[    28.731]    compiled for 1.10.1, module version = 1.2.0
[    28.731]    ABI class: X.Org Server Extension, version 5.0
[    28.731] (II) Loading extension DRI2
[    28.731] (II) LoadModule: "nvidia"
[    28.731] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    28.731] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.731]    compiled for 4.0.2, module version = 1.0.0
[    28.731]    Module class: X.Org Video Driver
[    28.731] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[    28.731] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    28.731] (++) using VT number 7

[    28.731] (II) Loading sub module "fb"
[    28.731] (II) LoadModule: "fb"
[    28.731] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.731] (II) Module fb: vendor="X.Org Foundation"
[    28.731]    compiled for 1.10.1, module version = 1.0.0
[    28.731]    ABI class: X.Org ANSI C Emulation, version 0.4
[    28.731] (II) Loading sub module "wfb"
[    28.731] (II) LoadModule: "wfb"
[    28.731] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.732] (II) Module wfb: vendor="X.Org Foundation"
[    28.732]    compiled for 1.10.1, module version = 1.0.0
[    28.732]    ABI class: X.Org ANSI C Emulation, version 0.4
[    28.732] (II) Loading sub module "ramdac"
[    28.732] (II) LoadModule: "ramdac"
[    28.732] (II) Module "ramdac" already built-in
[    28.732] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    28.732] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.732] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.732] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    28.732] (==) NVIDIA(0): RGB weight 888
[    28.732] (==) NVIDIA(0): Default visual is TrueColor
[    28.732] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.732] (**) NVIDIA(0): Option "TwinView" "1"
[    28.732] (**) NVIDIA(0): Option "MetaModes" "DFP: nvidia-auto-select +0+0, CRT-0: nvidia-auto-select +1600+0"
[    28.732] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[    28.732] (**) NVIDIA(0): Option "RegistryDwords" "EnableBrightnessControl=1"
[    29.592] (II) NVIDIA(GPU-0): Display (Idek Iiyama PLB2403WS (CRT-0)) does not support
[    29.787] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    29.788] (II) NVIDIA(GPU-0): Display (LEN (DFP-0)) does not support NVIDIA 3D Vision
[    29.788] (II) NVIDIA(GPU-0):     stereo.
[    29.789] (II) NVIDIA(0): NVIDIA GPU NVS 4200M (GF119) at PCI:1:0:0 (GPU-0)
[    29.789] (--) NVIDIA(0): Memory: 1048576 kBytes
[    29.789] (--) NVIDIA(0): VideoBIOS: 75.19.1f.00.01
[    29.789] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    29.789] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    29.789] (--) NVIDIA(0): Connected display device(s) on NVS 4200M at PCI:1:0:0
[    29.789] (--) NVIDIA(0):     Idek Iiyama PLB2403WS (CRT-0)
[    29.789] (--) NVIDIA(0):     LEN (DFP-0)
[    29.789] (--) NVIDIA(0): Idek Iiyama PLB2403WS (CRT-0): 400.0 MHz maximum pixel clock
[    29.789] (--) NVIDIA(0): LEN (DFP-0): 330.0 MHz maximum pixel clock
[    29.789] (--) NVIDIA(0): LEN (DFP-0): Internal Dual Link LVDS
[    29.791] (**) NVIDIA(0): TwinView enabled
[    29.791] (II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
[    29.791] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[    29.791] (**) NVIDIA(0):     enabled on all display devices.
[    29.798] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[    29.798] (**) NVIDIA(0):     enabled on all display devices.
[    29.798] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1600x900"
[    29.798] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    29.798] (WW) NVIDIA(0):     HorizSync range (47.098-56.510 kHz) would exclude this
[    29.798] (WW) NVIDIA(0):     mode's HorizSync (37.7 kHz); ignoring HorizSync check for
[    29.798] (WW) NVIDIA(0):     mode "1600x900".
[    29.799] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1600x900"
[    29.799] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    29.799] (WW) NVIDIA(0):     HorizSync range (47.098-56.510 kHz) would exclude this
[    29.799] (WW) NVIDIA(0):     mode's HorizSync (37.7 kHz); ignoring HorizSync check for
[    29.799] (WW) NVIDIA(0):     mode "1600x900".
[    29.812] (II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
[    29.812] (II) NVIDIA(0): Validated modes:
[    29.812] (II) NVIDIA(0):    
[    29.812] (II) NVIDIA(0):     "DFP:nvidia-auto-select+0+0,CRT-0:nvidia-auto-select+1600+0"
[    29.812] (II) NVIDIA(0): Virtual screen size determined to be 3520 x 1200
[    30.332] (--) NVIDIA(0): DPI set to (93, 92); computed from "UseEdidDpi" X config
[    30.332] (--) NVIDIA(0):     option
[    30.332] (--) Depth 24 pixmap format is 32 bpp
[    30.332] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    30.332] (II) NVIDIA:     access.
[    30.337] (II) NVIDIA(0): Setting mode
[    30.337] (II) NVIDIA(0):     "DFP:nvidia-auto-select+0+0,CRT-0:nvidia-auto-select+1600+0"
[    30.618] (II) Loading extension NV-GLX
[    30.662] (==) NVIDIA(0): Disabling shared memory pixmaps
[    30.662] (==) NVIDIA(0): Backing store disabled
[    30.662] (==) NVIDIA(0): Silken mouse enabled
[    30.662] (**) NVIDIA(0): DPMS enabled
[    30.662] (II) Loading extension NV-CONTROL
[    30.662] (II) Loading extension XINERAMA
[    30.662] (II) Loading sub module "dri2"
[    30.662] (II) LoadModule: "dri2"
[    30.663] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.663] (II) Module dri2: vendor="X.Org Foundation"
[    30.663]    compiled for 1.10.1, module version = 1.2.0
[    30.663]    ABI class: X.Org Server Extension, version 5.0
[    30.663] (II) NVIDIA(0): [DRI2] Setup complete
[    30.663] (==) RandR enabled
[    30.663] (II) Initializing built-in extension Generic Event Extension
[    30.663] (II) Initializing built-in extension SHAPE
[    30.663] (II) Initializing built-in extension MIT-SHM
[    30.663] (II) Initializing built-in extension XInputExtension
[    30.663] (II) Initializing built-in extension XTEST
[    30.663] (II) Initializing built-in extension BIG-REQUESTS
[    30.663] (II) Initializing built-in extension SYNC
[    30.663] (II) Initializing built-in extension XKEYBOARD
[    30.663] (II) Initializing built-in extension XC-MISC
[    30.663] (II) Initializing built-in extension SECURITY
[    30.663] (II) Initializing built-in extension XINERAMA
[    30.663] (II) Initializing built-in extension XFIXES
[    30.663] (II) Initializing built-in extension RENDER
[    30.663] (II) Initializing built-in extension RANDR
[    30.663] (II) Initializing built-in extension COMPOSITE
[    30.663] (II) Initializing built-in extension DAMAGE
[    30.663] (II) Initializing built-in extension GESTURE
[    30.690] (II) Initializing extension GLX
[    30.703] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.708] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    30.708] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.708] (II) LoadModule: "evdev"
[    30.710] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.710] (II) Module evdev: vendor="X.Org Foundation"
[    30.710]    compiled for 1.10.0.902, module version = 2.6.0
[    30.710]    Module class: X.Org XInput Driver
[    30.710]    ABI class: X.Org XInput driver, version 12.3
[    30.710] (II) Using input driver 'evdev' for 'Power Button'
[    30.710] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.710] (**) Power Button: always reports core events
[    30.710] (**) Power Button: Device: "/dev/input/event2"
[    30.830] (--) Power Button: Found keys
[    30.830] (II) Power Button: Configuring as keyboard
[    30.830] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    30.830] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    30.830] (**) Option "xkb_rules" "evdev"
[    30.830] (**) Option "xkb_model" "pc105"
[    30.830] (**) Option "xkb_layout" "at"
[    30.831] (II) XKB: reuse xkmfile /var/lib/xkb/server-11CCA49F19D9E93AF6B2C65E09D15B710633D292.xkm
[    30.836] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    30.836] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.836] (II) Using input driver 'evdev' for 'Video Bus'
[    30.836] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.836] (**) Video Bus: always reports core events
[    30.836] (**) Video Bus: Device: "/dev/input/event4"
[    30.950] (--) Video Bus: Found keys
[    30.950] (II) Video Bus: Configuring as keyboard
[    30.950] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0a/LNXVIDEO:01/input/input4/event4"
[    30.950] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    30.950] (**) Option "xkb_rules" "evdev"
[    30.950] (**) Option "xkb_model" "pc105"
[    30.950] (**) Option "xkb_layout" "at"
[    30.951] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    30.951] (II) No input driver/identifier specified (ignoring)
[    30.951] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    30.951] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    30.951] (II) Using input driver 'evdev' for 'Sleep Button'
[    30.951] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.951] (**) Sleep Button: always reports core events
[    30.951] (**) Sleep Button: Device: "/dev/input/event1"
[    31.110] (--) Sleep Button: Found keys
[    31.110] (II) Sleep Button: Configuring as keyboard
[    31.110] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    31.110] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    31.110] (**) Option "xkb_rules" "evdev"
[    31.110] (**) Option "xkb_model" "pc105"
[    31.110] (**) Option "xkb_layout" "at"
[    31.111] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event5)
[    31.111] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[    31.111] (II) Using input driver 'evdev' for 'Logitech Optical USB Mouse'
[    31.111] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.111] (**) Logitech Optical USB Mouse: always reports core events
[    31.111] (**) Logitech Optical USB Mouse: Device: "/dev/input/event5"
[    31.220] (--) Logitech Optical USB Mouse: Found 3 mouse buttons
[    31.220] (--) Logitech Optical USB Mouse: Found scroll wheel(s)
[    31.220] (--) Logitech Optical USB Mouse: Found relative axes
[    31.220] (--) Logitech Optical USB Mouse: Found x and y relative axes
[    31.220] (II) Logitech Optical USB Mouse: Configuring as mouse
[    31.220] (II) Logitech Optical USB Mouse: Adding scrollwheel support
[    31.220] (**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[    31.220] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.220] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input5/event5"
[    31.220] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[    31.220] (II) Logitech Optical USB Mouse: initialized for relative axes.
[    31.220] (**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
[    31.220] (**) Logitech Optical USB Mouse: (accel) acceleration profile 0
[    31.220] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[    31.220] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[    31.220] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[    31.220] (II) No input driver/identifier specified (ignoring)
[    31.221] (II) config/udev: Adding input device Integrated Camera (/dev/input/event7)
[    31.221] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[    31.221] (II) Using input driver 'evdev' for 'Integrated Camera'
[    31.221] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.221] (**) Integrated Camera: always reports core events
[    31.221] (**) Integrated Camera: Device: "/dev/input/event7"
[    31.270] (--) Integrated Camera: Found keys
[    31.270] (II) Integrated Camera: Configuring as keyboard
[    31.270] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input7/event7"
[    31.270] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD)
[    31.270] (**) Option "xkb_rules" "evdev"
[    31.270] (**) Option "xkb_model" "pc105"
[    31.270] (**) Option "xkb_layout" "at"
[    31.271] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event6)
[    31.271] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    31.271] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    31.271] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.271] (**) Dell Dell USB Keyboard: always reports core events
[    31.271] (**) Dell Dell USB Keyboard: Device: "/dev/input/event6"
[    31.330] (--) Dell Dell USB Keyboard: Found keys
[    31.330] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    31.330] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input6/event6"
[    31.330] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    31.330] (**) Option "xkb_rules" "evdev"
[    31.330] (**) Option "xkb_model" "pc105"
[    31.330] (**) Option "xkb_layout" "at"
[    31.332] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    31.332] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.332] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.332] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.332] (**) AT Translated Set 2 keyboard: always reports core events
[    31.332] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    31.400] (--) AT Translated Set 2 keyboard: Found keys
[    31.400] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    31.400] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    31.400] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    31.400] (**) Option "xkb_rules" "evdev"
[    31.400] (**) Option "xkb_model" "pc105"
[    31.400] (**) Option "xkb_layout" "at"
[    31.400] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    31.400] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    31.400] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    31.400] (II) LoadModule: "synaptics"
[    31.400] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    31.401] (II) Module synaptics: vendor="X.Org Foundation"
[    31.401]    compiled for 1.10.1, module version = 1.3.99
[    31.401]    Module class: X.Org XInput Driver
[    31.401]    ABI class: X.Org XInput driver, version 12.3
[    31.401] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    31.401] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    31.401] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    31.401] (**) Option "Device" "/dev/input/event9"
[    31.470] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5888
[    31.470] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4820
[    31.470] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    31.470] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    31.470] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    31.470] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    31.470] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    31.470] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    31.470] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    31.470] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    31.470] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    31.470] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.036
[    31.470] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    31.470] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    31.470] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    31.470] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    31.471] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    31.471] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    31.471] (II) No input driver/identifier specified (ignoring)
[    31.472] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event8)
[    31.472] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    31.472] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    31.472] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.472] (**) ThinkPad Extra Buttons: always reports core events
[    31.472] (**) ThinkPad Extra Buttons: Device: "/dev/input/event8"
[    31.472] (--) ThinkPad Extra Buttons: Found keys
[    31.472] (II) ThinkPad Extra Buttons: Configuring as keyboard
[    31.472] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input8/event8"
[    31.472] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[    31.472] (**) Option "xkb_rules" "evdev"
[    31.472] (**) Option "xkb_model" "pc105"
[    31.472] (**) Option "xkb_layout" "at"
[    33.333] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A6A577C3976F93D6EE7E61823B317683AF3D396.xkm
[    37.222] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse2)
[    37.222] (II) No input driver/identifier specified (ignoring)
[    37.222] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event10)
[    37.222] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    37.222] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    37.222] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.222] (**) TPPS/2 IBM TrackPoint: always reports core events
[    37.222] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event10"
[    37.310] (--) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    37.310] (--) TPPS/2 IBM TrackPoint: Found relative axes
[    37.310] (--) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    37.310] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    37.310] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    37.310] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.310] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input10/event10"
[    37.310] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    37.310] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[    37.310] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    37.310] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    37.310] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    37.310] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4

---

### Post by BicyclerBoy on 2011-09-13
Your earlier post stated you had the nvidia boot splash screen..your Xorg.0.log file confirms nVidia 280 driver..just a warnig about EDID mode contradiction.

I would think nVidia knows better than anyone about the HDA audio support.
A kernel upgrade should have been the easiest way.
The nVidia graphics driver has kernel version dependencies (headers package).

What did not work with the kernel upgrade ?

It is possible to upgrade just the alsa kernel modules from ubuntu audio dev ppa
& probably the user-space alsa libraries from some other launchpad ppa.

There was a posting on alsa-devel mailing lists about nvs 3100m support; this post was not answered.

---

### Post by shaolintl on 2011-09-14
Hi BicyclerBoy,

Thank for your reply. I have managed to upgrade the kernel (to 3.1) but it did not solve the problem. Interestingly, the eid files have changed and many parameters were deleted:

cat eld#0.0
monitor_present         0
eld_valid               0

the codec seems the same.

Thanks

---

### Post by BicyclerBoy on 2011-09-14
Has the output from this changed ?
aplay -l

dmesg | grep HDMI

Are there more or less files /proc/asound/card1/eld*
The later kernel hopefully has exposed more subdevices..

---

### Post by shaolintl on 2011-09-15
The output from both contains more information, but the number of eld did not change and they contain less information.

ls /proc/asound/card1
codec#0  eld#0.0  eld#0.1  eld#0.2  id  pcm3p  pcm7p  pcm8p

there are three pcm subdirectories (there was only one before)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dmesg | grep HDMI
[   19.416537] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   19.576336] HDMI status: Codec=0 Pin=6 Presence_Detect=0 ELD_Valid=0
[   19.736130] HDMI status: Codec=0 Pin=7 Presence_Detect=0 ELD_Valid=0
[   19.956112] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   19.956159] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   19.956202] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10


cat /var/log/Xorg.0.log | grep NVIDIA
[    26.563] (II) Module glx: vendor="NVIDIA Corporation"
[    26.591] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[    26.921] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.026] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[    27.026] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    27.246] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    27.246] (==) NVIDIA(0): RGB weight 888
[    27.246] (==) NVIDIA(0): Default visual is TrueColor
[    27.246] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.246] (**) NVIDIA(0): Option "TwinView" "0"
[    27.247] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    27.247] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[    27.247] (**) NVIDIA(0): Option "RegistryDwords" "EnableBrightnessControl=1"
[    28.166] (II) NVIDIA(GPU-0): Display (LEN (DFP-0)) does not support NVIDIA 3D Vision
[    28.166] (II) NVIDIA(GPU-0):     stereo.
[    28.167] (II) NVIDIA(0): NVIDIA GPU NVS 4200M (GF119) at PCI:1:0:0 (GPU-0)
[    28.167] (--) NVIDIA(0): Memory: 1048576 kBytes
[    28.167] (--) NVIDIA(0): VideoBIOS: 75.19.1f.00.01
[    28.167] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    28.167] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    28.167] (--) NVIDIA(0): Connected display device(s) on NVS 4200M at PCI:1:0:0
[    28.167] (--) NVIDIA(0):     LEN (DFP-0)
[    28.167] (--) NVIDIA(0): LEN (DFP-0): 330.0 MHz maximum pixel clock
[    28.167] (--) NVIDIA(0): LEN (DFP-0): Internal Dual Link LVDS
[    28.169] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[    28.169] (**) NVIDIA(0):     enabled on all display devices.
[    28.169] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1600x900"
[    28.169] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    28.169] (WW) NVIDIA(0):     HorizSync range (47.098-56.510 kHz) would exclude this
[    28.169] (WW) NVIDIA(0):     mode's HorizSync (37.7 kHz); ignoring HorizSync check for
[    28.169] (WW) NVIDIA(0):     mode "1600x900".
[    28.169] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1600x900"
[    28.169] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    28.169] (WW) NVIDIA(0):     HorizSync range (47.098-56.510 kHz) would exclude this
[    28.169] (WW) NVIDIA(0):     mode's HorizSync (37.7 kHz); ignoring HorizSync check for
[    28.169] (WW) NVIDIA(0):     mode "1600x900".
[    28.183] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    28.183] (II) NVIDIA(0): Validated modes:
[    28.183] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    28.183] (II) NVIDIA(0): Virtual screen size determined to be 1600 x 900
[    28.718] (--) NVIDIA(0): DPI set to (116, 120); computed from "UseEdidDpi" X config
[    28.718] (--) NVIDIA(0):     option
[    28.718] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    28.718] (II) NVIDIA:     access.
[    28.723] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    29.267] (==) NVIDIA(0): Disabling shared memory pixmaps
[    29.267] (==) NVIDIA(0): Backing store disabled
[    29.267] (==) NVIDIA(0): Silken mouse enabled
[    29.269] (**) NVIDIA(0): DPMS enabled
[    29.270] (II) NVIDIA(0): [DRI2] Setup complete
[  2169.711] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[  2528.742] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[  3328.891] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[  4658.553] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[  4875.683] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[  9207.984] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[ 10874.802] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[ 11250.377] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"

---

### Post by BicyclerBoy on 2011-09-15
This may sound like a silly question but..
Where do you expect this HDMI audio to be output ?

Your external monitor is CRT so must be connected via VGA cable.
The video driver does not detect (presence detect) any screen or audio device connected by HDMI/DVI/DisplayPort.

Your "aplay -l" looks better, I expected 2 output codec converters.
**If you have an HDMI receiver** connected, hw:1,8 is likely the output device..
speaker-test -c 2 -r 48000 -D hw:1,8
cat /proc/asound/card1/eld#0.2
.
/card1/eld#0.2 is associated with hw:1,8 (only if you have **no** snd-hda-intel probe_mask)
.
No need to post the /var/log/Xorg.0.log  again..

---

### Post by shaolintl on 2011-09-15
> **BicyclerBoy said:**
> This may sound like a silly question but..
Where do you expect this HDMI audio to be output ?


Not a silly question at all and just show I dont understand anything about this. I hope I did not waste your time for nothing.

I hope to output the sound to the speakers/earphones but now that you asked, it seems to me a very stupid thing to wish. 

I will try to find a DVI cable to connect to my screen and check if it works.

I thought that using the HDMI will output better quality sound to the earphone output, I guess now this is not the case?

---

### Post by shaolintl on 2011-09-15
Anyway, I would like to thank you for your help. At least I understood at the end whats going on with the HDMI.

Thanks again.

---

### Post by BicyclerBoy on 2011-09-15
That's okay..
We have moved along to a position/status where HDA HDMI audio is possibly working..

You may have to use a HDMI cable or DVI-HDMI adapter to get the monitor/receiver to behave.
Your 1920x1200 monitor has an external analogue audio input jack...so it may not support any HDMI audio.

If the previously posted speaker-test works, there has to be an extra entry in /etc/pulse/default.pa to get the HDMI output device to appear in pulse-audio (pavucontrol, gnome sound preferences).

---

