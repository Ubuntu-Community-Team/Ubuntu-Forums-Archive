---
title: "sound suddenly dead on amd64 ubuntustudiostalled"
date: 2009-02-13
forum: Multimedia Software
---

### Post by Vincent_Lin on 2009-02-13
Hi all,

I have installed ubuntustudio 64 bit on my HP tx2z vi DVD.  This is the second time that I installed on it after a long tweaking and messing around on touch screen, fglrx, Broadcom wireless driver.  So I learned all steps/tweaks for the setup but the machine was left with some funny behaviour.  Therefore the second installation.  The second time of installation gave me a fully working computer according to what I want and what I like.  Only thing that is not tweaked/setup yet is fingerprint reader which I couldn´t care less to work on it.   

The whole computer works so great for a couple of days after the second installation, then the sound suddenly stopped working.  No sound from all applications where it worked fine right after installation.  Also I had not started jack setup and tweaking yet, and everything was/is running pulseaudio on top of alsa, on the hardware that lspci reports as:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

dmesg | grep hda shows:

vincent@tx2z:~$ dmesg | grep hda
[   15.880063] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[  138.414285] hda-intel: Invalid position buffer, using LPIB read method instead.

/etc/modprobe.d/alsa-base is a long long file that I had not touched

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2


There was not tweak for sound at all, ie, every setting is the default after the installation. 
 
Judging by dmesg and /etc/modprobe.d/alsa-base, there must be something wrong on what and how the modules loaded, but my capability prevents me from looking it further and finding the resolution.

Can anyone help me to find a way to work it out?  Some pointer to information?  Some experience for resolving this problem?

Thanks all,

Vincent Lin

---

### Post by ussndmac on 2009-02-13
Have you tried 'aplay' in a terminal window?

Mac

---

### Post by Vincent_Lin on 2009-02-13
Thanks for the prompt reply.

aplay picks up the m4a file to play, but no sound.  

top reports that pulseaudio is on the top of all running process.  aplay is at the fourth or fifth position.

So, no sound from aplay.  Where sould I go to look further?

Thanks.

Vincent

---

### Post by ussndmac on 2009-02-13
If you haven't yet, in a terminal window try 'alsa-mixer' and make sure all the appropriate channels are cranked up.

Also, check the Applications > System > Preferences > Sound (I think that's the menu picks...I'm not near an Ubuntu machine at the moment) and check the all things are still pointing to the alsa device.

---

### Post by Vincent_Lin on 2009-02-14
I have tried all the options on alsamixer and non worked.

Thanks for the suggestions.

Can someone help me to look at my /etc/modprobes.d/alsa-base and dmesg output, that I posted on top, and help me to debug it?

Thanks.


Vincent

---

### Post by Vincent_Lin on 2009-02-14
Hi I really hope someone can give me a pointer as to where to look for problems and solutions.

I just tried dmesg  | hda again and it turned out differently:

vincent@tx2z:~$ dmesg | grep hda
[   16.660107] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   71.134319] hda-intel: Invalid position buffer, using LPIB read method instead.
[  100.363224] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  112.856059] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x10a90000
[  113.860030] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x10a90000
vincent@tx2z:~$ 

And setting at System -> preferences -. Audio:
When I click Test on Video/Audio devices when the driver is set to 

HDA ATI SB ALC(268) Analog (ALSA)

A window pops out saying that 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

Please someone help to find the source of the problem, and fix.

Thanks a lot.

Vincent

---

