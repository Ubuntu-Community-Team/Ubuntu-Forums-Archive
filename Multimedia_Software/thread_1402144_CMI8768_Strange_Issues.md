---
title: "CMI8768 Strange Issues"
date: 2010-02-08
forum: Multimedia Software
---

### Post by Atrixium on 2010-02-08
I'm getting some strange behaviour out of my new CMI8768 card, I can't seem to get surround sound out of it it just shows up as 1 output in Pulseaudio sound preferences. 

Also in sound preferences I have selected the Analog Surround 5.1 Output profile, which appears to exclude the input functions of the card, is there a way around this?

Here's some info:

**_aplay- l_**

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


_**aplay -L**_

front:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI DAC/ADC
    Front speakers
rear:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    Rear speakers
surround40:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server


_**speaker-test**_

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left


I've modified my /etc/pulse/daemon.conf to set default to 6 channels but it doesn't seem to affect anything. A number of documents I've seen on Google have made reference to the "asound.conf" but apparently I *shouldn't* need this.

Any assistance anyone can offer would be greatly appreciated!



_**System Info**_

Linux Mint 8 (Ubuntu 9.10) 64 Bit Kernel 2.6.32
AMD Athlon 64 X2 5200+
CMI8768 Sound card
Nvidia 9500GT Video card

---

### Post by Atrixium on 2010-02-11
Bump. Any PulseAudio wizards around?

---

### Post by markbuntu on 2010-02-12
I have one of those cards. FYI, the line-in and mic-in rear jacks are switchable. Line in can be rear or bass output, mic in can be center or lfe output. So, if you want surround sound these cannot be used for input, sorry. 

Have you tried playing any actual surround sound files or streams?

---

### Post by Atrixium on 2010-02-12
Thanks for the reply, I appreciate it!
 
I did try a surround DVD but it appeared that the front audio was being played from the rear outputs as well which seems consistent with speaker-test thinking I only have 1 output device.
 
I've also tried speaker-test -c 6 but that also only gives me the one input rather than the 6 discrete channel tests.
 
As for the Mic-in, in light of your recent revelation about my card I've decided to use a USB mic for my input, which should take care of that little issue.

---

### Post by markbuntu on 2010-02-12
Can you get stereo working?

Did you reinstall alsa after you put this card in?
You might want to try that.

(1) Remove the ALSA packages
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```


Packages gdm and ubuntu-desktop may also be removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

``` 

(3) Reboot

---

### Post by Atrixium on 2010-02-12
Unfortuantely no, just left speaker that appears to be sent to all 6 speakers.
 
I hadn't thought of removing and re-installing ALSA, it makes sense though from what little I understand of the Linux sound system. I just did some reading and it looks like I misunderstood the relationship between Pulseaduio and ALSA.
 
I'll try to uninstall and re-install ALSA when I get home today and report back on what happens.
 
Thanks!

---

### Post by Atrixium on 2010-02-13
Well, I followed through those steps and nothing has changed, I'm starting to think it might actually be a hardware issue, anything else you might be able to suggest?

---

### Post by Yellow Pasque on 2010-02-14
You might try upgrading to the latest ALSA drivers: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by Atrixium on 2010-02-15
Thanks guys! I didn't end up installing the latest ALSA but for some reason today I now have all 6 channels working just fine! Nothing changed except I plugged in a USB headset for mic input and all of a sudden I have 5.1, weird.  Thanks again for the help!

---

