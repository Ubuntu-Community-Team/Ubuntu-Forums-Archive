---
title: "Enable 5.1 audio on Fatal1ty Usb Headset"
date: 2009-01-20
forum: Multimedia Software
---

### Post by jiveaxe on 2009-01-20
Hi everyone,
I bought a Creative Fatal1ty HS-1000. This headset mounts a X-F1 card simulating a 7.1 multichannel audio. For testing surround capabilities i found a wav file that, if needed, can been downloaded [here]("http://rapidshare.com/files/186669908/8_Channel_ID.wav.html"); I have played this file in windows and all 8 directions are audible. In kubuntu 8.10 it's not so and I can hear only front left and front right channels (even if they seem side left and side right, respectively).

For what written in various posts ubuntu should be able to work with 5.1 audio but I haven't found a tutorial for a usb device like mine.

Probably I need to edit .asoundrc file for enabling 5.1 but I don't know how.

This is the output of the command aplay -L:

```
giuseppe@kubuntu:~$ aplay -L                                                      
default:CARD=SB                                                                   
    HDA ATI SB, VT1708B Analog                                                    
    Default Audio Device                                                          
front:CARD=SB,DEV=0                                                               
    HDA ATI SB, VT1708B Analog                                                    
    Front speakers                                                                
surround40:CARD=SB,DEV=0                                                          
    HDA ATI SB, VT1708B Analog                                                    
    4.0 Surround output to Front and Rear speakers                                
surround41:CARD=SB,DEV=0                                                          
    HDA ATI SB, VT1708B Analog                                                    
    4.1 Surround output to Front, Rear and Subwoofer speakers                     
surround50:CARD=SB,DEV=0                                                          
    HDA ATI SB, VT1708B Analog                                                    
    5.0 Surround output to Front, Center and Rear speakers                        
surround51:CARD=SB,DEV=0                                                          
    HDA ATI SB, VT1708B Analog                                                    
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers             
surround71:CARD=SB,DEV=0                                                          
    HDA ATI SB, VT1708B Analog                                                    
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers          
hdmi:CARD=SB,DEV=0                                                                
    HDA ATI SB                                                                    
    HDMI Audio Output                                                             
null                                                                              
    Discard all samples (playback) or generate zero samples (capture)             
front:CARD=HDMI                                                                   
    HDA ATI HDMI                                                                  
    Front speakers                                                                
surround40:CARD=HDMI                                                              
    HDA ATI HDMI                                                                  
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
    HDA ATI HDMI
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
default:CARD=Headset
    Creative USB Headset, USB Audio
    Default Audio Device
front:CARD=Headset,DEV=0
    Creative USB Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    Creative USB Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    Creative USB Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    Creative USB Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    Creative USB Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    Creative USB Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Headset,DEV=0
    Creative USB Headset, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
```

Thanks

---

### Post by jiveaxe on 2009-01-21
I'm testing some commands found googling;

1) ```
speaker-test -D plughw:2,0 -c 6 -l 1 -t wav
```

I can hear voice in front left and front right while in remaining positions only noise;

2) ```
aplay -D plughw:2,0 8_Channel_ID.wav
```

(you can download 8_Channel_ID.wav from my first post)

in this case front left and front right is reproduced while the other channels not (mute, no noise)

3) As written in [SurroundSound]("http://alsa.opensrc.org/SurroundSound") in alsa wiki:

> surround51 and surround40 are the generic PCM definitions for 6 (aka 5.1) and 4 (aka 4.0) channel analog outputs. When the ALSA driver supports 5.1 or 4.0 analog output, the corresponding configuration file for ALSA-lib is transparently provided and includes the definition of surround51 and/or surround40. The usage is very simple. Just pass surround51 or surround40 as the PCM name...

aplay -D surround51 foo.wav


but if I run

```
aplay -D surround51 8_Channel_ID.wav
```

audio is played from spekars connected to motherboard audio. Which device should I use?

Cheers

---

### Post by jiveaxe on 2009-01-22
up

---

### Post by mnnn on 2009-02-06
I suggest disabling onboard audio card, or create alias for surround51 (usb Xfi) in ALSA configs

---

