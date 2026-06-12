---
title: "New machine - no sound"
date: 2010-05-25
forum: Multimedia Software
---

### Post by rhinert on 2010-05-25
Been doing a bit of reading about multimedia and poking around.  This is for a new machine built from parts.  Motherboard is an Asus M4A87TD with integrated sound.  

Here are the results of some tests.  The sheer volume of sound related kernels blows me away (lsmod).  

Can you folks see anything obviously wrong?

----------------------------------------------------------------------------------------

command: aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---------------

command: lspci -v


00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
        Subsystem: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fcbf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel



05:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device 8326
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fe97c000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


---------------




Alsamixer and kmix do not appear to have a mute function.  I was given to understand that the console-based alsamixer would toggle mute with the "m" key but I get no color changes in the vertical bars or other visual indications that mute works.



---------------


command: lsmod


Module                  Size  Used by

snd_hda_codec_via      27111  0 
snd_hda_intel          21877  5 
snd_pcm_oss            35308  0 
snd_hda_codec          74201  2 snd_hda_codec_via,snd_hda_intel
snd_mixer_oss          13746  1 snd_pcm_oss
snd_hwdep               5412  1 snd_hda_codec
snd_pcm                70662  4 snd_hda_intel,snd_pcm_oss,snd_hda_codec
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   5259  0 
snd_timer              19098  3 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110            9017  0 
nvidia               9932176  38 
snd                    54148  19 snd_hda_intel,snd_pcm_oss,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
joydev                  8708  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
serio_raw               3978  0 
xhci                   35666  0 
ati_agp                 5094  0 
agpgart                31724  2 nvidia,ati_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950 0                                                                                              
usbhid                 36110  0 
hid                    67032  1 usbhid
ieee1394               81181  1 ohci1394
pata_jmicron            1843  0 
r8169                  33884  0 
mii                     4381  1 r8169
pata_atiixp             3148  0 
ahci                   32008  2

---

### Post by frozonecom on 2010-05-25
check in System>>Preferences>>Sound if anything is muted.

and in the Hardware Tab, make sure your sound device is selected.

Check those first.

---

### Post by rhinert on 2010-05-26
> **frozonecom said:**
> check in System>>Preferences>>Sound if anything is muted.

and in the Hardware Tab, make sure your sound device is selected.

Check those first.


That's the odd thing -- there appears to be no mute checkbox, widget or function in any module that has to do with sound.  I can't help but wonder if the mute is currently 'on' but there is simply no access to it?


The system settings -> hardware has no entry for sound.  Current entries under 'hardware" include:

1) power manager
2) network manager
3) bluetooth manager
4) remote control manager

Should there be an entry for sound in Kubuntu system settings?


Observation:  Command lspci lists the kernel module as "snd-hda-intel" which has a hyphen.  Command lsmod lists the module as "snd_hda_intel" with an underscore.  Significant?

---

### Post by frozonecom on 2010-05-26
lspci shows that you have 2 sound device, maybe one is interfering with the other, maybe disabling the other one will get your sound to work, maybe in the bios utility you can do that. 

> Restart your pc and press the key to open BIOS settings, then disable the onboard sound device.

if that doesnt work, undo the changes manually in the BIOS Settings to prevent damage.

---

### Post by rhinert on 2010-05-26
> **frozonecom said:**
> lspci shows that you have 2 sound device, maybe one is interfering with the other, maybe disabling the other one will get your sound to work, maybe in the bios utility you can do that. 

if that doesnt work, undo the changes manually in the BIOS Settings to prevent damage.



There is only one sound card in the system and that is built-in to the motherboard.  The  ATI Azalia is the "soundcard" and the nVidia Controller is used for (?).  When I select the Nvidia device under the console-based alsamixer, it complains that the Nvidia has no controls available.  When I select the ATI card in alsamixer, it displays a master-volume, a PCM volume and a control for capture.  There are no "mute" functions available.  Pressing the letter "m" produces no visible results.

I can't separate the Nvidia controller and the ATI Azalia soundcard in the bios.  I can only turn on or off the on-board sound.  I have tried disabling it and re-enabling it in the bios.  No joy.

This motherboard is only a few months old and others are having sound problems with Linux too. The primary purpose of this box is multimedia so I've ordered several used sound cards off Ebay to get this system up and functioning if all else fails......

I really appreciate the ideas and troubleshooting help....

---

### Post by kyrandesa on 2010-10-30
I have the same motherboard and the same problem on Ubuntu 10.04. sound is not muted and it works (even though on low volume) from the front-panel audio output.

I've also selected the correct audio output device. 

I just tried on a fresh install of Kubuntu 10.10 and there it works without problems.

---

