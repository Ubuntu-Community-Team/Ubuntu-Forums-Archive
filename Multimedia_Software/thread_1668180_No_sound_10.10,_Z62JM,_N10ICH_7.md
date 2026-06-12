---
title: "No sound 10.10, Z62JM, N10/ICH 7"
date: 2011-01-16
forum: Multimedia Software
---

### Post by G. Ross on 2011-01-16
Hi, total newb here - been decades since I used unix, much less linux.  Installed Ubuntu 10.10 Maverick Meerkat, works great except for no sound.  I have tried many of the suggestions in these threads but to no avail.  I notice many are for soundcards that I do not have.  Here is my data:

sudo lshw -c sound

  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:44 memory:febfc000-febfffff


00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 1297
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

This computer is a Z62JM, I think it is an ASUS, not sure.  Everything is working fantastically otherwise and I am SO VERY eager to be done with Windows.

 "Help me Ubuntu Ninjas, you're my only hope" (yeah - StarWars..)

---

### Post by lidex on 2011-01-16
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by G. Ross on 2011-01-16
Thanks lidex, this is something new that I have not done.  I ran the code and got


--2011-01-16 10:12:57--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-01-16 10:12:59--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 27247 (27K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,247      44.6K/s   in 0.6s    

2011-01-16 10:13:02 (44.6 KB/s) - `alsa-info.sh' saved [27247/27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : Y


Your ALSA information is in /tmp/alsa-info.txt.YZIA8eKEhU




That was interesting.  The contents of the file reads as follows:





upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Jan 16 18:13:03 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer Inc. 
Product Name:      Z62JM               
Product Version:   1.0       


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 1043:1297
--
	Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-


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


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1986A
Address: 0
Function Id: 0x1
Vendor Id: 0x11d41986
Subsystem Id: 0x10431443
Revision Id: 0x100500
No Modem Function Group found
Default PCM:
    rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
GPIO: io=0, o=1, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="AD198x Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x60]: 44100 48000
    bits [0x2]: 16
    formats [0x5]: PCM AC3
  Delay: 3 samples
  Connection: 2
     0x01* 0x06
Node 0x03 [Audio Output] wcaps 0x44d: Stereo Amp-Out
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="PCM Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="AD198x Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1c 0x1c]
  Converter: stream=8, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Processing caps: benign=1, ncoeff=70
Node 0x04 [Audio Output] wcaps 0x40d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x40d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x06 [Audio Input] wcaps 0x100511: Stereo
  Device: name="AD198x Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x07 [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 8
     0x03 0x09 0x13 0x14 0x15 0x16 0x17 0x18
Node 0x08 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x07
Node 0x09 [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80] [0x80]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Connection: 2
     0x04 0x05
Node 0x0a [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x07* 0x04 0x05
Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x07* 0x04
Node 0x0c [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x04* 0x07
Node 0x0d [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x05* 0x08
Node 0x0e [Audio Selector] wcaps 0x300100: Mono
  Connection: 2
     0x08* 0x11
Node 0x0f [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 8
     0x1f* 0x20 0x1d 0x1d 0x27 0x28 0x29 0x2a
Node 0x10 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x20* 0x1c 0x1f
Node 0x11 [Audio Selector] wcaps 0x300941: Stereo R/L
  Connection: 2
     0x0f* 0x2b
  Processing caps: benign=1, ncoeff=0
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Source", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 0
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x11
Node 0x14 [Audio Selector] wcaps 0x30010c: Mono Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80]
  Connection: 1
     0x23
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x22
Node 0x16 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x21
Node 0x17 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Internal Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Internal Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x10
Node 0x18 [Audio Selector] wcaps 0x30010c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x8f]
  Connection: 2
     0x19* 0x24
Node 0x19 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x1a [Pin Complex] wcaps 0x400185: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
  Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x1b [Pin Complex] wcaps 0x400185: Stereo Amp-Out
  Control: name="External Amplifier", index=0, device=0
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Pincap 0x0001001f: OUT HP EAPD Detect Trigger ImpSense
  EAPD 0x0:
  Pin Default 0x9117f110: [Fixed] Speaker at Int Rear
    Conn = Analog, Color = Other
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0b
Node 0x1c [Pin Complex] wcaps 0x400185: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x410110f0: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
Node 0x1d [Pin Complex] wcaps 0x400985: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x91a19121: [Fixed] Mic at Int Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0d
Node 0x1e [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411711f0: [N/A] Speaker at Ext Rear
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x1f [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a19020: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x20 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x418130f0: [N/A] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x21 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000027: IN Detect Trigger ImpSense
  Pin Default 0x5993e1f0: [N/A] Aux at Int ATAPI
    Conn = ATAPI, Color = White
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x22 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x9933112e: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0x2, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x23 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x59b370f0: [N/A] Telephony at Int ATAPI
    Conn = ATAPI, Color = Yellow
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x24 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x93f711f0: [Fixed] Other at Int Left
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x25 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x0145f1f0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Other
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x26 [Power Widget] wcaps 0x500500: Mono
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 8
     0x07 0x08 0x13 0x14 0x15 0x16 0x17 0x18
Node 0x27 [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 2
     0x1f 0x1d
Node 0x28 [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 2
     0x1f 0x20
Node 0x29 [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 2
     0x1d 0x20
Node 0x2a [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 3
     0x1f 0x1d 0x20
Node 0x2b [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x0f
Codec: Conexant ID 2bfa
Address: 1
Function Id: 0x2
Vendor Id: 0x14f12bfa
Subsystem Id: 0x10431966
Revision Id: 0x90000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 9 Jan 15 21:00 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 8 Jan 15 21:00 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 7 Jan 15 21:00 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116, 6 Jan 15 21:00 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 5 Jan 15 21:43 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 4 Jan 15 21:00 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 3 Jan 15 21:00 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jan 15 21:00 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 15 21:00 .
drwxr-xr-x 3 root root 220 Jan 15 21:00 ..
lrwxrwxrwx 1 root root  12 Jan 15 21:00 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfebfc000 irq 44'
  Mixer name	: 'Analog Devices AD1986A'
  Components	: 'HDA:11d41986,10431443,00100500 HDA:14f12bfa,10431966,00090000'
  Controls      : 20
  Simple ctrls  : 11
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [7.50dB] [on]
  Front Right: Playback 28 [90%] [7.50dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [on]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 31
		value.1 31
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 28
		value.1 28
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mic Boost'
		value.0 0
		value.1 0
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Internal Mic'
		comment.item.2 Mix
		iface MIXER
		name 'Capture Source'
		value Mic
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Internal Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Internal Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.14 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.15 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.16 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value 15
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Beep Playback Switch'
		value false
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
binfmt_misc
rfcomm
sco
bnep
l2cap
dm_crypt
snd_hda_codec_analog
tpm_infineon
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
iwl3945
snd_seq_midi
iwlcore
snd_rawmidi
snd_seq_midi_event
snd_seq
gspca_vc032x
gspca_main
videodev
tpm_tis
tpm
pcmcia
asus_laptop
snd_timer
snd_seq_device
ppdev
yenta_socket
v4l1_compat
joydev
tpm_bios
lp
parport_pc
pcmcia_rsrc
snd
sparse_keymap
pcmcia_core
btusb
parport
soundcore
mac80211
cfg80211
bluetooth
psmouse
serio_raw
snd_page_alloc
usbhid
hid
nouveau
ttm
drm_kms_helper
drm
video
output
firewire_ohci
intel_agp
sdhci_pci
r8169
firewire_core
mii
sdhci
led_class
crc_itu_t
agpgart
i2c_algo_bit


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x1a 0x0121401f
0x1b 0x9117f110
0x1c 0x410110f0
0x1d 0x91a19121
0x1e 0x411711f0
0x1f 0x02a19020
0x20 0x418130f0
0x21 0x5993e1f0
0x22 0x9933112e
0x23 0x59b370f0
0x24 0x93f711f0
0x25 0x0145f1f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a0000

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   10.225746] type=1400 audit(1295154010.081:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=827 comm="apparmor_parser"
[   10.345484] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.345542]   alloc irq_desc for 44 on node -1
[   10.345545]   alloc kstat_irqs on node -1
[   10.345560] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   10.345593] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.192413] phy0: Selected rate control algorithm 'iwl-3945-rs'
--
[ 8195.668975] [drm] nouveau 0000:01:00.0: Suspending GPU objects...
[ 8195.853130] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 8195.869021] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 226.594 msecs
[ 8195.901858] [drm] nouveau 0000:01:00.0: And we're gone!
--
[ 8196.909555] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 8196.909610] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[ 8196.909617] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 8196.909652] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
--
[ 8196.941696] PM: early resume of devices complete after 32.287 msecs
[ 8196.941784] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 8196.941793] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 8196.941844] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 8196.941847] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
--
[ 8215.754340] lo: Disabled Privacy Extensions
[ 8354.104868] hda_codec: invalid CONNECT_LIST verb 12[2]:2100



I am sorry that I do not know how to post that in a separate window, I will try and figure that out.  I am pretty sure I did some things with the ALSA driver using snd_hda_intel before, but maybe this means more to you than I.  Haha.

Does this help you in debugging?

---

### Post by G. Ross on 2011-01-16
Thanks lidex, this is something new that I have not done. I ran the code and got


--2011-01-16 10:12:57-- [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh](http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh) [following]
--2011-01-16 10:12:59-- [http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh](http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 27247 (27K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,247 44.6K/s in 0.6s 

2011-01-16 10:13:02 (44.6 KB/s) - `alsa-info.sh' saved [27247/27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

dmesg
lspci
lsmod
aplay
amixer
alsactl
/proc/asound/
/sys/class/sound/
~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : Y


Your ALSA information is in /tmp/alsa-info.txt.YZIA8eKEhU




That was interesting. The contents of the file reads as follows:





upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Jan 16 18:13:03 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer: ASUSTeK Computer Inc. 
Product Name: Z62JM 
Product Version: 1.0 


!!Kernel Information
!!------------------

Kernel release: 2.6.35-24-generic
Operating System: GNU/Linux
Architecture: i686
Processor: unknown
SMP Enabled: Yes


!!ALSA Version
!!------------

Driver version: 1.0.23
Library version: 1.0.23
Utilities version: 1.0.23


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

0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xfebfc000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
Subsystem: 1043:1297
--
Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-


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


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y, Y,Y,Y,Y,Y,Y,Y
enable_msi : -1
id : (null),(null),(null),(null),(null),(null),(null),( null),(null),(null),(null),(null),(null),(null),(n ull),(null),(null),(null),(null),(null),(null),(nu ll),(null),(null),(null),(null),(null),(null),(nul l),(null),(null),(null)
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
model : (null),(null),(null),(null),(null),(null),(null),( null),(null),(null),(null),(null),(null),(null),(n ull),(null),(null),(null),(null),(null),(null),(nu ll),(null),(null),(null),(null),(null),(null),(nul l),(null),(null),(null)
patch : (null),(null),(null),(null),(null),(null),(null),( null),(null),(null),(null),(null),(null),(null),(n ull),(null),(null),(null),(null),(null),(null),(nu ll),(null),(null),(null),(null),(null),(null),(nul l),(null),(null),(null)
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1986A
Address: 0
Function Id: 0x1
Vendor Id: 0x11d41986
Subsystem Id: 0x10431443
Revision Id: 0x100500
No Modem Function Group found
Default PCM:
rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
GPIO: io=0, o=1, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
Control: name="IEC958 Playback Con Mask", index=0, device=0
Control: name="IEC958 Playback Pro Mask", index=0, device=0
Control: name="IEC958 Playback Default", index=0, device=0
Control: name="IEC958 Playback Switch", index=0, device=0
Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
Device: name="AD198x Digital", type="SPDIF", device=1
Converter: stream=0, channel=0
Digital: Enabled
Digital category: 0x0
PCM:
rates [0x60]: 44100 48000
bits [0x2]: 16
formats [0x5]: PCM AC3
Delay: 3 samples
Connection: 2
0x01* 0x06
Node 0x03 [Audio Output] wcaps 0x44d: Stereo Amp-Out
Control: name="PCM Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="PCM Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Device: name="AD198x Analog", type="Audio", device=0
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x1c 0x1c]
Converter: stream=8, channel=0
Power states: D0 D3
Power: setting=D0, actual=D0
Processing caps: benign=1, ncoeff=70
Node 0x04 [Audio Output] wcaps 0x40d: Stereo Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Converter: stream=0, channel=0
Power states: D0 D3
Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x40d: Stereo Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Converter: stream=0, channel=0
Power states: D0 D3
Power: setting=D0, actual=D0
Node 0x06 [Audio Input] wcaps 0x100511: Stereo
Device: name="AD198x Analog", type="Audio", device=0
Converter: stream=0, channel=0
SDI-Select: 0
PCM:
rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
bits [0x6]: 16 20
formats [0x1]: PCM
Power states: D0 D3
Power: setting=D0, actual=D0
Connection: 1
0x12
Node 0x07 [Audio Mixer] wcaps 0x200101: Stereo
Connection: 8
0x03 0x09 0x13 0x14 0x15 0x16 0x17 0x18
Node 0x08 [Audio Mixer] wcaps 0x200100: Mono
Connection: 1
0x07
Node 0x09 [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x80] [0x80]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80]
Connection: 2
0x04 0x05
Node 0x0a [Audio Selector] wcaps 0x300101: Stereo
Connection: 3
0x07* 0x04 0x05
Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
Connection: 2
0x07* 0x04
Node 0x0c [Audio Selector] wcaps 0x300101: Stereo
Connection: 2
0x04* 0x07
Node 0x0d [Audio Selector] wcaps 0x300101: Stereo
Connection: 2
0x05* 0x08
Node 0x0e [Audio Selector] wcaps 0x300100: Mono
Connection: 2
0x08* 0x11
Node 0x0f [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Control: name="Mic Boost", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-Out vals: [0x00 0x00]
Connection: 8
0x1f* 0x20 0x1d 0x1d 0x27 0x28 0x29 0x2a
Node 0x10 [Audio Selector] wcaps 0x300101: Stereo
Connection: 3
0x20* 0x1c 0x1f
Node 0x11 [Audio Selector] wcaps 0x300941: Stereo R/L
Connection: 2
0x0f* 0x2b
Processing caps: benign=1, ncoeff=0
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Control: name="Capture Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="Capture Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="Capture Source", index=0, device=0
Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 0
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Control: name="Mic Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="Mic Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 1
0x11
Node 0x14 [Audio Selector] wcaps 0x30010c: Mono Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80]
Connection: 1
0x23
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 1
0x22
Node 0x16 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 1
0x21
Node 0x17 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Control: name="Internal Mic Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="Internal Mic Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 1
0x10
Node 0x18 [Audio Selector] wcaps 0x30010c: Mono Amp-Out
Control: name="Beep Playback Volume", index=0, device=0
ControlAmp: chs=1, dir=Out, idx=0, ofs=0
Control: name="Beep Playback Switch", index=0, device=0
ControlAmp: chs=1, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
Amp-Out vals: [0x8f]
Connection: 2
0x19* 0x24
Node 0x19 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x1a [Pin Complex] wcaps 0x400185: Stereo Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x1f 0x1f]
Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
Conn = 1/8, Color = Green
DefAssociation = 0x1, Sequence = 0xf
Pin-ctls: 0xc0: OUT HP
Unsolicited: tag=00, enabled=0
Connection: 1
0x0a
Node 0x1b [Pin Complex] wcaps 0x400185: Stereo Amp-Out
Control: name="External Amplifier", index=0, device=0
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x1f 0x1f]
Pincap 0x0001001f: OUT HP EAPD Detect Trigger ImpSense
EAPD 0x0:
Pin Default 0x9117f110: [Fixed] Speaker at Int Rear
Conn = Analog, Color = Other
DefAssociation = 0x1, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Connection: 1
0x0b
Node 0x1c [Pin Complex] wcaps 0x400185: Stereo Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00000037: IN OUT Detect Trigger ImpSense
Pin Default 0x410110f0: [N/A] Line Out at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Connection: 1
0x0c
Node 0x1d [Pin Complex] wcaps 0x400985: Stereo Amp-Out R/L
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00001737: IN OUT Detect Trigger ImpSense
Vref caps: HIZ 50 GRD 80
Pin Default 0x91a19121: [Fixed] Mic at Int Rear
Conn = 1/8, Color = Pink
DefAssociation = 0x2, Sequence = 0x1
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT VREF_HIZ
Unsolicited: tag=00, enabled=0
Connection: 1
0x0d
Node 0x1e [Pin Complex] wcaps 0x400104: Mono Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80]
Pincap 0x00000010: OUT
Pin Default 0x411711f0: [N/A] Speaker at Ext Rear
Conn = Analog, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Connection: 1
0x0e
Node 0x1f [Pin Complex] wcaps 0x400081: Stereo
Pincap 0x00001727: IN Detect Trigger ImpSense
Vref caps: HIZ 50 GRD 80
Pin Default 0x02a19020: [Jack] Mic at Ext Front
Conn = 1/8, Color = Pink
DefAssociation = 0x2, Sequence = 0x0
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=00, enabled=0
Node 0x20 [Pin Complex] wcaps 0x400081: Stereo
Pincap 0x00001727: IN Detect Trigger ImpSense
Vref caps: HIZ 50 GRD 80
Pin Default 0x418130f0: [N/A] Line In at Ext Rear
Conn = 1/8, Color = Blue
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x20: IN VREF_HIZ
Unsolicited: tag=00, enabled=0
Node 0x21 [Pin Complex] wcaps 0x400081: Stereo
Pincap 0x00000027: IN Detect Trigger ImpSense
Pin Default 0x5993e1f0: [N/A] Aux at Int ATAPI
Conn = ATAPI, Color = White
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Unsolicited: tag=00, enabled=0
Node 0x22 [Pin Complex] wcaps 0x400001: Stereo
Pincap 0x00000020: IN
Pin Default 0x9933112e: [Fixed] CD at Int ATAPI
Conn = ATAPI, Color = Black
DefAssociation = 0x2, Sequence = 0xe
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Node 0x23 [Pin Complex] wcaps 0x400000: Mono
Pincap 0x00000020: IN
Pin Default 0x59b370f0: [N/A] Telephony at Int ATAPI
Conn = ATAPI, Color = Yellow
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x20: IN
Node 0x24 [Pin Complex] wcaps 0x400000: Mono
Pincap 0x00000020: IN
Pin Default 0x93f711f0: [Fixed] Other at Int Left
Conn = Analog, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Node 0x25 [Pin Complex] wcaps 0x400301: Stereo Digital
Pincap 0x00000010: OUT
Pin Default 0x0145f1f0: [Jack] SPDIF Out at Ext Rear
Conn = Optical, Color = Other
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Connection: 1
0x02
Node 0x26 [Power Widget] wcaps 0x500500: Mono
Power states: D0 D3
Power: setting=D0, actual=D0
Connection: 8
0x07 0x08 0x13 0x14 0x15 0x16 0x17 0x18
Node 0x27 [Audio Mixer] wcaps 0x200101: Stereo
Connection: 2
0x1f 0x1d
Node 0x28 [Audio Mixer] wcaps 0x200101: Stereo
Connection: 2
0x1f 0x20
Node 0x29 [Audio Mixer] wcaps 0x200101: Stereo
Connection: 2
0x1d 0x20
Node 0x2a [Audio Mixer] wcaps 0x200101: Stereo
Connection: 3
0x1f 0x1d 0x20
Node 0x2b [Audio Mixer] wcaps 0x200100: Mono
Connection: 1
0x0f
Codec: Conexant ID 2bfa
Address: 1
Function Id: 0x2
Vendor Id: 0x14f12bfa
Subsystem Id: 0x10431966
Revision Id: 0x90000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 9 Jan 15 21:00 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 8 Jan 15 21:00 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 7 Jan 15 21:00 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116, 6 Jan 15 21:00 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 5 Jan 15 21:43 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 4 Jan 15 21:00 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 3 Jan 15 21:00 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jan 15 21:00 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 60 Jan 15 21:00 .
drwxr-xr-x 3 root root 220 Jan 15 21:00 ..
lrwxrwxrwx 1 root root 12 Jan 15 21:00 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfebfc000 irq 44'
Mixer name	: 'Analog Devices AD1986A'
Components	: 'HDA:11d41986,10431443,00100500 HDA:14f12bfa,10431966,00090000'
Controls : 20
Simple ctrls : 11
Simple mixer control 'Master',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 31 [100%] [0.00dB] [on]
Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 28 [90%] [7.50dB] [on]
Front Right: Playback 28 [90%] [7.50dB] [on]
Simple mixer control 'Mic',0
Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Mono
Limits: Playback 0 - 31
Mono: Capture [on]
Front Left: Playback 0 [0%] [-34.50dB] [off]
Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
Capabilities: volume penum
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 3
Front Left: 0 [0%]
Front Right: 0 [0%]
Simple mixer control 'IEC958',0
Capabilities: pswitch pswitch-joined penum
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
Capabilities: pswitch pswitch-joined penum
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Beep',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
Playback channels: Mono
Limits: Playback 0 - 15
Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 15
Front Left: Capture 0 [0%] [0.00dB] [off]
Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Mix',0
Capabilities: cswitch cswitch-joined cswitch-exclusive penum
Capture exclusive group: 0
Capture channels: Mono
Mono: Capture [off]
Simple mixer control 'External Amplifier',0
Capabilities: pswitch pswitch-joined penum
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Internal Mic',0
Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Mono
Limits: Playback 0 - 31
Mono: Capture [off]
Front Left: Playback 0 [0%] [-34.50dB] [off]
Front Right: Playback 0 [0%] [-34.50dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
control.1 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 31'
comment.dbmin -4650
comment.dbmax 0
iface MIXER
name 'Master Playback Volume'
value.0 31
value.1 31
}
control.2 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'Master Playback Switch'
value.0 true
value.1 true
}
control.3 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 31'
comment.dbmin -3450
comment.dbmax 1200
iface MIXER
name 'PCM Playback Volume'
value.0 28
value.1 28
}
control.4 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'PCM Playback Switch'
value.0 true
value.1 true
}
control.5 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 31'
comment.dbmin -3450
comment.dbmax 1200
iface MIXER
name 'Mic Playback Volume'
value.0 0
value.1 0
}
control.6 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'Mic Playback Switch'
value.0 false
value.1 false
}
control.7 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 3'
comment.dbmin 0
comment.dbmax 3000
iface MIXER
name 'Mic Boost'
value.0 0
value.1 0
}
control.8 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 15'
comment.dbmin 0
comment.dbmax 2250
iface MIXER
name 'Capture Volume'
value.0 0
value.1 0
}
control.9 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'Capture Switch'
value.0 false
value.1 false
}
control.10 {
comment.access 'read write'
comment.type ENUMERATED
comment.count 1
comment.item.0 Mic
comment.item.1 'Internal Mic'
comment.item.2 Mix
iface MIXER
name 'Capture Source'
value Mic
}
control.11 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 1
iface MIXER
name 'External Amplifier'
value true
}
control.12 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 31'
comment.dbmin -3450
comment.dbmax 1200
iface MIXER
name 'Internal Mic Playback Volume'
value.0 0
value.1 0
}
control.13 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'Internal Mic Playback Switch'
value.0 false
value.1 false
}
control.14 {
comment.access read
comment.type IEC958
comment.count 1
iface MIXER
name 'IEC958 Playback Con Mask'
value '0fff000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
}
control.15 {
comment.access read
comment.type IEC958
comment.count 1
iface MIXER
name 'IEC958 Playback Pro Mask'
value '0f00000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
}
control.16 {
comment.access 'read write'
comment.type IEC958
comment.count 1
iface MIXER
name 'IEC958 Playback Default'
value '0400000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
}
control.17 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 1
iface MIXER
name 'IEC958 Playback Switch'
value true
}
control.18 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 1
iface MIXER
name 'IEC958 Default PCM Playback Switch'
value true
}
control.19 {
comment.access 'read write'
comment.type INTEGER
comment.count 1
comment.range '0 - 15'
comment.dbmin -4500
comment.dbmax 0
iface MIXER
name 'Beep Playback Volume'
value 15
}
control.20 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 1
iface MIXER
name 'Beep Playback Switch'
value false
}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
binfmt_misc
rfcomm
sco
bnep
l2cap
dm_crypt
snd_hda_codec_analog
tpm_infineon
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
iwl3945
snd_seq_midi
iwlcore
snd_rawmidi
snd_seq_midi_event
snd_seq
gspca_vc032x
gspca_main
videodev
tpm_tis
tpm
pcmcia
asus_laptop
snd_timer
snd_seq_device
ppdev
yenta_socket
v4l1_compat
joydev
tpm_bios
lp
parport_pc
pcmcia_rsrc
snd
sparse_keymap
pcmcia_core
btusb
parport
soundcore
mac80211
cfg80211
bluetooth
psmouse
serio_raw
snd_page_alloc
usbhid
hid
nouveau
ttm
drm_kms_helper
drm
video
output
firewire_ohci
intel_agp
sdhci_pci
r8169
firewire_core
mii
sdhci
led_class
crc_itu_t
agpgart
i2c_algo_bit


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x1a 0x0121401f
0x1b 0x9117f110
0x1c 0x410110f0
0x1d 0x91a19121
0x1e 0x411711f0
0x1f 0x02a19020
0x20 0x418130f0
0x21 0x5993e1f0
0x22 0x9933112e
0x23 0x59b370f0
0x24 0x93f711f0
0x25 0x0145f1f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a0000

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[ 10.225746] type=1400 audit(1295154010.081:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=827 comm="apparmor_parser"
[ 10.345484] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 10.345542] alloc irq_desc for 44 on node -1
[ 10.345545] alloc kstat_irqs on node -1
[ 10.345560] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 10.345593] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 11.192413] phy0: Selected rate control algorithm 'iwl-3945-rs'
--
[ 8195.668975] [drm] nouveau 0000:01:00.0: Suspending GPU objects...
[ 8195.853130] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 8195.869021] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 226.594 msecs
[ 8195.901858] [drm] nouveau 0000:01:00.0: And we're gone!
--
[ 8196.909555] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 8196.909610] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x
[ 8196.909617] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 8196.909652] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
--
[ 8196.941696] PM: early resume of devices complete after 32.287 msecs
[ 8196.941784] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 8196.941793] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 8196.941844] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 8196.941847] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
--
[ 8215.754340] lo: Disabled Privacy Extensions
[ 8354.104868] hda_codec: invalid CONNECT_LIST verb 12[2]:2100



I am sorry that I do not know how to post that in a separate window, I will try and figure that out. I am pretty sure I did some things with the ALSA driver using snd_hda_intel before, but maybe this means more to you than I. Haha.

Does this help you in debugging?

---

### Post by G. Ross on 2011-01-16
Thanks lidex, this is something new that I have not done. I ran the code and got


--2011-01-16 10:12:57-- [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh](http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh) [following]
--2011-01-16 10:12:59-- [http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh](http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 27247 (27K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,247 44.6K/s in 0.6s 

2011-01-16 10:13:02 (44.6 KB/s) - `alsa-info.sh' saved [27247/27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

dmesg
lspci
lsmod
aplay
amixer
alsactl
/proc/asound/
/sys/class/sound/
~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : Y


Your ALSA information is in /tmp/alsa-info.txt.YZIA8eKEhU




That was interesting. The contents of the file reads as follows:





upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Jan 16 18:13:03 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer: ASUSTeK Computer Inc. 
Product Name: Z62JM 
Product Version: 1.0 


!!Kernel Information
!!------------------

Kernel release: 2.6.35-24-generic
Operating System: GNU/Linux
Architecture: i686
Processor: unknown
SMP Enabled: Yes


!!ALSA Version
!!------------

Driver version: 1.0.23
Library version: 1.0.23
Utilities version: 1.0.23


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

0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xfebfc000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
Subsystem: 1043:1297
--
Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-


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


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y, Y,Y,Y,Y,Y,Y,Y
enable_msi : -1
id : (null),(null),(null),(null),(null),(null),(null),( null),(null),(null),(null),(null),(null),(null),(n ull),(null),(null),(null),(null),(null),(null),(nu ll),(null),(null),(null),(null),(null),(null),(nul l),(null),(null),(null)
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
model : (null),(null),(null),(null),(null),(null),(null),( null),(null),(null),(null),(null),(null),(null),(n ull),(null),(null),(null),(null),(null),(null),(nu ll),(null),(null),(null),(null),(null),(null),(nul l),(null),(null),(null)
patch : (null),(null),(null),(null),(null),(null),(null),( null),(null),(null),(null),(null),(null),(null),(n ull),(null),(null),(null),(null),(null),(null),(nu ll),(null),(null),(null),(null),(null),(null),(nul l),(null),(null),(null)
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1986A
Address: 0
Function Id: 0x1
Vendor Id: 0x11d41986
Subsystem Id: 0x10431443
Revision Id: 0x100500
No Modem Function Group found
Default PCM:
rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
GPIO: io=0, o=1, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
Control: name="IEC958 Playback Con Mask", index=0, device=0
Control: name="IEC958 Playback Pro Mask", index=0, device=0
Control: name="IEC958 Playback Default", index=0, device=0
Control: name="IEC958 Playback Switch", index=0, device=0
Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
Device: name="AD198x Digital", type="SPDIF", device=1
Converter: stream=0, channel=0
Digital: Enabled
Digital category: 0x0
PCM:
rates [0x60]: 44100 48000
bits [0x2]: 16
formats [0x5]: PCM AC3
Delay: 3 samples
Connection: 2
0x01* 0x06
Node 0x03 [Audio Output] wcaps 0x44d: Stereo Amp-Out
Control: name="PCM Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="PCM Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Device: name="AD198x Analog", type="Audio", device=0
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x1c 0x1c]
Converter: stream=8, channel=0
Power states: D0 D3
Power: setting=D0, actual=D0
Processing caps: benign=1, ncoeff=70
Node 0x04 [Audio Output] wcaps 0x40d: Stereo Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Converter: stream=0, channel=0
Power states: D0 D3
Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x40d: Stereo Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Converter: stream=0, channel=0
Power states: D0 D3
Power: setting=D0, actual=D0
Node 0x06 [Audio Input] wcaps 0x100511: Stereo
Device: name="AD198x Analog", type="Audio", device=0
Converter: stream=0, channel=0
SDI-Select: 0
PCM:
rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
bits [0x6]: 16 20
formats [0x1]: PCM
Power states: D0 D3
Power: setting=D0, actual=D0
Connection: 1
0x12
Node 0x07 [Audio Mixer] wcaps 0x200101: Stereo
Connection: 8
0x03 0x09 0x13 0x14 0x15 0x16 0x17 0x18
Node 0x08 [Audio Mixer] wcaps 0x200100: Mono
Connection: 1
0x07
Node 0x09 [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-In vals: [0x80] [0x80]
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x80]
Connection: 2
0x04 0x05
Node 0x0a [Audio Selector] wcaps 0x300101: Stereo
Connection: 3
0x07* 0x04 0x05
Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
Connection: 2
0x07* 0x04
Node 0x0c [Audio Selector] wcaps 0x300101: Stereo
Connection: 2
0x04* 0x07
Node 0x0d [Audio Selector] wcaps 0x300101: Stereo
Connection: 2
0x05* 0x08
Node 0x0e [Audio Selector] wcaps 0x300100: Mono
Connection: 2
0x08* 0x11
Node 0x0f [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Control: name="Mic Boost", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-Out vals: [0x00 0x00]
Connection: 8
0x1f* 0x20 0x1d 0x1d 0x27 0x28 0x29 0x2a
Node 0x10 [Audio Selector] wcaps 0x300101: Stereo
Connection: 3
0x20* 0x1c 0x1f
Node 0x11 [Audio Selector] wcaps 0x300941: Stereo R/L
Connection: 2
0x0f* 0x2b
Processing caps: benign=1, ncoeff=0
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Control: name="Capture Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="Capture Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="Capture Source", index=0, device=0
Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 0
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Control: name="Mic Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="Mic Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 1
0x11
Node 0x14 [Audio Selector] wcaps 0x30010c: Mono Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80]
Connection: 1
0x23
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 1
0x22
Node 0x16 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 1
0x21
Node 0x17 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
Control: name="Internal Mic Playback Volume", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Control: name="Internal Mic Playback Switch", index=0, device=0
ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Connection: 1
0x10
Node 0x18 [Audio Selector] wcaps 0x30010c: Mono Amp-Out
Control: name="Beep Playback Volume", index=0, device=0
ControlAmp: chs=1, dir=Out, idx=0, ofs=0
Control: name="Beep Playback Switch", index=0, device=0
ControlAmp: chs=1, dir=Out, idx=0, ofs=0
Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
Amp-Out vals: [0x8f]
Connection: 2
0x19* 0x24
Node 0x19 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x1a [Pin Complex] wcaps 0x400185: Stereo Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x1f 0x1f]
Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
Conn = 1/8, Color = Green
DefAssociation = 0x1, Sequence = 0xf
Pin-ctls: 0xc0: OUT HP
Unsolicited: tag=00, enabled=0
Connection: 1
0x0a
Node 0x1b [Pin Complex] wcaps 0x400185: Stereo Amp-Out
Control: name="External Amplifier", index=0, device=0
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x1f 0x1f]
Pincap 0x0001001f: OUT HP EAPD Detect Trigger ImpSense
EAPD 0x0:
Pin Default 0x9117f110: [Fixed] Speaker at Int Rear
Conn = Analog, Color = Other
DefAssociation = 0x1, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Connection: 1
0x0b
Node 0x1c [Pin Complex] wcaps 0x400185: Stereo Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00000037: IN OUT Detect Trigger ImpSense
Pin Default 0x410110f0: [N/A] Line Out at Ext Rear
Conn = 1/8, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x40: OUT
Unsolicited: tag=00, enabled=0
Connection: 1
0x0c
Node 0x1d [Pin Complex] wcaps 0x400985: Stereo Amp-Out R/L
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Pincap 0x00001737: IN OUT Detect Trigger ImpSense
Vref caps: HIZ 50 GRD 80
Pin Default 0x91a19121: [Fixed] Mic at Int Rear
Conn = 1/8, Color = Pink
DefAssociation = 0x2, Sequence = 0x1
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT VREF_HIZ
Unsolicited: tag=00, enabled=0
Connection: 1
0x0d
Node 0x1e [Pin Complex] wcaps 0x400104: Mono Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x80]
Pincap 0x00000010: OUT
Pin Default 0x411711f0: [N/A] Speaker at Ext Rear
Conn = Analog, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Connection: 1
0x0e
Node 0x1f [Pin Complex] wcaps 0x400081: Stereo
Pincap 0x00001727: IN Detect Trigger ImpSense
Vref caps: HIZ 50 GRD 80
Pin Default 0x02a19020: [Jack] Mic at Ext Front
Conn = 1/8, Color = Pink
DefAssociation = 0x2, Sequence = 0x0
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=00, enabled=0
Node 0x20 [Pin Complex] wcaps 0x400081: Stereo
Pincap 0x00001727: IN Detect Trigger ImpSense
Vref caps: HIZ 50 GRD 80
Pin Default 0x418130f0: [N/A] Line In at Ext Rear
Conn = 1/8, Color = Blue
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x20: IN VREF_HIZ
Unsolicited: tag=00, enabled=0
Node 0x21 [Pin Complex] wcaps 0x400081: Stereo
Pincap 0x00000027: IN Detect Trigger ImpSense
Pin Default 0x5993e1f0: [N/A] Aux at Int ATAPI
Conn = ATAPI, Color = White
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Unsolicited: tag=00, enabled=0
Node 0x22 [Pin Complex] wcaps 0x400001: Stereo
Pincap 0x00000020: IN
Pin Default 0x9933112e: [Fixed] CD at Int ATAPI
Conn = ATAPI, Color = Black
DefAssociation = 0x2, Sequence = 0xe
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Node 0x23 [Pin Complex] wcaps 0x400000: Mono
Pincap 0x00000020: IN
Pin Default 0x59b370f0: [N/A] Telephony at Int ATAPI
Conn = ATAPI, Color = Yellow
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x20: IN
Node 0x24 [Pin Complex] wcaps 0x400000: Mono
Pincap 0x00000020: IN
Pin Default 0x93f711f0: [Fixed] Other at Int Left
Conn = Analog, Color = Black
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x20: IN
Node 0x25 [Pin Complex] wcaps 0x400301: Stereo Digital
Pincap 0x00000010: OUT
Pin Default 0x0145f1f0: [Jack] SPDIF Out at Ext Rear
Conn = Optical, Color = Other
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Connection: 1
0x02
Node 0x26 [Power Widget] wcaps 0x500500: Mono
Power states: D0 D3
Power: setting=D0, actual=D0
Connection: 8
0x07 0x08 0x13 0x14 0x15 0x16 0x17 0x18
Node 0x27 [Audio Mixer] wcaps 0x200101: Stereo
Connection: 2
0x1f 0x1d
Node 0x28 [Audio Mixer] wcaps 0x200101: Stereo
Connection: 2
0x1f 0x20
Node 0x29 [Audio Mixer] wcaps 0x200101: Stereo
Connection: 2
0x1d 0x20
Node 0x2a [Audio Mixer] wcaps 0x200101: Stereo
Connection: 3
0x1f 0x1d 0x20
Node 0x2b [Audio Mixer] wcaps 0x200100: Mono
Connection: 1
0x0f
Codec: Conexant ID 2bfa
Address: 1
Function Id: 0x2
Vendor Id: 0x14f12bfa
Subsystem Id: 0x10431966
Revision Id: 0x90000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 9 Jan 15 21:00 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 8 Jan 15 21:00 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 7 Jan 15 21:00 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116, 6 Jan 15 21:00 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 5 Jan 15 21:43 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 4 Jan 15 21:00 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 3 Jan 15 21:00 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jan 15 21:00 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 60 Jan 15 21:00 .
drwxr-xr-x 3 root root 220 Jan 15 21:00 ..
lrwxrwxrwx 1 root root 12 Jan 15 21:00 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfebfc000 irq 44'
Mixer name	: 'Analog Devices AD1986A'
Components	: 'HDA:11d41986,10431443,00100500 HDA:14f12bfa,10431966,00090000'
Controls : 20
Simple ctrls : 11
Simple mixer control 'Master',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 31 [100%] [0.00dB] [on]
Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 28 [90%] [7.50dB] [on]
Front Right: Playback 28 [90%] [7.50dB] [on]
Simple mixer control 'Mic',0
Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Mono
Limits: Playback 0 - 31
Mono: Capture [on]
Front Left: Playback 0 [0%] [-34.50dB] [off]
Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
Capabilities: volume penum
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 3
Front Left: 0 [0%]
Front Right: 0 [0%]
Simple mixer control 'IEC958',0
Capabilities: pswitch pswitch-joined penum
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
Capabilities: pswitch pswitch-joined penum
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Beep',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
Playback channels: Mono
Limits: Playback 0 - 15
Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 15
Front Left: Capture 0 [0%] [0.00dB] [off]
Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Mix',0
Capabilities: cswitch cswitch-joined cswitch-exclusive penum
Capture exclusive group: 0
Capture channels: Mono
Mono: Capture [off]
Simple mixer control 'External Amplifier',0
Capabilities: pswitch pswitch-joined penum
Playback channels: Mono
Mono: Playback [on]
Simple mixer control 'Internal Mic',0
Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
Capture exclusive group: 0
Playback channels: Front Left - Front Right
Capture channels: Mono
Limits: Playback 0 - 31
Mono: Capture [off]
Front Left: Playback 0 [0%] [-34.50dB] [off]
Front Right: Playback 0 [0%] [-34.50dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
control.1 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 31'
comment.dbmin -4650
comment.dbmax 0
iface MIXER
name 'Master Playback Volume'
value.0 31
value.1 31
}
control.2 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'Master Playback Switch'
value.0 true
value.1 true
}
control.3 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 31'
comment.dbmin -3450
comment.dbmax 1200
iface MIXER
name 'PCM Playback Volume'
value.0 28
value.1 28
}
control.4 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'PCM Playback Switch'
value.0 true
value.1 true
}
control.5 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 31'
comment.dbmin -3450
comment.dbmax 1200
iface MIXER
name 'Mic Playback Volume'
value.0 0
value.1 0
}
control.6 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'Mic Playback Switch'
value.0 false
value.1 false
}
control.7 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 3'
comment.dbmin 0
comment.dbmax 3000
iface MIXER
name 'Mic Boost'
value.0 0
value.1 0
}
control.8 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 15'
comment.dbmin 0
comment.dbmax 2250
iface MIXER
name 'Capture Volume'
value.0 0
value.1 0
}
control.9 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'Capture Switch'
value.0 false
value.1 false
}
control.10 {
comment.access 'read write'
comment.type ENUMERATED
comment.count 1
comment.item.0 Mic
comment.item.1 'Internal Mic'
comment.item.2 Mix
iface MIXER
name 'Capture Source'
value Mic
}
control.11 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 1
iface MIXER
name 'External Amplifier'
value true
}
control.12 {
comment.access 'read write'
comment.type INTEGER
comment.count 2
comment.range '0 - 31'
comment.dbmin -3450
comment.dbmax 1200
iface MIXER
name 'Internal Mic Playback Volume'
value.0 0
value.1 0
}
control.13 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 2
iface MIXER
name 'Internal Mic Playback Switch'
value.0 false
value.1 false
}
control.14 {
comment.access read
comment.type IEC958
comment.count 1
iface MIXER
name 'IEC958 Playback Con Mask'
value '0fff000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
}
control.15 {
comment.access read
comment.type IEC958
comment.count 1
iface MIXER
name 'IEC958 Playback Pro Mask'
value '0f00000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
}
control.16 {
comment.access 'read write'
comment.type IEC958
comment.count 1
iface MIXER
name 'IEC958 Playback Default'
value '0400000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 00000000000000000000000000000000000000000000000000 000'
}
control.17 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 1
iface MIXER
name 'IEC958 Playback Switch'
value true
}
control.18 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 1
iface MIXER
name 'IEC958 Default PCM Playback Switch'
value true
}
control.19 {
comment.access 'read write'
comment.type INTEGER
comment.count 1
comment.range '0 - 15'
comment.dbmin -4500
comment.dbmax 0
iface MIXER
name 'Beep Playback Volume'
value 15
}
control.20 {
comment.access 'read write'
comment.type BOOLEAN
comment.count 1
iface MIXER
name 'Beep Playback Switch'
value false
}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
binfmt_misc
rfcomm
sco
bnep
l2cap
dm_crypt
snd_hda_codec_analog
tpm_infineon
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
iwl3945
snd_seq_midi
iwlcore
snd_rawmidi
snd_seq_midi_event
snd_seq
gspca_vc032x
gspca_main
videodev
tpm_tis
tpm
pcmcia
asus_laptop
snd_timer
snd_seq_device
ppdev
yenta_socket
v4l1_compat
joydev
tpm_bios
lp
parport_pc
pcmcia_rsrc
snd
sparse_keymap
pcmcia_core
btusb
parport
soundcore
mac80211
cfg80211
bluetooth
psmouse
serio_raw
snd_page_alloc
usbhid
hid
nouveau
ttm
drm_kms_helper
drm
video
output
firewire_ohci
intel_agp
sdhci_pci
r8169
firewire_core
mii
sdhci
led_class
crc_itu_t
agpgart
i2c_algo_bit


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x1a 0x0121401f
0x1b 0x9117f110
0x1c 0x410110f0
0x1d 0x91a19121
0x1e 0x411711f0
0x1f 0x02a19020
0x20 0x418130f0
0x21 0x5993e1f0
0x22 0x9933112e
0x23 0x59b370f0
0x24 0x93f711f0
0x25 0x0145f1f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a0000

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[ 10.225746] type=1400 audit(1295154010.081:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=827 comm="apparmor_parser"
[ 10.345484] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 10.345542] alloc irq_desc for 44 on node -1
[ 10.345545] alloc kstat_irqs on node -1
[ 10.345560] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 10.345593] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 11.192413] phy0: Selected rate control algorithm 'iwl-3945-rs'
--
[ 8195.668975] [drm] nouveau 0000:01:00.0: Suspending GPU objects...
[ 8195.853130] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 8195.869021] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 226.594 msecs
[ 8195.901858] [drm] nouveau 0000:01:00.0: And we're gone!
--
[ 8196.909555] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 8196.909610] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x
[ 8196.909617] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 8196.909652] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
--
[ 8196.941696] PM: early resume of devices complete after 32.287 msecs
[ 8196.941784] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 8196.941793] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 8196.941844] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 8196.941847] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
--
[ 8215.754340] lo: Disabled Privacy Extensions
[ 8354.104868] hda_codec: invalid CONNECT_LIST verb 12[2]:2100



I am sorry that I do not know how to post that in a separate window, I will try and figure that out. I am pretty sure I did some things with the ALSA driver using snd_hda_intel before, but maybe this means more to you than I. Haha.

Does this help you in debugging?

---

### Post by G. Ross on 2011-01-16
Oops.  I didn't mean to post that three times.  I feel like a major rookie right now.

I didn't understand your last comment on the output thingy - the stuff you wrote in brackets.  It does seem that it is recognizing the sound card though.  Thanks again.

---

### Post by lidex on 2011-01-18
OK. Now is time to try editing alsa-base.conf.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

The models you can choose from are:
```
AD1986A
=======
  6stack	6-jack, separate surrounds (default)
  3stack	3-stack, shared surrounds
  laptop	2-channel only (FSC V2060, Samsung M50)
  laptop-eapd	2-channel with EAPD (ASUS A6J)
  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
  ultra		2-channel with EAPD (Samsung Ultra tablet PC)
  samsung	2-channel with EAPD (Samsung R65)
  samsung-p50	2-channel with HP-automute (Samsung P50)
```

---

### Post by G. Ross on 2011-01-18
Ok.  No sound on reboot.  I enter Alsamixer and when I press F6 it has only the options of Default and HDA-Intel.  System > Preferences > Sound, under hardware has Internal Audio, 1 Output/1 Input, Analog Stereo Duplex.

When I highlight and hit enter on 'beep', I should hear a beep right?

Is this my actual card?  Or a default?

N10/ICH 7 Family High Definition Audio Controller is what the "true" name is, right?  It is by Intel.  

I did not understand where I would input these options:

AD1986A
=======
  6stack	6-jack, separate surrounds (default)
  3stack	3-stack, shared surrounds
  laptop	2-channel only (FSC V2060, Samsung M50)
  laptop-eapd	2-channel with EAPD (ASUS A6J)
  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
  ultra		2-channel with EAPD (Samsung Ultra tablet PC)
  samsung	2-channel with EAPD (Samsung R65)
  samsung-p50	2-channel with HP-automute (Samsung P50)

Under 'output' in System > Preferences > Sound, I have only 'Internal Analog Stereo, Stereo' as an option.

I also saw on some other threads that PulseAudio has caused others some problems.  I tried several ways of making Esound the defaul, but to no avail.  I know that this computer is different than most off-the-shelf models, so I figure this may be my problem as well.  Dunno though.  I am loving EVERYTHING in ubuntu so far - except the lack of sound.  I don't want to try other types of linux, or go so far back as to use Esound distro of ubuntu (like three years old).  

Thanks again for the assistance, each time you reply it is something I have not done yet, and that is a good sign.

Peace.

---

### Post by G. Ross on 2011-01-18
I was also looking over this thread: [http://ubuntuforums.org/archive/index.php/t-1467387.html](http://ubuntuforums.org/archive/index.php/t-1467387.html)

It seems you were involved in this discussion as well.  That is my same soundcard I think.  Should I follow your instructions?

*****
OK. Update your kernel:
sudo apt-get update
sudo apt-get upgrade
Now reboot so we can work with the latest kernel.
Install alsa backports:
sudo apt-get install linux-backports-modules-alsa-lucid-generic Reboot again.

Now this. Can you post the output of these terminal commands for me please:
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#**
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.
**********

Also, every time I re-install ubuntu I am using 10.10 distro.  Is there a string of commands I should run upon re-installing?  I am now running a freshly re-installed 10.10, no upgrades, no third-party software.  I just think I might not have done all the things I should do.

Right on.

---

