---
title: "No Sound Through HDMI"
date: 2012-02-27
forum: Multimedia Software
---

### Post by Velvet Love Sock on 2012-02-27
I'm having an issue trying to get sound to play through my HDMI. Not too sure what information will be useful for helping solve this problem so I'll just provide a little:

My graphics card: ASUS 8400GS with current NVIDIA 8series driver I got from their website.

Im running Kubuntu 2.6.32-38-generic x86_64

aplay -l:
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L:
default:CARD=SB
    HDA ATI SB, ALC1200 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia
    Default Audio Device
front:CARD=NVidia
    HDA NVidia
    Front speakers                                                                           
surround40:CARD=NVidia                                                                       
    HDA NVidia                                                                               
    4.0 Surround output to Front and Rear speakers                                           
surround41:CARD=NVidia                                                                       
    HDA NVidia                                                                               
    4.1 Surround output to Front, Rear and Subwoofer speakers                                
surround50:CARD=NVidia                                                                       
    HDA NVidia                                                                               
    5.0 Surround output to Front, Center and Rear speakers                                   
surround51:CARD=NVidia                                                                       
    HDA NVidia                                                                               
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers                        
surround71:CARD=NVidia                                                                       
    HDA NVidia                                                                               
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia
    HDA NVidia
    IEC958 (S/PDIF) Digital Audio Output

When i use alsa mixer I have only two choices for sound cards:
HDA ATI SB and HDA NVidia

The HDA NVidia section of alsamixer says: this sound device does not have any controls.


I have searched around the web and cannot seem to find a solution. This is my fourth install of Kubuntu as I have tried many suggestions other people have said and ended up either ruining the graphics driver or just getting to frustrated to continue.

Any suggestions?
Thanks :)

---

### Post by BicyclerBoy on 2012-02-27
Your video card is pre-azalia so it has no HDA audio codecs. It uses the mobo soundcard **if it can at all.**

**If** your card has the header:
The HDMI audio from your video card is routed from the S/PDIF header (on video card).

So you need a 3 or 4 wire cable to link the video card S/PDIF input from the mobo (or other sound card) internal S/PDIF output header.

Then you use the mobo soundcard digital output device.
S/PDIF limits your HDMI audio to 2 ch stereo 96KHz or AC3/DTS pass-thru'.

So first check the card & any documentation for a S/PDIF input header.
Else buy a GT240, GT430 GT220 (or GT520 last option).

---

### Post by Velvet Love Sock on 2012-02-27
Thanks, I'll just upgrade the card.

---

