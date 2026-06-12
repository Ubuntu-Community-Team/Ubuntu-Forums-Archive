---
title: "sound only from earphone?"
date: 2009-11-07
forum: Multimedia Software
---

### Post by zyx on 2009-11-07
Headphones work on hda-intel. speakers don't!

Since I update into 9.10, only earphone works (both front and rear)! 

aplay shows
a1@e1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
a1@e1:~$

If I take the earphone off, it does not have sound any more. 
is there a way to make it work?
Thanks in advance!

---

### Post by Ulysses361 on 2009-11-07
Please send us the output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by zyx on 2009-11-07
Here are the information you need!

a1@e1:~$ wget -O alsa-info.sh [http://212.20.107.51/alsa-info.sh](http://212.20.107.51/alsa-info.sh) 
--2009-11-08 12:05:58--  [http://212.20.107.51/alsa-info.sh](http://212.20.107.51/alsa-info.sh)                   
Proxy request sent, awaiting response... 302 Moved Temporarily               
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]                                                                                  
--2009-11-08 12:05:59--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)                                                                               
Proxy request sent, awaiting response... 200 OK                                             
Length: unspecified [text/plain]                                                            
Saving to: `alsa-info.sh'                                                                   

    [   <=>                                             ] 26,584      33.2K/s   in 0.8s    

2009-11-08 12:06:02 (33.2 KB/s) - `alsa-info.sh' saved [26584]

a1@e1:~$ bash alsa-info.sh --pastebin 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.                                                                                
ALSA Information Script v 0.4.58                                                            
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

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.                                                                                
Automatically upload ALSA information to pastebin? [y/N] : y                                
Uploading information to [www.pastebin.ca](www.pastebin.ca) ...  Done!                                         

Your ALSA information is located at [http://pastebin.ca/1661625](http://pastebin.ca/1661625)
                                                                                            
Please inform the person helping you.                                                       

a1@e1:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0320000 irq 16
a1@e1:~$
a1@e1:~$ sudo aptitude install paman gnome-alsamixer alsa-utils flashplugin-nonfree-extrasound
Reading package lists... Done                                                                              
Building dependency tree                                                                                   
Reading state information... Done                                                                          
Reading extended state information                                                                         
Initializing package states... Done                                                                        
Writing extended state information... Done                                                                 
The following NEW packages will be installed:                                                              
  flashplugin-nonfree-extrasound                                                                           
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,160B of archives. After unpacking 65.5kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  flashplugin-nonfree-extrasound

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
Get:1 [http://mirror.internode.on.net](http://mirror.internode.on.net) karmic/multiverse flashplugin-nonfree-extrasound 0.0.svn2431-3 [8,160B]
Fetched 8,160B in 0s (93.2kB/s)
Selecting previously deselected package flashplugin-nonfree-extrasound.
(Reading database ... 363142 files and directories currently installed.)
Unpacking flashplugin-nonfree-extrasound (from .../flashplugin-nonfree-extrasound_0.0.svn2431-3_i386.deb) ...
Setting up flashplugin-nonfree-extrasound (0.0.svn2431-3) ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

a1@e1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

a1@e1:~$ sudo lshw -C sound
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:d0320000-d0323fff

a1@e1:~$ ls -lart /dev/snd
total 0
crw-rw----+  1 root audio 116, 2 2009-11-07 17:52 timer
crw-rw----+  1 root audio 116, 3 2009-11-07 17:52 seq
crw-rw----+  1 root audio 116, 7 2009-11-07 17:52 hwC0D2
crw-rw----+  1 root audio 116, 8 2009-11-07 17:52 controlC0
drwxr-xr-x   2 root root      60 2009-11-07 17:52 by-path
drwxr-xr-x   3 root root     200 2009-11-07 17:52 .
crw-rw----+  1 root audio 116, 4 2009-11-08 12:03 pcmC0D1p
crw-rw----+  1 root audio 116, 6 2009-11-08 12:03 pcmC0D0c
crw-rw----+  1 root audio 116, 5 2009-11-08 12:09 pcmC0D0p
drwxr-xr-x  16 root root    3920 2009-11-08 12:24 ..
a1@e1:~$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.20 emulation code)
Kernel: Linux e1 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xd0320000 irq 16

Audio devices:
0: AD198x Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Analog Devices AD1882

a1@e1:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82Q35 Express DRAM Controller [8086:29b0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82Q35 Express PCI Express Root Port [8086:29b1] (rev 02)
00:03.0 Communication controller [0780]: Intel Corporation 82Q35 Express MEI Controller [8086:29b4] (rev 02)
00:03.2 IDE interface [0101]: Intel Corporation 82Q35 Express PT IDER Controller [8086:29b6] (rev 02)
00:03.3 Serial controller [0700]: Intel Corporation 82Q35 Express Serial KT Controller [8086:29b7] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller [8086:2914] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller [8086:2920] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller [8086:2926] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV610 [Radeon HD 2400 XT] [1002:94c1]

a1@e1:~$ sudo which alsactl
/sbin/alsactl

a1@e1:~$ sudo fuser -v /dev/dsp /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  a1   8896 F.... kmix
                     a1  11072 F.... pulseaudio

a1@e1:~$ dpkg -S bin/slmodemd
dpkg: *bin/slmodemd* not found.

a1@e1:~$ dpkg -S bin/slmodemd
dpkg: *bin/slmodemd* not found.

a1@e1:~$ lsmod | grep snd
snd_hda_intel          26920  3
snd_hda_codec_analog    59292  1
snd_hda_codec          75708  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  18 snd_hda_intel,snd_hda_codec_analog,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

Hope you find the problems! Thank you again!

---

### Post by Ulysses361 on 2009-11-08
Hi,

Please try this procedure:

Step 1: Open Terminal from "Applications->Accessories->
Terminal"

Step 2: Run the following commands (copy/paste each command into the Terminal and then hit <enter>)

sudo aptitude update
sudo aptitude install gnome-alsamixer

Step 3: copy-paste the following command into the Terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf

and add these lines to the end of the file:

# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=3stack

If that model option does not help, try one of these alternatives:

 AD1988/AD1988B/AD1989A/AD1989B
   6stack 6-jack
   6stack-dig ditto with SPDIF
   3stack 3-jack
   3stack-dig ditto with SPDIF
   laptop 3-jack with hp-jack automute
   laptop-dig ditto with SPDIF
   auto auto-config reading BIOS (default)

Step 4: Then navigate to System>Preferences>Sound and change everything to ALSA

Step 5; reboot and retest sound

Step 6: Experiment with the audio settings in gnome-alsamixer  until you get sound (hopefully). 

Step 7: If you are trying to use analog speaker output instead of digital output, please try muting the following digital channels:

Simple mixer control 'IEC958',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 9 [23%] [-45.00dB] [on]
  Front Right: Playback 9 [23%] [-45.00dB] [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

Regards,

Mark

---

### Post by zyx on 2009-11-08
Thank you, Mark!

I did all you told, unfortunately, it does not work. My computer is Lenovo (desktop, M57 Tower E6750).

I think I am tired to find out the problem, just leave it!

---

### Post by zyx on 2009-11-11
> **zyx said:**
> Headphones work on hda-intel. speakers don't!

Since I update into 9.10, only earphone works (both front and rear)! 

aplay shows
a1@e1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
a1@e1:~$

If I take the earphone off, it does not have sound any more. 
is there a way to make it work?
Thanks in advance!

The problem is solved when I updated KDE into 4.3.3 and added
options snd-hda-intel model=lenovo
options snd-hda-intel model=3stack
into /etc/modprobe.d/alsa-base

Hope it would be useful to the same problems others had!:P

---

