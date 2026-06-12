---
title: "Karmic Koala with sound card Intel ICH6"
date: 2010-01-29
forum: Multimedia Software
---

### Post by openversus on 2010-01-29
Hi to all!
I have recently moved to 9:10 and I found some problems with the sound card Intel.
Reading some posts I managed to partially solve the problem and now I hear the music perfectly but only from the headphones: but I need to "unflug" external amplifier in gnome-alsa-mixer each time I reboot ... otherwise I not even feel the headphones ... boh?

lspci:
00:1 e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

aplay-l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1 / 1
  Subdevice # 0: subdevice # 0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1 / 1
  Subdevice # 0: subdevice # 0



Can you help me?

Buena Vida!

---

### Post by openversus on 2010-02-02
No way... 	](*,)
I tried to install again Alsa package with no results...
Many people has problems with this soundcard...
Hoping to find a solution... \\:D/


Buena vida!

---

### Post by AndriusKulikauskas on 2010-03-28
I have the same sound card.  I also have no sound.  I lost the sound when I upgraded to Karmic Koala.  Maybe because I replaced an alsa related file during the upgrade.  I appreciate any help.  Here's my link to what worked with previous versions: [http://www.worknets.org/wiki.cgi?LinuxOnLaptops](http://www.worknets.org/wiki.cgi?LinuxOnLaptops)

---

### Post by AndriusKulikauskas on 2010-04-16
I followed the suggestions in this [troubleshooting guide]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") and upgraded my Alsa files.  [Here's the resulting diagnostic.]("http://pastebin.ca/1863035")  But still no sound!

---

### Post by Yellow Pasque on 2010-04-16
Play with some of the controls in alsamixer, for example:
> On some platforms, particularly the IBM Thinkpad T40 series, the Headphone Jack and/or Line Jack inputs need to be muted in order to hear sound at all. The alsamixer app can do this for you by using the 'm' toggle to mute/unmute.

---

### Post by lidex on 2010-04-18
AK, what's interesting is your linked page states your codec as AD1981B but alsa-info shows snd_intel8x0. This is an AC97 codec.
Can you post the contents of this file please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by mve-lamb on 2010-04-27
> **lidex said:**
> AK, what's interesting is your linked page states your codec as AD1981B but alsa-info shows snd_intel8x0. This is an AC97 codec.
Can you post the contents of this file please:
```
cat /etc/modprobe.d/alsa-base.conf
```

Hi , I have same problem.... and same hardware so, I think openversus will not mind to post instead him:
> mve@mtmp:~$ lspci -v
....
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: IBM Device 0567
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at 90040800 (32-bit, non-prefetchable) [size=512]
	Memory at 90040400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
	Subsystem: IBM Device 0576
	Flags: medium devsel, IRQ 23
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

.....
mve@mtmp:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mve@mtmp:~$ cat /proc/asound/cards
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 22
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 70HT28WW-1.05
mve@mtmp:~$ cat /etc/modprobe.d/alsa-base.conf
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
mve@mtmp:~$ lsmod |grep snd
snd_intel8x0           25588  2 
snd_seq_dummy           1338  0 
snd_ac97_codec        100646  1 snd_intel8x0
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
ac97_bus                1002  1 snd_ac97_codec
snd_rawmidi            19056  1 snd_seq_midi
snd_pcm_oss            35308  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
snd                    54148  15 thinkpad_acpi,snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
mve@mtmp:~$


Even with U 10.04 B/B2/RC problem still present :confused:

MVE

---

### Post by klemes on 2010-04-27
Here is a useful guide about this type of sound cards:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I am entirely out of  context here but I 'll try anyway.
In more than one of my systems I have an Intel HDA card and I 've found out that  
adding the parameter model=auto at the end of the line 'options snd-hda-intel' in /etc/modprobe.d/alsa-base.conf and then reloading alsa or rebooting helps recognizing the correct type of card I have and restores sound in my system.:guitar:

---

### Post by AndriusKulikauskas on 2010-05-02
Temüjin, Lidex, Klemes, Thank you for your posts.

I upgraded to Lynx and sound didn't work.  

What got it to work was going to Sound Preferences -> Output -> Connector and changing it from Analog Output / Amplifier to Analog Output / No Amplifier.

I'm using the original alsa-base.conf which I include below but I had earlier added model=auto to the line snd-intel8x0m index=-2 after which I think the "internal audio" appeared on the Hardware list in the Sound Preferences, so that may have triggered something helpful, too.  I changed that line but "internal audio" is still in the Hardware list.

Thank you for helping! It's nice to have sound.

Here's more about what I tried:
[http://www.worknets.org/wiki.cgi?LinuxOnLaptops](http://www.worknets.org/wiki.cgi?LinuxOnLaptops)


-----------

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2 
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

# Andrius 2010.05.02
#options snd-hda-intel model=thinkpad
root@dorasai:/etc/modprobe.d#

---

