---
title: "Audio not working on Dell E-Port docking station in Jaunty (9.04); was OK in 8.04"
date: 2009-05-07
forum: Multimedia Software
---

### Post by pcls on 2009-05-07
I have a Dell Latitude E6400 notebook and a Dell E-Port docking station.  Sound through the docking station (i.e. the headphone jack on docking station) was working well in Ubuntu 8.10.  On upgrading to Jaunty (9.04), sound stopped working through the docking station. 

With or without speakers plugged into the docking-station headphone jack, sound now comes through the notebook built-in speakers.  If I plug the speakers into the notebook headphone jack, the notebook built-in speakers are correctly disabled and sound comes through the external speakers (albeit with slightly poor quality).

I have also tried reinstalling Jaunty 9.04 from scratch (in case the problem was somehow due to the upgrade process), but the problem is unchanged.

I've read some posts about selecting the IEC958 switch in the volume control (through the Volume|Preferences button), but this option does not exist.

Output of "aplay -l":
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0Output of "cat /proc/asound/card0/codec#* | grep Codec":
> Codec: IDT 92HD71B7X
Codec: Conexant ID 2c06I have also tried, without success,  the following (using "model=dell-m4-1" and even variations m41, m4-2, ...) as suggested on the thread [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258630) 
> 1. create/edit file "/etc/modprobe.d/sound" and change the content to:

      options snd-hda-intel model=dell-m22 enable=1 index=0
      alias snd-card-0 snd-hda-intel
      alias sound-slot-0 snd-hda-intel

2. rebootcat /proc/asound/modules:
```
 0 snd_hda_intel
 1 snd_usb_audio
```cat /proc/asound/cards:
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6fdc000 irq 21
 1 [Q9000          ]: USB-Audio - QuickCam Pro 9000
                      Logitech, Inc. QuickCam Pro 9000 at usb-0000:00:1a.7-4.1.2, high speed
```lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 160M (rev a1)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```lsmod | grep -i snd
```
snd_usb_audio          90400  1 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_usb_lib            24320  1 snd_usb_audio
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_hwdep              15108  1 snd_usb_audio
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  19 snd_usb_audio,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
soundcore              15200  1 snd
```cat /etc/modprobe.d/alsa-base.conf 
```
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
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```Can anyone help me get sound through the docking station please?

---

### Post by pcls on 2009-05-07
Sorry, I was using **Ubuntu 8.10** when the sound through the docking station was working.

---

### Post by pcls on 2009-05-12
I've still not have any luck with this.  I get the feeling from other threads about sound that the current versions of intel-hda sound modules in the kernel need quite a few bugs ironed out.  Is there nothing I can do but wait for the appropriate updates?

Any ideas?

---

### Post by cjsteele on 2009-05-12
unfortunately, you're being bitten by a bug in the kernel... maybe not the upstream kernel coders' fault, but how it gets packaged in Ubuntu.  I have run into this literally dozens of times over the years, and ran into the same exact problem.  I have an Intel HDA chipset in my HP nx9420 and sound broke after a kernel update to whatever the current 9.04 kernel image is.  I upgraded to Karmic and the kernel image there (2.6.30-xyz) allows sound to function, but when there are multiple programs accessing sound, it gets garbled.

---

### Post by brownrc on 2009-05-14
I have an latitude E6400 with the Docking station as well. The audio port on the Docking station worked with 8.10 but no longer works after I upgraded to 9.04. The audio port on the actual laptop works fine as do the built in speakers on the laptop. Hopefully a patch will be issued soon.

---

### Post by cjsteele on 2009-05-14
I downgraded to the 2.6.28-11 kernel and have been very happy with the sound and performance -- I suggest you give that a shot until a new kernel is available from distribution.

-C

---

### Post by brownrc on 2009-05-15
I am running kernel 2.6.28-11 with no luck in getting sound out of the docking station. :(

```
$ uname -a
Linux copernicus 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

from dpkg-query -l linux-image*
linux-image-2.6.28-11-generic              2.6.28-11.42

---

### Post by cjsteele on 2009-05-16
Sorry mate.  

Check this out though: I had to reboot this morning (stupid citrix session dorked my mouse, and a log-out didn't fix it) and when I rebooted, I forgot to select the 2.6.28 kernel, but sound is working swimmingly with 2.6.30-5... wtf?

I'm at a loss.  Maybe its not a kernel problem?  What ver of alsa you go?

-C

---

### Post by twm3 on 2009-05-24
Very small data point for you'all - unfortunately I don't understand the implications.

I installed the default kernel, 2.6.28, about 2 weeks ago. No sound when my Dell D630 was docked. Nmad it. :sad: I happened to boot up in Linux (versus Windoze Vista) when off the dock and had sound. Sweet. Did some work and believe I turned the machine off. Put the machine back on the dock, booted into Linux, started doing some work and then finally realized that I had sound. Bottom line: a boot off the docking station seemed to kick start something so when I went back onto the docking station, I had sound through the docking station.

My D630 has the Intel X3100 graphics chipset in it. Ugh, Jaunty has been a killer on graphics. Almost painful at times and that's only for business graphics, bringing up or dragging browsers, etc. Read where Intel wasn't playing nicely with Linux for this release, there was a bug, slow performance, etc. Found a "work around" which I installed so my kernel changed from 2.6.28 to 2.26.29. Not sure if my graphics performance increased in a significant way. What I do know, unfortunately, is that my sound when in the docking station is not working. :sad: But sound off the docking station is working. 

Hope that helps someone who has a clue as I am certainly lacking a/the clue.

~twm3

---

### Post by pcls on 2009-05-25
Thank you twm3.

I gave this a try (i.e. booting without docking station), just in case it helped me too.  No such luck.

---

### Post by pcls on 2009-05-25
> **cjsteele said:**
> Sorry mate.  

Check this out though: I had to reboot this morning (stupid citrix session dorked my mouse, and a log-out didn't fix it) and when I rebooted, I forgot to select the 2.6.28 kernel, but sound is working swimmingly with 2.6.30-5... wtf?

I'm at a loss.  Maybe its not a kernel problem?  What ver of alsa you go?

-C

Thanks C.

Alsa version 1.0.18.  

I haven't tried kernel 2.6.30-5, I just have the version released as standard (jaunty-updates repository) with ubuntu 9.04.  So, are you getting sound through your docking station in the newer kernel?  If so, did you (i.e. can I) get the kernel through the jaunty-proposed repository?

---

### Post by cdEWoozy on 2009-05-30
I also have the Dell Latitude E6400. I only get sound out of the built-in speakers or the headphone jack from the notebook.

Behavior with Ubuntu 9.04:
Sound never worked with the headphone jack (hpj) of the docking station. The built-in hpj worked, as did jack-sensing (automatic disabling of the built-in speakers when something was plugged into the built-in hpj. Did not work for the hpj of the docking station).

Behaviour with Ubuntu 9.10 alpha 1 (fresh install, default settings):
I'm getting sound if speakers are plugged into the hpj of the docking station, but the built-in speakers are neither automatically disabled (no jack-sensing working there) nor do I see how I could do that.
I have four volume sliders available: Master, Headphone, PCM and Front. Headphone controls the built-in hpj, Front controls the built-in speakers and hpj of the docking station.
I checked whether some switch (e.g. IEC958, whatever that is) would do the trick, but nothing worked.

Does anyone know of an existing bug report or should we file a new one?


Additional information for the sake of a complete report :)

```
linux-image-2.6.30-6-generic 2.6.30-6.7
alsa-utils 1.0.20-1ubuntu1
```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD71B7X
Codec: Intel G45 DEVCTG
```

```
$ cat /proc/asound/modules
 0 snd_hda_intel
kai@tezra:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6adc000 irq 21
```

```
$ lsmod | grep -i snd
snd_hda_codec_intelhdmi    14848  1 
snd_hda_codec_idt      70316  1 
snd_hda_intel          30440  3 
snd_hda_codec          79296  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_pcm_oss            44960  0 
snd_mixer_oss          19072  1 snd_pcm_oss
snd_pcm                92776  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3428  0 
snd_seq_oss            33568  0 
snd_seq_midi            8160  0 
snd_rawmidi            27392  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60992  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    76968  18 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8960  1 snd
snd_page_alloc         10896  2 snd_hda_intel,snd_pcm
```

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.2 SD Host controller: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
```

---

### Post by kedmond on 2009-06-04
I have nothing useful to add...just that I have a Dell Latitude E6400 with a dock and I've had the exact same problem.  :-(

The sound and docking works perfectly under Windows XP however.  Oh well...

-Kazem

---

### Post by cdEWoozy on 2009-06-04
I filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/383756](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/383756)

It would be nice if someone could confirm it.

---

### Post by twm3 on 2009-06-21
Sound back working.  Follow on to my earlier posting. For reasons that are beyond me and I don't have the time and/or expertise to figure out, Jaunty's sound stopped working for me. NMAD. So I went back to Intrepid and ran into the same sound "hitch" that other's had run into: they had sound but the volume control didn't work. Was fine with me as I could usually control the volume through the application requiring sound (slacker.com, etc.) and/or through the volume control on the speakers.

For reasons I don't recall, I installed Kubuntu 9.04 and ran into the same problem as with other 9.04 installs. The Kubuntu sound options were easier to explore for me and ran across something where I enabled PCM (whatever that is). Whee, sound. But since Kubuntu didn't have the Gnome "Add/Remove..." and I was having a hard time navigating around on Kubuntu, I did a clean install of Ubuntu 9.04. No sound. Not a big surprise.

Tried the same trick of turning on the various PCM options and I have sound. Same problem where there is no volume control but I do have sound. Sweet.

Here are my sound settings. I don't know what the settings do, don't have time to explore cutting them back (I assume that I have some unecessary options set) but I have sound.

Dell D630 on docking station:

Device: HDA Intel (Alsa mixer)
   Playback Tab
      Shows Master, PCM, and Front - with all sliders set at half way 
   Switches Tab
      IEC958 Default PCM: checked
   Options Tab
      IEC958 Digital Playback
   Preferences:
      Master, PCM, Front, IEC958 Default PCM, and IEC958 Playback Source are all
         checked

Device: SigmaTel STAC9205 (OSS Mixer)
   Playback Tab
      Shows Volume, In-gain, and Digital-1 - all sliders set at 

Device: Playback: HDA Intel - STAC92xx Analog (PulseAudio Mixer)
   Playback Tab:
      Master Slider - half-way (this is working a binary switch: if at minimum, no sound;
         anything else there is sound

I suspect that the "Device: Playback: HDA Intel - STAC92xx Analog (PulseAudio Mixer)" setting is the key to the lack of sound.

Drop me a line if you need more specific information and can also tell me what I need to do give you more specific information.

My approach reminds me of a thousand monkies typing will eventually produce all of Shakespeare's works. At least sound is working.

~Tom

---

### Post by NemoTheLobster on 2009-07-30
On my D630 I put the Karmic kernel (2.6.31-4) on Jaunty and enabled the IEC958 options in the mixer.  The "IEC958 Default PCM" needs to be enabled and "IEC958 Playback Source" set to "Digital Playback" to get any sound.  There is a third switch just labled "IEC958" that toggles between docking station and internal speakers.

I installed the karmic kernel for video and DFS issues before messing with sound, so not sure if it's required.

---

### Post by pcls on 2009-09-03
There has been some progress on this problem in launchpad bug reports: [https://bugs.launchpad.net/bugs/387866](https://bugs.launchpad.net/bugs/387866)

Blirp (in comment #12) reports that the following will enable sound through the docking station, but does not mute the internal speakers.
> I got this to work by following steffen's second post here [http://www.linlap.com/wiki/dell%20precision%20m4400](http://www.linlap.com/wiki/dell%20precision%20m4400) (the one at Monday 13 of April, 2009 [12:09:14]), but I didn't modify alsa-base.conf.
 * In the Volume control, click Preferences
* In the Preferences check Import1 Mux
* Close Preferences
* In the new 'Recording'-tab, unmute the microphone.
 Sound now comes through the speakers attached to the docking station. It still doesn't mute the speakers on the machine.

        


It works this way for me too.

---

### Post by jdmulloy on 2010-03-17
I'm running the latest Kubuntu Lucid beta and this is working *perfectly* :D

I have speakers plugged into the dock and no sound comes out of the built in speakers. When I plug headphones into the laptop no sound comes out of the speakers. I did install pulse audio, not sure if that helps or not.

---

