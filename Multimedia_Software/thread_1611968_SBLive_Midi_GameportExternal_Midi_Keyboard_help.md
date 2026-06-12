---
title: "SBLive Midi Gameport/External Midi Keyboard help"
date: 2010-11-02
forum: Multimedia Software
---

### Post by cvowen on 2010-11-02
Need help getting my external midi keyboard to be recognized by SBLIve EMU10k1 game port. 
Trying to play around with Bristol which works fine with computer keyboard but wanted the external midi keyboard to do the work!
Havn't tried since release 8.**, which worked then, but I thought I'd fire it up with 10.10.

See if the below info helps.
Looks clean to me.
Have the midi cables correct in/out/ etc.

!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      GA-MA785GM-US2H


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_emu10k1


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Live           ]: EMU10K1 - SB Live! Platinum [CT4760P]
                      SB Live! Platinum [CT4760P] (rev.5, serial:0x80401102) at 0xcf00, irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

03:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

03:07.0 0401: 1102:0002 (rev 05)
	Subsystem: 1102:8040


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

AND:
!!All Loaded Modules
!!------------------

Module
binfmt_misc
snd_emu10k1_synth
snd_emux_synth
snd_seq_virmidi
snd_seq_midi_emul
snd_emu10k1
snd_ac97_codec
ac97_bus
snd_pcm
snd_page_alloc
snd_util_mem
snd_hwdep
nvidia
snd_seq_midi
ppdev
snd_rawmidi
lp
parport_pc
snd_seq_midi_event
snd_seq
parport
snd_timer
usblp
snd_seq_device
k10temp
edac_core
edac_mce_amd
usbhid
hid
emu10k1_gp
i2c_piix4
gameport
snd
soundcore
firewire_ohci
floppy
ahci
firewire_core
r8169
crc_itu_t
mii
pata_atiixp
libahci

---

### Post by cvowen on 2010-11-03
O.K., Got it going! 
External Casio Midi keyboard connected to gameport of a SBLive with EMU10K1 chip.

Research this: Go to community/help page Midi/HardwareSynthesisSetup.

Download and install sound font .sf2 file, which I had forgotten to initially do, but since the SBLive etc. sound cards have hardware synths grab one.

At terminal....this was a great help and after changing things around do this.....wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh



Opened up terminal and I did this:
******@*******-desktop:~$ sudo gedit /etc/modprobe.d/asla-base
Copy/pasted/saved this into asla-base:
options snd-emu10k1 max_buffer_size=512 max_synth_voices=256
options modprobe snd_seq_midi
options modprobe snd_emux_synth
options modprobe snd_emu10k1_synth

Note:
options snd-emu10k1 max_buffer_size=512 max_synth_voices=256
The reason for this is that my .sf2 file was huge (FluidR3_GM.sf2 -140MB.) and when trying to load it you'll get a "denied because of a lack of memory etc." You'll find posts for a buffer_size of 256 but I'm using 512 cause I've 2G memory?

This part:
options modprobe snd_seq_midi
options modprobe snd_emux_synth
options modprobe snd_emu10k1_synth
Got that somewhere on the web. I'm to tired to follow thru but it worked for me.

I think basically that your kernal has the modules but it up to you to "load" them? Tell Ubuntu what you want and it'll put it out there!

BRISTOL SYNTH:
I run it from Terminal don't like the Synaptic Package.
1. Fire up QTJack, go to setup and change Midi Driver to: Seq
2. Open Terminal and do this:
*****@******-desktop:~$ startBristol -b3 -jack    Click Enter **-b3 or whatever you want. Read the manual.  

3. Open QTJack and do this on the Connections Tabs:
Audio Tab: Bristol Out/System In
Midi Tab: System OUt/Bristol In
Alsa Tab: 16:SB Live! Platinum Out/ 14: Midi Through....May be different on you system? Worked for me.

---

