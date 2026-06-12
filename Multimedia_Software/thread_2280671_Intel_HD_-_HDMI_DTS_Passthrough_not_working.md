---
title: "Intel HD - HDMI DTS Passthrough not working"
date: 2015-06-01
forum: Multimedia Software
---

### Post by massa84 on 2015-06-01
Good afternoon forum.
I have some issue with my mediaserver and my new television.


My system is connected in this way :


**[PC]** ---(HDMI)---> **[TV]** ---(S/PDIF)---> **[SOUND SYSTEM]**


**Mediacenter spec:**
MOBO: Asus P8H77-I
CPU: Intel i3-3225
GPU: Integrated Intel HD 4000
RAM: 2x4gb generic ram
HDD: 5x WD Red 3TB
OS: Ubuntu


**OLD Television**
LG 47LA740s


**Audio System**
Logitech Z906 (hardware decoding of DTS and DolbyDigital)




In the past 1and half year I've run different version of ubuntu (13.10, 14.04 , 14.10) being able to passthrough both DolbyDigital and DTS without any issue using both VLC and KODI.
I just had to enable the optical digital output on the television and execute pavucontrol on the mediacenter to enable the passthrough of the digital formats for the HDMI audio output.




Recently i moved from Italy to London and I bought a new television while keeping my 'old' mediacenter and audio system.


**NEW Television**
LG 55UB850V (WebOs)


And now i'm not able to passthrough DTS from my mediacenter anymore ! 
If I try to reproduce a DTS track from any movie i have NO SOUND sent to the TV.

- Passthrough of Dolby Digital works perfectly ( !!!!!!!!!!!!!!!! ) .
- The television support DTS for sure.
- I enabled the optical output on the television and enabled the passthrough option and configured pavucontrol correctly
- If i disable the passthrough option on the television (so that the output are the speaker of the television) still have the same problem (DD works, DTS doesn't)
- The passthrough issue is the same on both VLC (any version) and KODI 14,15.
- If I connect the mediacenter directly to the sound system through S/PDIF (without HDMI passthrough), both DolbyDigital and DTS works perfectly
- Pulseaudio LOG doesn't show any issue at all.
- If i disable PulseAudio and use ALSA i have the same issue (DolbyDigital passthrough works , DTS doesn't)
- If I reproduce a movie with DTS audio directly on the television (from external HDD or DLNA) it works perfectly and the audio is correctly decoded by the sound system
- If I reproduce a movie from my windows notebook connected to the TV through the same HDMI it works perfectly and the audio is correctly decoded by the sound system
- I've updated the TV firmware to the latest version available
- I've tried different linux version (ubuntu 14.04, 14.10, 15.04, elementary OS 0.3)
- I've tried to update kernel to the latest version available (4.0.3) without improvements.
- I've tried to update ALSA to the latest version available without improvements.

I've tried using a laptop form a friend with a 4th generation intel cpu with integrated graphic card : intel HD 4400, and i had exactly the same issue ( DolbyDigital works, DTS doesn't), so i think it's an issue the impact all Intel HD GPUs

I think it may be some issue during the HDMI handshake between the TV and the GPU but i have no idea on how to fix or debug this issue.


I've run out of options, please help me.

Thank you very much, 
Marco.

---

### Post by massa84 on 2015-06-01
alsa-info.sh output : [http://www.alsa-project.org/db/?f=2da3cf76e0772fa10c601db39c7c4752df2b7e7c](http://www.alsa-project.org/db/?f=2da3cf76e0772fa10c601db39c7c4752df2b7e7c)

cat /proc/asound/card0/eld#3.0 
```
monitor_present        1
eld_valid        1
monitor_name        LG TV
connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0x6d1e
product_id        0x1
port_id            0x0
support_hdcp        0
support_ai        1
audio_sync_delay    0
speakers        [0xffff] FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
sad_count        3
sad0_coding_type    [0x7] DTS
sad0_channels        6
sad0_rates        [0xc0] 44100 48000
sad0_max_bitrate    1536000
sad1_coding_type    [0x2] AC-3
sad1_channels        6
sad1_rates        [0xe0] 32000 44100 48000
sad1_max_bitrate    640000
sad2_coding_type    [0x1] LPCM
sad2_channels        2
sad2_rates        [0x14e0] 32000 44100 48000 96000 192000
sad2_bits        [0xe0000] 16 20 24
```

---

