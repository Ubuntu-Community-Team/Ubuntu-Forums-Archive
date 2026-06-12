---
title: "Can't have my sound card M Audio Audiophile 24/96 working"
date: 2009-11-12
forum: Multimedia Software
---

### Post by softrain on 2009-11-12
Hi, I'm struggling with my soundcard that I can't produce any sound.
I've tried to install xubuntu 9.04, ubuntu 9.04, karmic but still no luck.
the card use to work fine with another box running 9.04

Here is the the result command of aplay -L

```
tom@tv:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    Front speakers
surround40:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    4.0 Surround output to Front and Rear speakers
surround41:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    IEC958 (S/PDIF) Digital Audio Output

```

the card is not mute. I've tried to play with envy24control, but no luck

command

```
tom@tv:~$ speaker-test -c2 -Dplug:iec958

speaker-test 1.0.18

Playback device is plug:iec958
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.634977
 0 - Front Left
 1 - Front Right
^C

```

but still no sound

command: 
tom@tv:~$ alsamixer -c 1

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.18 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
&#9474; Card: M Audio Audiophile 24/96                                                        
&#9474; Chip: ICE1712 - multitrack                                                            
&#9474; View: [Playback] Capture  All                                                         
&#9474; Item: ADC 1 [dB gain=18.00]                                                           
&#9474;                                                                                       
&#9474;                                                                                       
&#9474;                      &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 
&#9474;                      &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 
&#9474;  PCM Out  PCM Out    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      Off    H/W In 0 H/W In 1   
&#9474;                      &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                                 
&#9474;                                                                                       
&#9474;                                                                                       
&#9474;                       95        100      65       69                                  
&#9474;   IEC958  IEC958 1   ADC    < ADC 1  >  DAC     DAC 1    Deemphas   H/W     H/W 1     
&#9474;                                                                                       
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

```


and

tom@tv:~$ speaker-test -c 2 -Dfront:M2496

speaker-test 1.0.18

Playback device is front:M2496
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Sample format not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument


any help or tips would be very welcome indeed!

/art

---

### Post by softrain on 2009-11-12
Oddly enough, when I play a tune with XBMC through the M2496
  envy24control VU Meter is moving like sound was going out!!
but no sound can be heard from the output :(
if my card was damaged, would I had such a behavior?
do anybody have the same issue than me even with same or another chipset?

Thanks for your help

/art1

---

### Post by softrain on 2009-11-12
I've played again with envy24control and it works now :popcorn:
If sb has this kind pb, please feel free to ask my settings.

/art1

---

