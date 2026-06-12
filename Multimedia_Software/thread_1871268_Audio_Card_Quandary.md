---
title: "Audio Card Quandary"
date: 2011-10-28
forum: Multimedia Software
---

### Post by kbarz on 2011-10-28
I'm working to set up a machine for the kids of my mother's daycare using QIMO 2.0 which is built on Ubuntu (if I remember right, it's 10.04.)  I have motherboard audio (Intel D865perl) which doesn't seem to work at all.  QIMO identifies my pci audio card as a C-Media cmi8738.

I can get the pci card to work via pulseaudio and one of it's many controls finally activates it.  The problem is then that some of the kid oriented programs seem to have a problem with that solution.  In particular, TuxPaint will hang on exit to the point where I have to kill -s it.  So, kind of defeats the purpose for the kids.

Anyhow, I've looked into some reports on the TuxPaint/PulseAudio issue, and they said then to remove pulseaudio completely and use alsa.  One QIMO reinstall later and TuxPaint works perfectly, but I can't find anyway to get the sound card to work with alsa.  

So, is there a way to force the card and alsa to play nice?  Otherwise, what commonly available alsa compatible cards are out there (e.g. hopefully not requiring a drive all the way across town to MicroCenter or mail order?)  Looks like for speakers I have an Altec Lansing ATP3 setup. 

Thank you in advance for your help.  The daycare kids thank you too.
Ken

---

### Post by BicyclerBoy on 2011-10-28
aplay -l
aplay -L

Why would TuxPaint screw up pulse audio ? Does TuxPaint make sound as well ?

---

### Post by kbarz on 2011-10-28
aplay -I want a filename, and I'll beg ignorance over what I should be telling it.

Below is what aplay -L comes back with.  I'm assuming the ICH5 is the motherboard audio that isn't working.

As to tux paint, it uses a little sound to start and end.  Searching online for the issue has said that pulseaudio was the culprit, though I just found another posting that contradicts that, saying it's alsa:  [http://www.tuxpaint.org/docs/known_issues/](http://www.tuxpaint.org/docs/known_issues/).  The other kid programs seem to play their sound ok with a pulseaudio configuration.

It's what I get for being a Windows geek all these years.

cheryl@Cheryls-Playschool:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Front speakers
surround40:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output
front:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Front speakers
rear:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    Rear speakers
surround40:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    4.0 Surround output to Front and Rear speakers
iec958:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output

---

### Post by kbarz on 2011-10-28
Found part of my problem on another forum.  Seems the motherboard audio was in the top two slots, and the cmi8738 was at #2.  Editing /etc/modprobe.d/alsa-base.conf I was able to change it around to this:

0 snd_cmipci
1 snd_intel8x0
2 snd_hda_intel

Still no sign of sound but hopefully this is a step in the right direction?

---

### Post by BicyclerBoy on 2011-10-28
Why use a soundcard ?

The mobo sound has S/PDIF etc ..does the mobo sound not have output connectors ?

Changing the order does nothing as far as I know..

That cmd was lower case L
Both again please..

aplay -l
aplay -L

---

### Post by kbarz on 2011-10-29
It does have output connectors.  The reason it has a separate audio card was that for its long life as a windows machine, the d865perl required separate drivers for audio, lan, ... that didn't come automatically with xp.  Then intel quit support.  Moot point so far as I've heard nothing from the mobo audio and sporadic from the audio card (then a weird message about connection terminated.)  Here's all the aplay output.  And forgive me, I apparently need to look up all the audio terminology (S/PDIF, ...) and why one is better than the other.  With my main box with windows 7 and the most current ubuntu, it detected everything on install and has worked perfectly.


cheryl@Cheryls-Playschool:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cheryl@Cheryls-Playschool:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Front speakers
rear:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    Rear speakers
surround40:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    4.0 Surround output to Front and Rear speakers
iec958:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output
front:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Front speakers
surround40:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

---

### Post by BicyclerBoy on 2011-10-29
Assumimg you are using stereo analogue output..

Plugged into PCI soundcard:
speaker-test -c 2 -r 44100 -D hw:0,0

Plugged into mobo jacks:
speaker-test -c 2 -r 44100 -D hw:1,0

should hear pink noise in each channel.

XP stuff: I have found that chipset drivers from intel fixes lots of PC problems with optical drives, missing audio h/w etc. 

Intel mobos seem to have their problems & need bios updates.

That HDA-intel sound device is not mobo chipset, it is the HDA codec in the video card.

---

### Post by kbarz on 2011-10-29
Hmm.  Nothing in either case.  Went ahead and pulled the pci card to reduce complexity.  Here's the config now:

 1 snd_intel8x0
 2 snd_hda_intel

Looks like the hda/hdmi is actually referring to the hdmi jack on my video card.

cheryl@Cheryls-Playschool:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cheryl@Cheryls-Playschool:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Front speakers
surround40:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

---

### Post by BicyclerBoy on 2011-10-29
The HDA-intel codec is in the video card..I stated that before..

HDA-intel is an audio std like AC97..

Your /etc/modprobe.d/alsa-base.conf hacking is causing the first card to be identified as card 1 but that should not matter..

Are your speakers just plugged into the 3.5mm jacks ?
Just stereo (1x 3.5mm jack)..plugged into light green jack..

---

### Post by kbarz on 2011-10-29
Green plug into green jack.  Check.  However, your last comment did provide some insight.  Turns out the mobo has one audio connection, but the wiring from the new case has two connectors off the same wiring.  I had HD Audio plugged into the mobo.  The other connector had AC97 printed on it.  I switched them and now speaker-test -c 2 -r 44100 -D hw:1,0 works as advertised.  My understanding from the documentation is that this wiring is for the front panel audio, but whatever, speaker-test works now.  

So, I assume there's something else I have to tell it to use this for system and application sounds?  I've launched one app that I know has sound, but it's silent.

---

### Post by kbarz on 2011-10-29
Hah!  Got it!  Changed over the front panel plug to the mobo, tried several different controls on the default mixer to no avail.  Finally re-downloaded the pulseaudio volume control and device selector which I've had limited success with the pci card.  Selected internal audio and adjusted the slides and presto:  the apps make annoying kid music (but that was the idea.)

Went to TuxPaint config and re-enabled sound there.  So far it will play sound and shut down without needing the process to be killed.  I'll hammer on it some more, but hopefully this has it.

Thank you for all your help!
Ken

---

