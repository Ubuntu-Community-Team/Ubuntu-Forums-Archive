---
title: "Problems with Mythbuntu - need to disable HDMI audio"
date: 2009-05-10
forum: Multimedia Software
---

### Post by TerranAce007 on 2009-05-10
I have a system with an AMD-780 motherboard with integrated Radeon HD3200 HDMI graphics connected to my 32" LCD tv. I'm running mythbuntu 9.04 with kubuntu-desktop installed and set as the default environment. I have a surround sound speaker system plugged into the pc which I wish to use as default, NOT the HDMI audo. To reiterate, the HDMI is just for video.

Mythtv does not want to play sound consistently and it's becoming very frustrating. I've googled and searched these forums, but nothing I've tried has fixed it. Audio device and mixer are both set to ALSA:default, however when I launch mythtv, I see these errors in the console:

```

2009-05-10 16:37:19.889 Mixer unable to find control PCM
2009-05-10 16:37:19.889 Mixer unable to find control PCM
...
2009-05-10 16:37:59.848 NVP: prebuffering pause
2009-05-10 17:00:27.392 NVP: prebuffering pause
2009-05-10 17:01:35.141 NVP: prebuffering pause
2009-05-10 17:01:37.037 NVP: prebuffering pause
...

```

There's no sound and when I try to change channels, MythTV crashes. Here is some information on my sound cards:

```
 aplay -l
                                
**** List of PLAYBACK Hardware Devices ****                                                                                                                  
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]                                                                                             
  Subdevices: 0/1                                                                                                                                            
  Subdevice #0: subdevice #0                                                                                                                                 
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]                                                                                           
  Subdevices: 1/1                                                                                                                                            
  Subdevice #0: subdevice #0                                                                                                                                 
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]                                                                                                   
  Subdevices: 1/1                                                                                                                                            
  Subdevice #0: subdevice #0    
```

```
cat /proc/asound/cards                                                                               
 0 [SB             ]: HDA-Intel - HDA ATI SB                                                                              
                      HDA ATI SB at 0xfe024000 irq 16                                                                     
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI                                                                            
                      HDA ATI HDMI at 0xfdffc000 irq 19                                                                   
 2 [CX8801         ]: CX88x - Conexant CX8801                                                                             
                      Conexant CX8801 at 0xf8000000   
```  

Card 2, CX8801 is the audio device for the PCTV HD3200 tuner card. This works when I attach the cord from the tuner output to the sound card input, but the audio output is direct and not coming from the buffered mythtv output, so audio and video sync is off by about a second.

KDE4 lists 3 devices in System Settings -> Multimedia:
```

HDA ATI SB (ALC883 Analog)
HDA ATI HDMI, ATI HDMI (ATI HDMI Audio Output)
PulseAudio

```

Both SB and HDMI devices work correctly when I test them. I can hear the sound coming from my TV speakers when I test HDMI.

Now, the interesting part. Sometimes after a reboot, KDE4 will inform me that the HDMI audio device has been removed from the system and it appears greyed out in the system settings -> multimedia section. When this happens, MythTV plays sound fine through my computer's speakers. I can't figure out why HDMI audio disappears occasionally, but I'd like to just disable it and use the SB device as default.

It appears that Myth is trying to use the HDMI audio when it's detected, but can't find the PCM mixer because it's associated with the SB device, possibly due to an .asoundrc config problem. I haven't touched it. All defaults there.

How do I either disable the HDMI device or force Myth to use the SB device and associated mixer?

If that's not possible, how can I force Myth to use HDMI and fix the mixer settings?

---

### Post by jetpeach on 2009-12-12
i'm not sure if this thread would help you
[http://ubuntuforums.org/showthread.php?t=877162](http://ubuntuforums.org/showthread.php?t=877162)
i'm trying to do the same thing as you and just disable the hdmi sound completely, the thread i linked changes the default in theory but doesn't describe how to disable completely. if you found a good way, could you let us know?
thanks!

EDIT: i was able to disable HDMI sound output on my computer by doing the following,
look at output of
cat /proc/asound/modules
the top output was snd_hda_intel , might be the same for you (use the one you want to blacklist). put the line 
blacklist snd_hda_intel 
into the file
/etc/modprobe.d/blacklist.conf
i use " sudo nano /etc/modprobe.d/blacklist.conf " and added at the top. then the hdmi sound module didn't load anymore and i was happy!

---

