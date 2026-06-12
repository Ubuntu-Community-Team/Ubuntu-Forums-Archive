---
title: "Kubuntu 14.04.1 LTS No Surround Sound 5.1 on ALC887-VD"
date: 2015-01-10
forum: Multimedia Software
---

### Post by jim_10 on 2015-01-10
Hello,
 I have a small problem with the sound configuration in Kubuntu KDE. I have a pc which serves me as a media center with xbmc, pc is connected to the TV via HDMI cable and the TV is connected to a home theater system via HDMI cable.
In Pavucontrol choose to output HDMI 5.1 Digital Surround and then audio and video settings - audio device settings there have also selected in the test 5.1 but heard only the front left and right speakers or other speakers do not work.
[IMG]http://imageshack.com/a/img537/2093/Bkndoi.jpg[/IMG]

When Will I choose 5.1 and when I watch a movie in 5.1 do not hear the dialogue.

aplay -l  
> 
**** Lista PLAYBACK urz&#261;dze&#324; **** 
karta 0: PCH [HDA Intel PCH], urz&#261;dzenie 0: ALC887-VD Analog [ALC887-VD Analog] 
  Urz&#261;dzenia podrz&#281;dne: 1/1 
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0 
karta 0: PCH [HDA Intel PCH], urz&#261;dzenie 1: ALC887-VD Digital [ALC887-VD Digital] 
  Urz&#261;dzenia podrz&#281;dne: 1/1 
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0 
karta 0: PCH [HDA Intel PCH], urz&#261;dzenie 3: HDMI 0 [HDMI 0] 
  Urz&#261;dzenia podrz&#281;dne: 0/1 
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0 


aplay -L 
> 
default 
    Playback/recording through the PulseAudio sound server 
null 
    Discard all samples (playback) or generate zero samples (capture) 
pulse 
    PulseAudio Sound Server 
sysdefault:CARD=PCH 
    HDA Intel PCH, ALC887-VD Analog 
    Default Audio Device 
front:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    Front speakers 
surround40:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    4.0 Surround output to Front and Rear speakers 
surround41:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    4.1 Surround output to Front, Rear and Subwoofer speakers 
surround50:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    5.0 Surround output to Front, Center and Rear speakers 
surround51:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers 
surround71:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers 
iec958:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Digital 
    IEC958 (S/PDIF) Digital Audio Output 
hdmi:CARD=PCH,DEV=0 
    HDA Intel PCH, HDMI 0 
    HDMI Audio Output 
dmix:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    Direct sample mixing device 
dmix:CARD=PCH,DEV=1 
    HDA Intel PCH, ALC887-VD Digital 
    Direct sample mixing device 
dmix:CARD=PCH,DEV=3 
    HDA Intel PCH, HDMI 0 
    Direct sample mixing device 
dsnoop:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    Direct sample snooping device 
dsnoop:CARD=PCH,DEV=1 
    HDA Intel PCH, ALC887-VD Digital 
    Direct sample snooping device 
dsnoop:CARD=PCH,DEV=3 
    HDA Intel PCH, HDMI 0 
    Direct sample snooping device 
hw:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    Direct hardware device without any conversions 
hw:CARD=PCH,DEV=1 
    HDA Intel PCH, ALC887-VD Digital 
    Direct hardware device without any conversions 
hw:CARD=PCH,DEV=3 
    HDA Intel PCH, HDMI 0 
    Direct hardware device without any conversions 
plughw:CARD=PCH,DEV=0 
    HDA Intel PCH, ALC887-VD Analog 
    Hardware device with all software conversions 
plughw:CARD=PCH,DEV=1 
    HDA Intel PCH, ALC887-VD Digital 
    Hardware device with all software conversions 
plughw:CARD=PCH,DEV=3 
    HDA Intel PCH, HDMI 0 
    Hardware device with all software conversions 


Maybe somebody help me :)

---

