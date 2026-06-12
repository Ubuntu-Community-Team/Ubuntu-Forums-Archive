---
title: "No sound outside of myth"
date: 2010-11-23
forum: Mythbuntu
---

### Post by moodog on 2010-11-23
I am running mythbuntu 10.04, and am having problems with getting sound out of anything outside of mythtv. I upgraded everything from about 9.04 to 10.04 using dist upgrade about 9 months ago. Prior to this if myth was running and I (eg.) opened youtube in firefox, I'd get sound from youtube. Now I can't seem to get sound from anything other than myth. Even if I shut down the front end and back end processes, I'm still unable to get sound. I have no troubles with sound within myth though.

Any suggestions for where to start looking?


Edit: just found this thread - will give it a go and hopefully it will fix the problem.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1501316](http://www.uluga.ubuntuforums.org/showthread.php?t=1501316)

---

### Post by moodog on 2010-11-25
My first post was probably lacking a bit in detail - see below.

Ok, so I followed what was in that other thread, and at least I can now play other sources, however I've still got issues.

If I set Speakers Configuration in Myth to 5.1, whenever I play music through MythMusic and then play another source (i.e. aplay, or youtube etc.), the myth audio becomes just choppy static. As soon as I stop/pause the other source all is good. If I set the Speakers Configuration in myth to Stereo though, all is good. Multiple sources can play at the same time without issue.

I'm also having another minor problem where there seems to be something wrong with the signal - every so often (5-10 seconds, sometimes more random), there is a short pause in the audio - at the same time I notice the front of my amp flash. 

Details:

I have a sound card in my machine (i.e. not using onboard audio) and use the optical out to take the sound to my amp - configured to use PCM out.

output from aplay -L

```
null
    Discard all samples (playback) or generate zero samples (capture)
analog
    Analog Output - Use analog outputs, converting samples, format, and rate as necessary.
mixed-analog
    Mixed Analog Output - Use analog outputs, converting samples, format, and rate as necessary. Allows mixing with system sounds.
digital
    Digital Output - Use digital outputs, converting samples, format, and rate as necessary.
mixed-digital
    Mixed Digital Output - Use digital outputs, converting samples, format, and rate as necessary. Allows mixing with system sounds.
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
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

```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've tried using aplay -D to output directly to the devices, and have found that card 1, devices 0 and 2 work. I've tried each different configuration with myth, and no change. 

Any advice?

---

