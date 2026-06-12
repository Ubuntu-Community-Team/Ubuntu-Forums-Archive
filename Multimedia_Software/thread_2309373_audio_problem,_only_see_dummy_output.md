---
title: "audio problem, only see dummy output"
date: 2016-01-09
forum: Multimedia Software
---

### Post by rob141 on 2016-01-09
Hello everybody.

My audio always had worked before and it was the ati/HDMI output because i my laptop is connected to my tv with the hdmi cable.

today i had to temporarly disconnect it but then i lost all audio so i went to try to change the output to the laptop output instead of the hdmi but i think i just got think getting worst and worst by trying to install diferent audio application like pulse or something. not sure. Now it is reconected with the HDMI but the sound still did not comeback.


I have ubuntu 15.10 and XFCE

now if i do this:  [COLOR=#000000][FONT=Ubuntu Mono]pacmd list-cards   i get this:    [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]pacmd list-cards

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]if i do this:  [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]pacmd list-cards   i get this:  [/FONT][/COLOR]aplay: device_list:268: no soundcards found

[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]if i try to open the audio mixer, i get:    GStreamer was unable to detect any sound device

i tryed to re-install GStreamer but i dont think it did anything much :(

If i open for example VLC and go in the audio tab, all i see is: dummy output

What can i do to solve that problem please ?



I have juste tryed the command: lspci and here is wjat i get:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
**_02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]_**
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
05:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
```

In the list, i see the audio i should have but why it does not work ?

---

### Post by Yellow Pasque on 2016-01-12
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by rob141 on 2016-01-12
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

thank you for the reply, here is the output:


```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Wed Jan 13 01:19:35 UTC 2016




!!Linux Distribution
!!------------------


Ubuntu 15.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 15.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 15.10" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




!!DMI Information
!!---------------


Manufacturer:      Gateway        
Product Name:      NV59                           
Product Version:   V1.26          
Firmware Version:  V1.26          




!!Kernel Information
!!------------------


Kernel release:    4.2.0-23-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     
Library version:    1.0.29
Utilities version:  1.0.29




!!Loaded ALSA modules
!!-------------------






!!Sound Servers on this system
!!----------------------------


No sound servers found.




!!Soundcards recognised by ALSA
!!-----------------------------






!!PCI Soundcards installed in the system
!!--------------------------------------


00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1b.0 0403: 8086:3b56 (rev 05)
	Subsystem: 1025:033d
--
02:00.1 0403: 1002:aa60
	Subsystem: 1025:033d




!!Modprobe options (Sound related)
!!--------------------------------


snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2




!!Loaded sound module options
!!---------------------------




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116,  1 Jan 13  2016 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 13  2016 /dev/snd/timer




!!Aplay/Arecord output
!!--------------------


APLAY


aplay: device_list:268: no soundcards found...


ARECORD


arecord: device_list:268: no soundcards found...


!!Amixer output
!!-------------




!!Alsactl output
!!--------------


--startcollapse--
--endcollapse--




!!All Loaded Modules
!!------------------


Module
binfmt_misc
fglrx
arc4
ath9k
ath9k_common
ath9k_hw
ath
mac80211
intel_powerclamp
coretemp
uvcvideo
cfg80211
videobuf2_vmalloc
videobuf2_memops
kvm_intel
acer_wmi
videobuf2_core
sparse_keymap
v4l2_common
kvm
videodev
media
amd_iommu_v2
lpc_ich
input_leds
joydev
shpchp
mei_me
mac_hid
mei
serio_raw
parport_pc
ppdev
lp
parport
autofs4
hid_generic
usbhid
hid
uas
usb_storage
broadcom
psmouse
tg3
ahci
ptp
libahci
pps_core
wmi
video




!!ALSA/HDA dmesg
!!--------------
```

---

### Post by rob141 on 2016-01-15
If i do:

speaker-test

here is the output:

```
Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768: (parse_card) cannot find card '0'
ALSA lib conf.c:4260: (_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:4260: (_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251: (snd_func_refer) error evaluating name
ALSA lib conf.c:4260: (_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4739: (snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2267: (snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory
```

---

### Post by Yellow Pasque on 2016-01-15
> Driver version:     
Library version:    1.0.29
Utilities version:  1.0.29

One of the troubleshooting methods you tried borked the kernel module (it happens to the best of us ;P). Reinstalling the kernel image package should fix it. These commands will also reset pulseaudio's user configuration files so fresh ones get generated:
```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo modprobe snd-hda-intel
rm -r ~/.config/pulse*
pulseaudio -k
```

---

### Post by rob141 on 2016-01-15
WOW your a king :)  

I cant confirm 100% that it is working because i am  at work and connected to my laptop through teamviewer but now i can see my sound cart HDMI ATI  in vlc just for example and in alsamixer i can see the hda-intel sound card so i am pretty positive that it is finally working.

I will let you know as soon as i get home if it is really working.

Thank you so much for your help.  YOUR THE BEST !!!!!

---

### Post by rob141 on 2016-01-15
> **Temüjin said:**
> One of the troubleshooting methods you tried borked the kernel module (it happens to the best of us ;P). Reinstalling the kernel image package should fix it. These commands will also reset pulseaudio's user configuration files so fresh ones get generated:
```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo modprobe snd-hda-intel
rm -r ~/.config/pulse*
pulseaudio -k
```

Thank you very much, the sound is working but the only thing is that it use the intel sound card instead of the amd/ati HDMI !!  I need to have the HDMI sound working instead because my laptop is connected with hdmi to my tv. The hdmi works in vlc but not if i go on netflix.  How can i have the hdmi be the default sound for everything please ?

---

### Post by rob141 on 2016-01-15
```
 
Here is the new output:



upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Sat Jan 16 00:23:21 UTC 2016




!!Linux Distribution
!!------------------


Ubuntu 15.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 15.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 15.10" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




!!DMI Information
!!---------------


Manufacturer: Gateway 
Product Name: NV59 
Product Version: V1.26 
Firmware Version: V1.26 




!!Kernel Information
!!------------------


Kernel release: 4.2.0-23-generic
Operating System: GNU/Linux
Architecture: x86_64
Processor: x86_64
SMP Enabled: Yes




!!ALSA Version
!!------------


Driver version: k4.2.0-23-generic
Library version: 1.0.29
Utilities version: 1.0.29




!!Loaded ALSA modules
!!-------------------


snd_hda_intel
snd_hda_intel




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
Installed - Yes (/usr/bin/pulseaudio)
Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------


0 [MID ]: HDA-Intel - HDA Intel MID
HDA Intel MID at 0xf0600000 irq 29
1 [HDMI ]: HDA-Intel - HDA ATI HDMI
HDA ATI HDMI at 0xcfedc000 irq 30




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1b.0 0403: 8086:3b56 (rev 05)
    Subsystem: 1025:033d
--
02:00.1 0403: 1002:aa60
    Subsystem: 1025:033d




!!Modprobe options (Sound related)
!!--------------------------------


snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2




!!Loaded sound module options
!!---------------------------


!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : -1


!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : -1




!!HDA-Intel Codec information
!!---------------------------
--startcollapse--


Codec: Realtek ALC272X
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0272
Subsystem Id: 0x1025033d
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
rates [0x560]: 44100 48000 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
Power states: D0 D1 D2 D3 CLKSTOP
Power: setting=D0, actual=D0
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
Control: name="Headphone Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Device: name="ALC272X Analog", type="Audio", device=0
Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
Amp-Out vals: [0x00 0x00]
Converter: stream=5, channel=0
PCM:
rates [0x560]: 44100 48000 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
Control: name="Speaker Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
Amp-Out vals: [0x40 0x40]
Converter: stream=5, channel=0
PCM:
rates [0x560]: 44100 48000 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
Amp-Out vals: [0x40 0x40]
Converter: stream=0, channel=0
PCM:
rates [0x560]: 44100 48000 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
Control: name="IEC958 Playback Con Mask", index=0, device=0
Control: name="IEC958 Playback Pro Mask", index=0, device=0
Control: name="IEC958 Playback Default", index=0, device=0
Control: name="IEC958 Playback Switch", index=0, device=0
Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
Device: name="ALC272X Digital", type="SPDIF", device=1
Converter: stream=5, channel=0
Digital:
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
Control: name="Capture Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Control: name="Capture Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Device: name="ALC272X Analog", type="Audio", device=0
Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
Amp-In vals: [0x00 0x1f]
Converter: stream=1, channel=0
SDI-Select: 0
PCM:
rates [0x560]: 44100 48000 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
Amp-In vals: [0x8b 0x8b]
Converter: stream=0, channel=0
SDI-Select: 0
PCM:
rates [0x560]: 44100 48000 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Control: name="Internal Mic Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=1, ofs=0
Control: name="Internal Mic Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=1, ofs=0
Control: name="Mic Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Control: name="Mic Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Control: name="Beep Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=4, ofs=0
Control: name="Beep Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=4, ofs=0
Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-In vals: [0x00 0x00] [0x1f 0x1f] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
Connection: 8
0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x00 0x00] [0x00 0x00]
Connection: 2
0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x00 0x00] [0x00 0x00]
Connection: 2
0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x00 0x00] [0x80 0x80]
Connection: 2
0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x00] [0x80]
Connection: 2
0x02 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400700: Mono Digital
Pincap 0x00000010: OUT
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
Pincap 0x00000020: IN
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x00:
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400401: Stereo
Pincap 0x00000020: IN
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x00:
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
Control: name="Speaker Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Pincap 0x0001003c: IN OUT HP EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
Conn = ATAPI, Color = Unknown
DefAssociation = 0x1, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 2
0x0c 0x0d*
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x0001003c: IN OUT HP EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Unsolicited: tag=00, enabled=0
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 2
0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00000034: IN OUT Detect
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Unsolicited: tag=00, enabled=0
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x0e
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80]
Pincap 0x00000010: OUT
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x00:
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
Control: name="Mic Boost Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x00 0x00]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00001734: IN OUT Detect
Vref caps: HIZ 50 GRD 80
Pin Default 0x03a19840: [Jack] Mic at Ext Left
Conn = 1/8, Color = Pink
DefAssociation = 0x4, Sequence = 0x0
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=02, enabled=1
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x0e
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
Control: name="Internal Mic Boost Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x00 0x00]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x0000173c: IN OUT HP Detect
Vref caps: HIZ 50 GRD 80
Pin Default 0x99a30930: [Fixed] Mic at Int ATAPI
Conn = ATAPI, Color = Unknown
DefAssociation = 0x3, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=00, enabled=0
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 3
0x0c* 0x0d 0x0e
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x00 0x00]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00001734: IN OUT Detect
Vref caps: HIZ 50 GRD 80
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN VREF_HIZ
Unsolicited: tag=00, enabled=0
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x0d
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x00 0x00]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x0000173c: IN OUT HP Detect
Vref caps: HIZ 50 GRD 80
Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN VREF_HIZ
Unsolicited: tag=00, enabled=0
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 3
0x0c* 0x0d 0x0e
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
Pincap 0x00000020: IN
Pin Default 0x4016892d: [N/A] Speaker at Ext N/A
Conn = Digital, Color = Purple
DefAssociation = 0x2, Sequence = 0xd
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400780: Mono Digital
Pincap 0x00000014: OUT Detect
Pin Default 0x03451120: [Jack] SPDIF Out at Ext Left
Conn = Optical, Color = Black
DefAssociation = 0x2, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
Processing caps: benign=0, ncoeff=17
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
Control: name="Headphone Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x0000001c: OUT HP Detect
Pin Default 0x0321101f: [Jack] HP Out at Ext Left
Conn = 1/8, Color = Black
DefAssociation = 0x1, Sequence = 0xf
Pin-ctls: 0xc0: OUT HP
Unsolicited: tag=01, enabled=1
Power states: D0 D1 D2 D3 EPSS
Power: setting=D0, actual=D0
Connection: 3
0x0c* 0x0d 0x0e
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
Connection: 10
0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
Connection: 10
0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x13
Codec: Conexant ID 2c06
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x14f12c06
Subsystem Id: 0x10250093
Revision Id: 0x100000
Modem Function Group: 0x2
Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
rates [0x70]: 32000 44100 48000
bits [0x2]: 16
formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
Power states: D0 D3
Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
Converter: stream=1, channel=0
Digital: Enabled GenLevel
Digital category: 0x2
IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
Control: name="IEC958 Playback Con Mask", index=0, device=0
Control: name="IEC958 Playback Pro Mask", index=0, device=0
Control: name="IEC958 Playback Default", index=0, device=0
Control: name="IEC958 Playback Switch", index=0, device=0
Control: name="ELD", index=0, device=3
Pincap 0x00000094: OUT Detect HDMI
Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
Conn = Digital, Color = Unknown
DefAssociation = 0x1, Sequence = 0x0
Pin-ctls: 0x40: OUT
Unsolicited: tag=01, enabled=1
Connection: 1
0x02
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116, 5 Jan 15 19:08 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 2 Jan 15 19:08 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 9 Jan 15 19:08 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 10 Jan 15 19:08 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116, 4 Jan 15 19:08 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 7 Jan 15 19:10 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 6 Jan 15 19:14 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 8 Jan 15 19:10 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 3 Jan 15 19:11 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116, 1 Jan 16 2016 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 15 19:08 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 80 Jan 15 19:08 .
drwxr-xr-x 3 root root 280 Jan 15 19:08 ..
lrwxrwxrwx 1 root root 12 Jan 15 19:08 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root 12 Jan 15 19:08 pci-0000:02:00.1 -> ../controlC1




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC272X Analog [ALC272X Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 1: ALC272X Digital [ALC272X Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC272X Analog [ALC272X Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [MID]


Card hw:0 'MID'/'HDA Intel MID at 0xf0600000 irq 29'
Mixer name    : 'Realtek ALC272X'
Components    : 'HDA:10ec0272,1025033d,00100001 HDA:14f12c06,10250093,00100000'
Controls : 31
Simple ctrls : 13
Simple mixer control 'Master',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 64
Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 64
Mono:
Front Left: Playback 0 [0%] [-64.00dB] [off]
Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Speaker',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 64
Mono:
Front Left: Playback 64 [100%] [0.00dB] [on]
Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
Capabilities: pvolume
Playback channels: Front Left - Front Right
Limits: Playback 0 - 255
Mono:
Front Left: Playback 255 [100%] [0.00dB]
Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 0 [0%] [-34.50dB] [on]
Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Mic Boost',0
Capabilities: volume
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 3
Front Left: 0 [0%] [0.00dB]
Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Beep',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 0 [0%] [-34.50dB] [off]
Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch
Capture channels: Front Left - Front Right
Limits: Capture 0 - 31
Front Left: Capture 0 [0%] [-16.50dB] [on]
Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
Capabilities: enum
Items: 'Disabled' 'Enabled'
Item0: 'Disabled'
Simple mixer control 'Internal Mic',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 31 [100%] [12.00dB] [on]
Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Internal Mic Boost',0
Capabilities: volume
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 3
Front Left: 0 [0%] [0.00dB]
Front Right: 0 [0%] [0.00dB]


!!-------Mixer controls for card 1 [HDMI]


Card hw:1 'HDMI'/'HDA ATI HDMI at 0xcfedc000 irq 30'
Mixer name    : 'ATI R6xx HDMI'
Components    : 'HDA:1002aa01,00aa0100,00100200'
Controls : 7
Simple ctrls : 1
Simple mixer control 'IEC958',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [on]




!!Alsactl output
!!--------------


--startcollapse--
state.MID {
    control.1 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 -6400
            dbvalue.1 -6400
        }
    }
    control.2 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Internal Mic Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 1200
            dbvalue.1 1200
        }
    }
    control.6 {
        iface MIXER
        name 'Internal Mic Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.7 {
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.8 {
        iface MIXER
        name 'Mic Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.9 {
        iface MIXER
        name 'Auto-Mute Mode'
        value Disabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.10 {
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1650
            dbmax 3000
            dbvalue.0 -1650
            dbvalue.1 3000
        }
    }
    control.11 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.12 {
        iface MIXER
        name 'Internal Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.13 {
        iface MIXER
        name 'Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.14 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.15 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.16 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.17 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.19 {
        iface MIXER
        name 'Master Playback Volume'
        value 64
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 0
        }
    }
    control.20 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface CARD
        name 'Internal Mic Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.22 {
        iface CARD
        name 'Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface CARD
        name 'Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.24 {
        iface CARD
        name 'Speaker Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.25 {
        iface CARD
        name 'SPDIF Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'Beep Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.27 {
        iface MIXER
        name 'Beep Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.28 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.29 {
        iface PCM
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.30 {
        iface PCM
        device 1
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.31 {
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
state.HDMI {
    control.1 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface PCM
        device 3
        name ELD
        value '100005000010000100000000000000000000000009070700'
        comment {
            access 'read volatile'
            type BYTES
            count 24
        }
    }
    control.7 {
        iface PCM
        device 3
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write'
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
}
--endcollapse--




!!All Loaded Modules
!!------------------


Module
snd_hda_codec_realtek
snd_hda_codec_generic
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hda_core
snd_hwdep
snd_pcm
snd_timer
snd
soundcore
nls_utf8
btrfs
xor
raid6_pq
ufs
qnx4
hfsplus
hfs
minix
ntfs
msdos
jfs
xfs
libcrc32c
cpuid
drbg
ansi_cprng
ctr
ccm
binfmt_misc
fglrx
arc4
uvcvideo
ath9k
ath9k_common
videobuf2_vmalloc
ath9k_hw
ath
videobuf2_memops
mac80211
videobuf2_core
v4l2_common
videodev
intel_powerclamp
acer_wmi
sparse_keymap
media
cfg80211
coretemp
kvm_intel
mei_me
mei
amd_iommu_v2
kvm
joydev
input_leds
serio_raw
lpc_ich
shpchp
mac_hid
parport_pc
ppdev
lp
parport
autofs4
hid_generic
usbhid
hid
uas
usb_storage
broadcom
psmouse
ahci
tg3
libahci
ptp
pps_core
wmi
video




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x411111f0
0x13 0x411111f0
0x14 0x99130110
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x03a19840
0x19 0x99a30930
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x4016892d
0x1e 0x03451120
0x21 0x0321101f


/sys/class/sound/hwC0D0/driver_pin_configs:


/sys/class/sound/hwC0D0/user_pin_configs:


/sys/class/sound/hwC0D0/init_verbs:


/sys/class/sound/hwC0D0/hints:


/sys/class/sound/hwC0D1/init_pin_configs:


/sys/class/sound/hwC0D1/driver_pin_configs:


/sys/class/sound/hwC0D1/user_pin_configs:


/sys/class/sound/hwC0D1/init_verbs:


/sys/class/sound/hwC0D1/hints:


/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010


/sys/class/sound/hwC1D0/driver_pin_configs:


/sys/class/sound/hwC1D0/user_pin_configs:


/sys/class/sound/hwC1D0/init_verbs:


/sys/class/sound/hwC1D0/hints:




!!ALSA/HDA dmesg
!!--------------


[ 252.526046] hfs: can't find a HFS filesystem on dev sda4
[ 287.478958] snd_hda_intel 0000:02:00.1: Handle VGA-switcheroo audio client
[ 287.493931] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:02:00.1/sound/card1/input13
[ 287.503934] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC272X: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[ 287.503941] snd_hda_codec_realtek hdaudioC0D0: speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[ 287.503946] snd_hda_codec_realtek hdaudioC0D0: hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[ 287.503949] snd_hda_codec_realtek hdaudioC0D0: mono: mono_out=0x0
[ 287.503951] snd_hda_codec_realtek hdaudioC0D0: dig-out=0x1e/0x0
[ 287.503954] snd_hda_codec_realtek hdaudioC0D0: inputs:
[ 287.503958] snd_hda_codec_realtek hdaudioC0D0: Internal Mic=0x19
[ 287.503961] snd_hda_codec_realtek hdaudioC0D0: Mic=0x18
[ 287.518166] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[ 287.518679] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[ 598.711767] perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000 

```

---

### Post by rob141 on 2016-01-15
> **rob141 said:**
> Thank you very much, the sound is working but the only thing is that it use the intel sound card instead of the amd/ati HDMI !!  I need to have the HDMI sound working instead because my laptop is connected with hdmi to my tv. The hdmi works in vlc but not if i go on netflix.  How can i have the hdmi be the default sound for everything please ?

there is also another problem, everytime i reboot, i have to do this:  [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe snd-hda-intel

or else i have no sound at all again. 

May i still have your help please for the no sound at reboot and to have the default ati hdmi sound card working instead of the intel one please ?


[/FONT][/COLOR]

---

### Post by rob141 on 2016-01-15
I have just made some other test and its weird.

the sound is still working ok in VLC, i can choose the ati hdmi sound and its all fine.

I have also the application Kodi and i can also choose the sound card ati HDMI in kodi and it is working fine

so actually the only place  ( i think ) the sound does not work ok is over the internet and i use google chrome.

so right now the problem is still the NO SOUND at all after every reboot ( until i do: [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe snd-hda-intel ) [/FONT][/COLOR]and no sound on the internet.  

May i have your help for this please ?

---

### Post by Bucky Ball on 2016-01-16
CODE TAGS PLEASE! Slickymaster added them to your first post, please add them to your post #8. It is a waste of space, hard to read as disjointed, and does not help your chances of support. Code tags will keep the original formatting. 

See the link in my signature below for how to add code tags and please use them now and in the future. Thanks.

---

### Post by rob141 on 2016-01-18
Here is the output of:

pacmd list-cards:

```

    index: 0
	name: <alsa_card.pci-0000_02_00.1>
	driver: <module-alsa-card.c>
	owner module: 21
	properties:
		alsa.card = "1"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xcfedc000 irq 30"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:02:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:02:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
		device.product.id = "aa60"
		device.product.name = "Redwood HDMI Audio [Radeon HD 5000 Series] (Mobility Radeon HD 5650)"
		device.string = "1"
		device.description = "Redwood HDMI Audio [Radeon HD 5000 Series] (Mobility Radeon HD 5650)"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: unknown)
		off: Off (priority 0, available: unknown)
	active profile: <output:hdmi-stereo>
	sinks:
		alsa_output.pci-0000_02_00.1.hdmi-stereo/#1: Redwood HDMI Audio [Radeon HD 5000 Series] (Mobility Radeon HD 5650) Digital Stereo (HDMI)
	sources:
		alsa_output.pci-0000_02_00.1.hdmi-stereo.monitor/#1: Monitor of Redwood HDMI Audio [Radeon HD 5000 Series] (Mobility Radeon HD 5650) Digital Stereo (HDMI)
	ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
			properties:
				device.icon_name = "video-display"
    index: 1
	name: <alsa_card.pci-0000_00_1b.0>
	driver: <module-alsa-card.c>
	owner module: 22
	properties:
		alsa.card = "0"
		alsa.card_name = "HDA Intel MID"
		alsa.long_card_name = "HDA Intel MID at 0xf0600000 irq 29"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "3b56"
		device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Built-in Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
		output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
		output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500, available: unknown)
		output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5560, available: unknown)
		off: Off (priority 0, available: unknown)
	active profile: <output:analog-stereo+input:analog-stereo>
	sinks:
		alsa_output.pci-0000_00_1b.0.analog-stereo/#2: Built-in Audio Analog Stereo
	sources:
		alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#2: Monitor of Built-in Audio Analog Stereo
		alsa_input.pci-0000_00_1b.0.analog-stereo/#3: Built-in Audio Analog Stereo
	ports:
		analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
			properties:
				device.icon_name = "audio-speakers"
		analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-headphones"
		iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
			properties:

```

How do i make my ati card the default one and to stay this way after a reboot please ??

---

### Post by Yellow Pasque on 2016-01-19
Are you using the onboard audio at all? If not, the easy way is to disable that, either through your BIOS or by using:
```
echo "options snd-hda-intel enable=0,1" | sudo tee -a /etc/modprobe.d/hdmidefault.conf
```

---

### Post by rob141 on 2016-01-19
> **Temüjin said:**
> Are you using the onboard audio at all? If not, the easy way is to disable that, either through your BIOS or by using:
```
echo "options snd-hda-intel enable=0,1" | sudo tee -a /etc/modprobe.d/hdmidefault.conf
```

Thank you so much, your code did work to have the default ati sound outpout.

But after a reboot, the sound was back to default dummy output and i had to do this:

```

sudo modprobe snd-hda-codec-hdmi

```

then this:
```

sudo modprobe snd-hda-intel

```

to have the sound back working and its still the right ati output.

Now my last concern is how can it stay this way ( it is even working now on the web like on netflix ) even after a reboot please ?

---

### Post by Yellow Pasque on 2016-01-21
I have no idea why you manually have to load the modules. It's probably related to something you did when trying to fix the original issue. Maybe the answer is in dmesg. Run this after reboot before you load the modules:
```
dmesg | grep -i snd
```

You might be able to work around the issue by setting the modules to load at boot:
```
echo "snd-hda-intel" | sudo tee -a /etc/modules
echo "snd-hda-codec-hdmi" | sudo tee -a /etc/modules
```

---

### Post by rob141 on 2016-01-21
> **Temüjin said:**
> I have no idea why you manually have to load the modules. It's probably related to something you did when trying to fix the original issue. Maybe the answer is in dmesg. Run this after reboot before you load the modules:
```
dmesg | grep -i snd
```

You might be able to work around the issue by setting the modules to load at boot:
```
echo "snd-hda-intel" | sudo tee -a /etc/modules
echo "snd-hda-codec-hdmi" | sudo tee -a /etc/modules
```


Thnks but it did not work this time.

I have first rebooted then i did your first code but nothing happened, still the default dummy output.

Then i did your 2 other codes and rebooted again and still have the dummy output. So i had again to manually load the module ati first the intel after in order to have the default ati output working.

Maybe it would work with a simple script that load the ati module first then the intel module on every boot ? Could that do the trick ?  I just dont know how to make a script and to have it execute by it-self on every boot ?

---

### Post by rob141 on 2016-01-27
I still need help please. The problem is not completely solved !!  After each reboot i am back to default dummy output.

How can i either fix this or how can i make a script that will run automatically on each boot and that script would run these 2 commands in order:

1- [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe snd-hda-codec-hdmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]2-[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe snd-hda-intel[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2016-01-27
Try putting the commands in /etc/rc.local
```
gksu mousepad /etc/rc.local
```

---

### Post by rob141 on 2016-01-28
> **Temüjin said:**
> Try putting the commands in /etc/rc.local
```
gksu mousepad /etc/rc.local
```


Do i put he 2 commands before the:

exit 0


and do i put them as is or do i put gksu instead of sudo ?

i am asking because i really dont want to accidently mess something up loll.

---

### Post by Yellow Pasque on 2016-01-29
> **rob141 said:**
> Do i put the 2 commands before the exit 0
Yes.


> and do i put them as is or do i put gksu instead of sudo ?
rc.local will be run with root permissions so you don't need either one. Just put the two commands between the last comment and exit 0
```
# By default this script does nothing.

modprobe snd-hda-codec-hdmi
modprobe snd-hda-intel

exit 0
```

---

### Post by rob141 on 2016-02-03
YYYYYYYYEEEEEEEEEEEESSSSSSSSSSSSSS  !!!!!!!!!!! ITS WORKING 

YOUR REALLY THE BEST !!!!!


wow thank you so so so much for all your help.

I dont know where your from Temujin but i honestly wish you were from Montreal so we could meet so i could pay you a beer or more then one loll.

Thank you again for everything ;)

---

### Post by faddat on 2016-02-29
All I needed was the modprobe part, and thank you!

---

### Post by emal011 on 2016-03-24
> **Temüjin said:**
> One of the troubleshooting methods you tried borked the kernel module (it happens to the best of us ;P). Reinstalling the kernel image package should fix it. These commands will also reset pulseaudio's user configuration files so fresh ones get generated:
```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo modprobe snd-hda-intel
rm -r ~/.config/pulse*
pulseaudio -k
```

Hi, I'm having the same issue with my audio output. At the beggining I use your tip and it works, after a reboot everything was the same, dummy output. Even if I write sudo *modprobe snd-hda-intel* again, it does'nt work anymore. Can I have some help here please?

```
2 card(s) available.
    index: 0
        name: <alsa_card.pci-0000_00_1b.0>
        driver: <module-alsa-card.c>
        owner module: 20
        properties:
                alsa.card = "0"
                alsa.card_name = "HDA Intel PCH"
                alsa.long_card_name = "HDA Intel PCH at 0xfb020000 irq 33"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "1c20"
                device.product.name = "6 Series/C200 Series Chipset Family High Definition Audio Controller"
                device.form_factor = "internal"
                device.string = "0"
                device.description = "Internes Audio"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        profiles:
                input:analog-stereo: Analog Stereo Eingang (priority 60, available: unknown)
                output:analog-stereo: Analog Stereo Ausgang (priority 6000, available: unknown)
                output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
                off: Aus (priority 0, available: unknown)
        active profile: <output:analog-stereo+input:analog-stereo>
        ports:
                analog-input-mic: Mikrofon (priority 8700, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: yes)                                                                                         
                        properties:                                                           
                                                                                              
                analog-output-lineout: Line-Ausgang (priority 9900, latency offset 0 usec, available: yes)                                                                                  
                        properties:                                                           
                                                                                              
                analog-output-speaker: Lautsprecher (priority 10000, latency offset 0 usec, available: no)                                                                                  
                        properties:                                                           
                                device.icon_name = "audio-speakers"                           
                analog-output-headphones: Analoge Kopfhörer (priority 9000, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "audio-headphones"
    index: 1
        name: <alsa_card.pci-0000_01_00.1>
        driver: <module-alsa-card.c>
        owner module: 21
        properties:
                alsa.card = "1"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:01:00.1"
                sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
                device.bus = "pci"
                device.vendor.id = "10de"
                device.vendor.name = "NVIDIA Corporation"
                device.product.id = "0be3"
                device.product.name = "High Definition Audio Controller"
                device.string = "1"
                device.description = "High Definition Audio Controller"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        profiles:
                output:hdmi-stereo: Digital Stereo (HDMI) Ausgang (priority 5400, available: unknown)
                off: Aus (priority 0, available: unknown)
        active profile: <output:hdmi-stereo>
```

As you can see it detect my 2 audio sources, one of them is from my Nvidia graphics card, but I use the internal audio(or I want to use the internal one). As I said, it works but not anymore..

My settings are: Kubuntu 15.10 x64

Thanks in advance.

ML

---

Edit: I found a solution and it works even after a reboot!!

```
sudo adduser $USER audio
```

---

