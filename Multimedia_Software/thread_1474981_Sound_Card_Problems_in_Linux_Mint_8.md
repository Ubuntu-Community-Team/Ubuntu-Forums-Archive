---
title: "Sound Card Problems in Linux Mint 8"
date: 2010-05-06
forum: Multimedia Software
---

### Post by AvataroftheSun on 2010-05-06
Hi.  I've recently installed Linux Mint 8 64-bit on my computer and need some  help with getting my sound card to work.  I've been searching around the  internet for solutions but I know next to nothing about computer audio.

My  sound card is a PCI Express Creative Sound Blaster X-Fi Xtreme Audio.   Came with my computer.  Told it uses the SB Audigy chipset.  Using the onboard audio is not an option.

The card shows up in Sound Preferences under the Hardware tab, but I cannot get sound from it.

I tried looking for help on the Linux Mint forums but they were unable to help.  Here's what they told me to do:
   Install the karmic alsa backports through the Terminal
   Install hidden Level 5 updates to update the kernel
   Disable every audio device except the SB card (the others are onboard  and HDMI)
   Check volume levels in alsamixer, PulseAudio Device Chooser and Volume Control

I also tried to install the OpenAudio driver (not sure, will double check), which crashed Linux every time I try to activate it.

Any  further information about my computer will be supplied if necessary.

Thanks.

---

### Post by AvataroftheSun on 2010-05-08
Anyone have any ideas here?  I have no idea how to proceed and I've tried everything I can think of.

---

### Post by lidex on 2010-05-08
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by AvataroftheSun on 2010-05-08
Output of commands:
```
corey@corey-desktop ~ $ uname -a
Linux corey-desktop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux
corey@corey-desktop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
corey@corey-desktop ~ $ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar 25 2010 for kernel 2.6.31-21-generic (SMP).
corey@corey-desktop ~ $ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

==> /proc/asound/card2/codec#1 <==
Codec: Creative CA0110-IBG

```My computer is an Alienware Aurora Desktop built in December 2009, so fairly recent.  Any other info you need?

---

### Post by lidex on 2010-05-09
It would be easier if you disabled onboard sound in bios.

---

### Post by AvataroftheSun on 2010-05-09
Onboard Sound has been disabled from BIOS.  It had no effect.

---

### Post by lidex on 2010-05-09
Sure it has. What is 
```
aplay -l
``` now?

---

### Post by AvataroftheSun on 2010-05-09
```
corey@corey-desktop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Although, that's to be expected.
Regardless, I had already disabled it in the PulseAudio controller.  I don't really see what effect disabling it in the BIOS would have considering PulseAudio didn't use it anyway...

---

### Post by enchesss on 2010-05-09
have you tried to blacklist the hdmi?

Not sure if post #6 will work for you?

[http://ubuntuforums.org/showthread.php?t=844794](http://ubuntuforums.org/showthread.php?t=844794)

---

### Post by lidex on 2010-05-09
Can you post output of this command please:
```
lsmod | grep snd
```

Also something that is useful here is pulseaudio volume control, or pavucontrol, especially the configuration tab. If not installed:
```
sudo apt-get install pavucontrol
```
You can change profiles here.

---

### Post by AvataroftheSun on 2010-05-09
> **enchesss said:**
> have you tried to blacklist the hdmi?

Not sure if post #6 will work for you?

[http://ubuntuforums.org/showthread.php?t=844794](http://ubuntuforums.org/showthread.php?t=844794)

No good.  The HDMI and Sound Card are listed under the same name.  Blacklisting one will disable the other.  Don't really know why though...

Output of lsmod | grep snd:

```
corey@corey-desktop ~ $ lsmod | grep snd
snd_hda_codec_ca0110     9440  1 
snd_hda_codec_atihdmi     4384  1 
snd_hda_intel          30176  6 
snd_hda_codec          96320  3 snd_hda_codec_ca0110,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               9448  1 snd_hda_codec
snd_pcm_oss            44096  0 
snd_mixer_oss          19008  1 snd_pcm_oss
snd_pcm                93544  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3556  0 
snd_seq_oss            33632  0 
snd_seq_midi            8320  0 
snd_rawmidi            27200  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                61312  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25840  2 snd_pcm,snd_seq
snd_seq_device          8500  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77960  24 snd_hda_codec_ca0110,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10960  2 snd_hda_intel,snd_pcm
```

I already have PulseAudio volume control.  I'm pretty sure it came preinstalled with Mint.

---

### Post by lidex on 2010-05-09
Have you tried a different profile in pavucontrol configuration?
And one more command output:
```
cat /proc/asound/modules
```

Reference:
[http://ubuntuforums.org/showthread.php?t=922860]("http://ubuntuforums.org/showthread.php?t=922860")

---

### Post by AvataroftheSun on 2010-05-09
Output of cat /proc/asound/modules (this is after disabling the onboard from the BIOS of course):
```
corey@corey-desktop ~ $ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel
```
Tried changing the profile.  The only time anything happens is when the output isn't specified or the profile is set to "Off."

---

### Post by lidex on 2010-05-09
> **AvataroftheSun said:**
> Output of cat /proc/asound/modules (this is after disabling the onboard from the BIOS of course):
```
corey@corey-desktop ~ $ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel
```
Tried changing the profile.  The only time anything happens is when the output isn't specified or the profile is set to "Off."

What about the port setting on output devices tab?

---

### Post by AvataroftheSun on 2010-05-09
> **lidex said:**
> What about the port setting on output devices tab?
There are two: "Analog Output" and "Analog Headphones".  Switching between the two had no effect.

---

### Post by AvataroftheSun on 2010-05-11
One thing I'm considering doing is reinstalling Mint over the one I have, thus returning the system to, probably, an easier to handle state (no kernel modifications, no high-level updates, no drivers, etc.).  Would that be recommended?

Edit: Never mind.  I'll only reinstall if there's something I installed that's messing things up for sure.

---

### Post by AvataroftheSun on 2010-05-16
Anyone have any ideas?  I tried contacting Creative and Dell about my card and they've been of absolutely no help.  I want to finally ditch Windows and this is the only thing preventing me.

---

