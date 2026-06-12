---
title: "No sound &amp; audio device doesn't get recognized in Karmic"
date: 2010-03-07
forum: Multimedia Software
---

### Post by iClouseau88 on 2010-03-07
Hi,
I just installed Ubuntu 9.04 on my laptop then immediately upgraded to Karmic 9.10. Pulseaudio installed by default.  There's no sound although the mute button is not checked and the volume slide control is at medium.

lspci gives:

00:14.2 Audio device: ATI Technologies IXP SB4x6 Hi Definition audio controller (rev01)

System >Preferences >Sound >Hardware tab: blank window "choose a device to configure"

Output tab: "dummy" output stereo

So, it appears that somehow the audio device controller in my laptop is not recognized or its driver disabled, possibly by pulseaudio.  Sound works fine in Windows 7 part of this dual-booted laptop.

I would very much appreciate your help.

---

### Post by iClouseau88 on 2010-03-08
Hi,

here's additional info:

~$ cat /etc/X11/xorg.conf gives:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

~$ sudo lshw -C sound gives:

*-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:c0500000-c0503fff

Any suggestions?

---

### Post by iClouseau88 on 2010-03-09
Hi again,

$aplay -l gives:
***list of PLAYBACK Hardware Devices***
(There's no listing of audio playback devices at all below thisline!)

$alsamixer gives: "no mixer elems found"

$ cat /proc/asound/version gives:
ALSA driver version 1.0.20

$uname -r gives:

(kernel) 2.6.31-20-generic

I have been trying every solution and suggestions found in ubuntuforums and via Google but still get no sound, blank Hardware tab and "dummy output".  I am getting desperate!  Please help me!

Thanks in adance!

---

### Post by iClouseau88 on 2010-03-09
some more info:
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Mar  9 22:23:08 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite A110


!!Kernel Information
!!------------------

Kernel release:    2.6.31-20-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0500000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:437b (rev 01)
	Subsystem: 1179:ff00


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=0 power_save_controller=N
snd-hda-intel: model=auto


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : auto,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : N
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: LSI ID 1040
Address: 0
Function Id: 0x2
Vendor Id: 0x11c11040
Subsystem Id: 0x11790001
Revision Id: 0x100200
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 5 Mar  9 17:05 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 4 Mar  9 17:05 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 3 Mar  9 17:05 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Mar  9 17:05 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Mar  9 17:05 .
drwxr-xr-x 3 root root 140 Mar  9 17:05 ..
lrwxrwxrwx 1 root root  12 Mar  9 17:05 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xc0500000 irq 16'
  Mixer name	: 'LSI ID 1040'
  Components	: 'HDA:11c11040,11790001,00100200'
  Controls      : 0
  Simple ctrls  : 0


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
	control {
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
lib80211_crypt_tkip
wl
lib80211
joydev
pcmcia
arc4
ecb
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
iptable_filter
snd_seq_oss
ip_tables
x_tables
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
psmouse
serio_raw
yenta_socket
rsrc_nonstatic
pcmcia_core
ath5k
mac80211
led_class
ath
cfg80211
shpchp
i2c_piix4
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
lp
parport
ohci1394
ieee1394
8139too
8139cp
mii
video
output
radeon
ttm
drm
i2c_algo_bit
ati_agp
agpgart


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

---

### Post by chaanakya_chiraag on 2010-03-09
Try this:
```
sudo killall pulseaudio
sudo pulseaudio --system --daemonize
```

---

### Post by iClouseau88 on 2010-03-09
Hi,
Thank you for your reply.  Here's what the terminal shows after I ran the second command:

$sudo pulseaudio --system --daemonize

W: main.c: Running in systemmode, but --disallow-exit not set!
W: main.c: Running in systemmode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disallowing SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!
E: main.c: [B]Daemon startup failed!
[/B]
What do these mean and what should I do next?

---

### Post by chaanakya_chiraag on 2010-03-09
Just realized: it's ```
sudo pulseaudio --system --daemon
```  Does that work?

---

### Post by iClouseau88 on 2010-03-09
No, not at all.  Still the same error messages!

---

### Post by chaanakya_chiraag on 2010-03-10
Did you run the first command?  Or did you jump directly to the second?

---

### Post by chaanakya_chiraag on 2010-03-10
The first command kills the pulseaudio server so that you can start it manually using the second command.

---

### Post by iClouseau88 on 2010-03-10
I did run the first command,then the second one.

---

### Post by iClouseau88 on 2010-03-10
Hello folks,

Good news! Finally I was able to solve the problem after 2 days of digging.  Here's what I did:

1. Open a terminal and enter:

sudo gedit /etc/modprobe.d/alsa-base.conf

2.  In the alsa-base.conf file that opens, add the following line to specify the audio driver:

options snd-hda-intel probe-mask=8 model=3stack

3.  Save the file and reboot

4.  System >Admin >User Settings >Advanced >User Privileges

5.  **Uncheck** the box called "Use audio devices" (tip from Bug#433654 in launchpad.net;this is to unlock access to audio device(s))

6. Open the terminal and type the following lines:

$killall pulseaudio
$sudo alsa force-reload
$aplay -l

Immediately following $aplay -l, I saw a list of audio device(s) available under the list of Playback Hardware.  

To doublecheck: System >Preferences >Sound: Hardware tab now list the audio device whereas before I only saw "Dummy Output".

I hope this information is helpful.

---

### Post by Atilana on 2010-03-10
Hi, try this code 
sudo killall pulseaudiosudo pulseaudio --system --daemonizei'm pretty sure that this work..

---

### Post by johnh10000 on 2010-03-21
> **iClouseau88 said:**
> Hello folks,

Good news! Finally I was able to solve the problem after 2 days of digging.  Here's what I did:

1. Open a terminal and enter:

sudo gedit /etc/modprobe.d/alsa-base.conf

2.  In the alsa-base.conf file that opens, add the following line to specify the audio driver:

options snd-hda-intel probe-mask=8 model=3stack

3.  Save the file and reboot

4.  System >Admin >User Settings >Advanced >User Privileges

5.  **Uncheck** the box called "Use audio devices" (tip from Bug#433654 in launchpad.net;this is to unlock access to audio device(s))

6. Open the terminal and type the following lines:

$killall pulseaudio
$sudo alsa force-reload
$aplay -l

Immediately following $aplay -l, I saw a list of audio device(s) available under the list of Playback Hardware.  

To doublecheck: System >Preferences >Sound: Hardware tab now list the audio device whereas before I only saw "Dummy Output".

I hope this information is helpful.

cheers friend worked for me!!!!

---

### Post by nikger on 2010-03-24
Thanks for this helpful post, worked perfect for me..

---

### Post by beezwings on 2010-05-11
Hi~

I tried using this to get my usb headphones (that previously worked in Jaunty but not in Karmic) to work. It did, however, in the process, it also killed my internal microphone. How can I still use my internal mic/mic jack while using usb headphones? Any ideas?

Thanks!

---

