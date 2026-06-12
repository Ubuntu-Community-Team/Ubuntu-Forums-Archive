---
title: "HDMI sound on monitor but not on TV"
date: 2011-05-13
forum: Multimedia Software
---

### Post by unwowed on 2011-05-13
Hello, I've got a very annoying problem with ION 330 MCP79 HTPC: the HDMI sound just doesn't work with PHILIPS LCD panel, but works fine with computer LCD monitor. I've tried following the numerous threads on those forums but in the end couldn't get any sound from TV. Sound plays fine if I plug it in windows 7 laptop.

Current system state:
BIOS settings for Azalia internal+external
Natty with all updates
Recompiled alsa 1.0.24 via alsa upgrade script
pulseaudio
probe_masked hdmi device (there're also analog and S/PDIF devices on Relatek chip, but they are not loaded with current configuration)
NVidia current (270.41.06)

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
alsamixer:
[http://imageshack.us/photo/my-images/4/alsamixer.png/](http://imageshack.us/photo/my-images/4/alsamixer.png/)

No sound and no errors wiwth all of those:
speaker-test -D plughw:0,3 -c 2
speaker-test -D hw:0,3 -c 2
speaker-test -D plughw:0,3 -c 2 -r 44100
speaker-test -D hw:0,3 -c 2 -r 44100
aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav

Same results were observed on ubuntu alsa 1.0.24

Please see attached files for additional system info

---

### Post by varunendra on 2011-05-14
Not a help at this moment, just copy-pasting your attached reports in a proper way to make them more readable:

alsa-info.txt:
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri May 13 08:41:28 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      nVidia
Product Name:      MCP79
Product Version:   To Be Filled By O.E.M.


!!Kernel Information
!!------------------

Kernel release:    2.6.38-9-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfae78000 irq 23


!!PCI Soundcards installed in the system
!!--------------------------------------

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:08.0 0403: 10de:0ac0 (rev b1)
    Subsystem: 10de:cb84


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=3stack-6ch-dig enable_msi=0 probe_mask=0x8
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : 0
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : 3stack-6ch-dig,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : 8,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Nvidia MCP79/7A HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0007
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  4 May 13 12:14 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  3 May 13 12:14 /dev/snd/hwC0D3
crw-rw----+ 1 root audio 116,  2 May 13 12:20 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  1 May 13 12:14 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 May 13 12:14 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May 13 12:14 .
drwxr-xr-x 3 root root 160 May 13 12:14 ..
lrwxrwxrwx 1 root root  12 May 13 12:14 pci-0000:00:08.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xfae78000 irq 23'
  Mixer name    : 'Nvidia MCP79/7A HDMI'
  Components    : 'HDA:10de0007,10de0101,00100100'
  Controls      : 5
  Simple ctrls  : 2
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.NVidia {
    control.1 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
parport_pc
ppdev
vesafb
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
binfmt_misc
snd_pcm
snd_seq_midi
rfcomm
snd_rawmidi
sco
bnep
l2cap
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
lib80211_crypt_tkip
nvidia
psmouse
snd
shpchp
wl
soundcore
snd_page_alloc
serio_raw
lib80211
btusb
bluetooth
joydev
rc_imon_pad
ir_lirc_codec
lirc_dev
ir_sony_decoder
ir_jvc_decoder
imon
ir_rc6_decoder
ir_rc5_decoder
ir_nec_decoder
rc_core
i2c_nforce2
lp
parport
usbhid
hid
usb_storage
uas
r8169
ahci
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x18560110
0x07 0x58560121
0x09 0x58560122
0x0b 0x58560123
0x0d 0x58560124

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   17.904552] Bluetooth: RFCOMM ver 1.11
[   18.492925] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   18.492945] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   18.495588] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   18.495610] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   18.495706] HDA Intel 0000:00:08.0: setting latency timer to 64
[   21.107151] vesafb: framebuffer at 0xf7000000, mapped to 0xf8680000, using 1216k, total 1216k
```

xorg.conf.txt:
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```


Xorg.0.log.txt:
```
[    21.647] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.647] X Protocol Version 11, Revision 0
[    21.647] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    21.647] Current Operating System: Linux ciibat-MCP79 2.6.38-9-generic-pae #43-Ubuntu SMP Thu Apr 28 17:12:11 UTC 2011 i686
[    21.647] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=24a13e07-3260-4b32-ab2e-49d25a6dffa2 ro quiet splash vt.handoff=7
[    21.648] Build Date: 19 April 2011  03:33:17PM
[    21.648] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    21.648] Current version of pixman: 0.20.2
[    21.648]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.648] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.649] (==) Log file: "/var/log/Xorg.0.log", Time: Fri May 13 12:14:43 2011
[    21.649] (==) Using config file: "/etc/X11/xorg.conf"
[    21.650] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.651] (==) No Layout section.  Using the first Screen section.
[    21.651] (**) |-->Screen "Default Screen" (0)
[    21.651] (**) |   |-->Monitor "<default monitor>"
[    21.652] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    21.652] (**) |   |-->Device "Default Device"
[    21.652] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    21.652] (==) Automatically adding devices
[    21.653] (==) Automatically enabling devices
[    21.653] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.653]     Entry deleted from font path.
[    21.654] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.654] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.654] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.654] (II) Loader magic: 0x81ffde0
[    21.654] (II) Module ABI versions:
[    21.654]     X.Org ANSI C Emulation: 0.4
[    21.654]     X.Org Video Driver: 10.0
[    21.654]     X.Org XInput driver : 12.3
[    21.654]     X.Org Server Extension : 5.0
[    21.658] (--) PCI:*(0:3:0:0) 10de:087d:10de:cb79 rev 177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
[    21.658] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.659] (II) "extmod" will be loaded by default.
[    21.659] (II) "dbe" will be loaded by default.
[    21.659] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    21.659] (II) "record" will be loaded by default.
[    21.659] (II) "dri" will be loaded by default.
[    21.659] (II) "dri2" will be loaded by default.
[    21.659] (II) LoadModule: "glx"
[    21.660] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.745] (II) Module glx: vendor="NVIDIA Corporation"
[    21.745]     compiled for 4.0.2, module version = 1.0.0
[    21.746]     Module class: X.Org Server Extension
[    21.746] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    21.746] (II) Loading extension GLX
[    21.746] (II) LoadModule: "extmod"
[    21.747] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.748] (II) Module extmod: vendor="X.Org Foundation"
[    21.748]     compiled for 1.10.1, module version = 1.0.0
[    21.748]     Module class: X.Org Server Extension
[    21.748]     ABI class: X.Org Server Extension, version 5.0
[    21.748] (II) Loading extension MIT-SCREEN-SAVER
[    21.748] (II) Loading extension XFree86-VidModeExtension
[    21.748] (II) Loading extension XFree86-DGA
[    21.748] (II) Loading extension DPMS
[    21.748] (II) Loading extension XVideo
[    21.748] (II) Loading extension XVideo-MotionCompensation
[    21.748] (II) Loading extension X-Resource
[    21.748] (II) LoadModule: "dbe"
[    21.749] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.750] (II) Module dbe: vendor="X.Org Foundation"
[    21.750]     compiled for 1.10.1, module version = 1.0.0
[    21.750]     Module class: X.Org Server Extension
[    21.750]     ABI class: X.Org Server Extension, version 5.0
[    21.750] (II) Loading extension DOUBLE-BUFFER
[    21.750] (II) LoadModule: "record"
[    21.751] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.751] (II) Module record: vendor="X.Org Foundation"
[    21.752]     compiled for 1.10.1, module version = 1.13.0
[    21.752]     Module class: X.Org Server Extension
[    21.752]     ABI class: X.Org Server Extension, version 5.0
[    21.752] (II) Loading extension RECORD
[    21.752] (II) LoadModule: "dri"
[    21.753] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.754] (II) Module dri: vendor="X.Org Foundation"
[    21.754]     compiled for 1.10.1, module version = 1.0.0
[    21.754]     ABI class: X.Org Server Extension, version 5.0
[    21.754] (II) Loading extension XFree86-DRI
[    21.754] (II) LoadModule: "dri2"
[    21.755] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.755] (II) Module dri2: vendor="X.Org Foundation"
[    21.755]     compiled for 1.10.1, module version = 1.2.0
[    21.756]     ABI class: X.Org Server Extension, version 5.0
[    21.756] (II) Loading extension DRI2
[    21.756] (II) LoadModule: "nvidia"
[    21.756] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.758] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.758]     compiled for 4.0.2, module version = 1.0.0
[    21.758]     Module class: X.Org Video Driver
[    21.759] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    21.759] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.759] (++) using VT number 7

[    21.759] (II) Loading sub module "fb"
[    21.760] (II) LoadModule: "fb"
[    21.760] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.761] (II) Module fb: vendor="X.Org Foundation"
[    21.761]     compiled for 1.10.1, module version = 1.0.0
[    21.761]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.761] (II) Loading sub module "wfb"
[    21.761] (II) LoadModule: "wfb"
[    21.762] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.762] (II) Module wfb: vendor="X.Org Foundation"
[    21.762]     compiled for 1.10.1, module version = 1.0.0
[    21.762]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.763] (II) Loading sub module "ramdac"
[    21.763] (II) LoadModule: "ramdac"
[    21.763] (II) Module "ramdac" already built-in
[    21.763] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.763] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.763] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.764] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    21.764] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.764] (==) NVIDIA(0): RGB weight 888
[    21.764] (==) NVIDIA(0): Default visual is TrueColor
[    21.764] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.764] (**) NVIDIA(0): Option "NoLogo" "True"
[    22.743] (II) NVIDIA(GPU-0): Display (Philips FTV (DFP-1)) supports NVIDIA 3D Vision
[    22.743] (II) NVIDIA(GPU-0):     stereo.
[    22.745] (II) NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
[    22.745] (--) NVIDIA(0): Memory: 524288 kBytes
[    22.746] (--) NVIDIA(0): VideoBIOS: 62.79.67.00.00
[    22.746] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.746] (--) NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0
[    22.746] (--) NVIDIA(0):     Philips FTV (DFP-1)
[    22.746] (--) NVIDIA(0): Philips FTV (DFP-1): 165.0 MHz maximum pixel clock
[    22.746] (--) NVIDIA(0): Philips FTV (DFP-1): Internal Single Link TMDS
[    22.752] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
[    22.752] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    22.752] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    22.752] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    22.752] (WW) NVIDIA(0):     check for mode "1920x1080".
[    22.752] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
[    22.752] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    22.752] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    22.752] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    22.752] (WW) NVIDIA(0):     check for mode "1920x1080".
[    22.752] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
[    22.753] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    22.753] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    22.753] (WW) NVIDIA(0):     this mode's VertRefresh (25.0 Hz); ignoring VertRefresh
[    22.753] (WW) NVIDIA(0):     check for mode "1920x1080".
[    22.753] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
[    22.753] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    22.753] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    22.753] (WW) NVIDIA(0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
[    22.753] (WW) NVIDIA(0):     check for mode "1920x1080".
[    22.753] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
[    22.754] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    22.754] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    22.754] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    22.754] (WW) NVIDIA(0):     check for mode "1920x1080".
[    22.756] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
[    22.757] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    22.757] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    22.757] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    22.757] (WW) NVIDIA(0):     check for mode "1920x1080".
[    22.757] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
[    22.757] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    22.757] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    22.757] (WW) NVIDIA(0):     this mode's VertRefresh (25.0 Hz); ignoring VertRefresh
[    22.757] (WW) NVIDIA(0):     check for mode "1920x1080".
[    22.758] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-1) contradicts itself: mode
[    22.758] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    22.758] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    22.758] (WW) NVIDIA(0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
[    22.758] (WW) NVIDIA(0):     check for mode "1920x1080".
[    22.847] (II) NVIDIA(0): Assigned Display Device: DFP-1
[    22.847] (==) NVIDIA(0): 
[    22.847] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    22.847] (==) NVIDIA(0):     will be used as the requested mode.
[    22.847] (==) NVIDIA(0): 
[    22.848] (II) NVIDIA(0): Validated modes:
[    22.848] (II) NVIDIA(0):     "nvidia-auto-select"
[    22.848] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    22.890] (--) NVIDIA(0): DPI set to (76, 76); computed from "UseEdidDpi" X config
[    22.890] (--) NVIDIA(0):     option
[    22.890] (--) Depth 24 pixmap format is 32 bpp
[    22.890] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    22.899] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    22.931] (II) Loading extension NV-GLX
[    23.006] (==) NVIDIA(0): Disabling shared memory pixmaps
[    23.006] (==) NVIDIA(0): Backing store disabled
[    23.006] (==) NVIDIA(0): Silken mouse enabled
[    23.007] (==) NVIDIA(0): DPMS enabled
[    23.007] (II) Loading extension NV-CONTROL
[    23.008] (II) Loading extension XINERAMA
[    23.008] (II) Loading sub module "dri2"
[    23.008] (II) LoadModule: "dri2"
[    23.009] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.009] (II) Module dri2: vendor="X.Org Foundation"
[    23.009]     compiled for 1.10.1, module version = 1.2.0
[    23.009]     ABI class: X.Org Server Extension, version 5.0
[    23.009] (II) NVIDIA(0): [DRI2] Setup complete
[    23.010] (==) RandR enabled
[    23.010] (II) Initializing built-in extension Generic Event Extension
[    23.010] (II) Initializing built-in extension SHAPE
[    23.010] (II) Initializing built-in extension MIT-SHM
[    23.010] (II) Initializing built-in extension XInputExtension
[    23.010] (II) Initializing built-in extension XTEST
[    23.010] (II) Initializing built-in extension BIG-REQUESTS
[    23.010] (II) Initializing built-in extension SYNC
[    23.010] (II) Initializing built-in extension XKEYBOARD
[    23.010] (II) Initializing built-in extension XC-MISC
[    23.010] (II) Initializing built-in extension SECURITY
[    23.010] (II) Initializing built-in extension XINERAMA
[    23.010] (II) Initializing built-in extension XFIXES
[    23.010] (II) Initializing built-in extension RENDER
[    23.010] (II) Initializing built-in extension RANDR
[    23.010] (II) Initializing built-in extension COMPOSITE
[    23.010] (II) Initializing built-in extension DAMAGE
[    23.010] (II) Initializing built-in extension GESTURE
[    23.010] (II) Initializing extension GLX
[    23.125] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.160] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.160] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.160] (II) LoadModule: "evdev"
[    23.161] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.162] (II) Module evdev: vendor="X.Org Foundation"
[    23.162]     compiled for 1.10.0.902, module version = 2.6.0
[    23.162]     Module class: X.Org XInput Driver
[    23.162]     ABI class: X.Org XInput driver, version 12.3
```

Reporting outputs in this way (by wrapping them in [ code].... [ /code] tags) makes them more readable + allows everyone to be able to see it, even if they are not logged in. Besides, those who are logged in but using windows (like I was moments ago :)) can't read the attached txt files properly because windows and linux use different methods to create and read text files.

Hope it helps drawing more attention to your problem. I'd love to see it solved.

---

### Post by lidex on 2011-05-14
If the hdmi audio works on one device and not another then it sounds like an issue of communication with the second device, not so much a problem of alsa or xorg.

From ubuntu help:
> Now that we have the info for the HDMI device, try a test, In the example below, 0 is the card number and 3 is the device number.

aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav

If aplay does not output any errors, but still no sound is heared, "reboot" the receiver, monitor or tv set. Since the HDMI interface executes a handshake on connection, it might have noticed before that there was no audio stream embedded, and disabled audio decoding.

If the test is successful, edit/create /etc/asound.conf to set HDMI as the default audio device, reboot, and audio should now work. 

---

### Post by mark.kendall on 2011-05-15
> **lidex said:**
> If the hdmi audio works on one device and not another then it sounds like an issue of communication with the second device, not so much a problem of alsa or xorg.

From ubuntu help:

I have the same problem as unwowed, sound works on a monitor with speakers plugged in but not on my TV.  Sound worked several years ago (nvidia 17x or 18x drivers) and I have tried reseting the tv (disconnected the power) to no avail.

My thread is at [http://ubuntuforums.org/showthread.php?t=1751425](http://ubuntuforums.org/showthread.php?t=1751425) and also more recently at [http://www.nvnews.net/vbulletin/showthread.php?p=2431905#post2431905](http://www.nvnews.net/vbulletin/showthread.php?p=2431905#post2431905)

---

### Post by unwowed on 2011-05-16
Well, it's really stupid but the solution was to downgrade the BIOS image. Sorry for bothering everyone over nothing. At least it drew some attention to Mark's problem. 

Do I mark thread as solved?

---

### Post by varunendra on 2011-05-19
> **unwowed said:**
> Well, it's really stupid but the solution was to downgrade the BIOS image. Sorry for bothering everyone over nothing. At least it drew some attention to Mark's problem. 

Do I mark thread as solved?
Well.., this leaves us clueless about what might have been changed (I suspect some weird BIOS settings). But since this suggests (or at least hints about) a 'potential' solution, I think you should mark it as [SOLVED].

---

### Post by mark.kendall on 2011-06-27
What bios version did this work with, I've just got 4 rom images from Zotac but unfortunately none of them solved this problem for me?

---

