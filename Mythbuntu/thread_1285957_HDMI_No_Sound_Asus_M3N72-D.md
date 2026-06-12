---
title: "HDMI No Sound Asus M3N72-D"
date: 2009-10-08
forum: Mythbuntu
---

### Post by cleatus99 on 2009-10-08
Asus M3N72-D SLI Barebone Kit - nForce 750a, AMD Phenom II X4 940 Black Edition, 4GB OCZ SLI DDR2-800, 750GB HDD, Ultra Case, 650W PSU

Ok so I got a Tiger Direct barebones Kit. To run Mythbuntu 9.04

I have 8.10 running on another 570SLI based system, so I thought this would be an easy nextgen myth box.

I can not figure out how to get the HDMI sound to work and play nice with Ubuntu.

I've read thread after thread, still not getting the noob fix.
```

# lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075d (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:08.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:08.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:08.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:08.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:0a.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 VGA compatible controller: nVidia Corporation nForce 750a SLI (rev a2)

```
```

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I can't play Sound through mythtv or through desktop VLC XINE etc. and in work on HDMI, it does work on back analog connections.

```

# speaker-test -c2 -twav -Dplughw:0,3

speaker-test 1.0.18

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 2.731535

```
However I run this and it plays the "Front Left" and "Front Right" Sound through TV HDMI.
I am running NVIDIA 180 Drivers, Video looks great, just can't get sound to work.

I've turned on the IEC958, IEC958 D, IEC958 1 in alsamixer.
```

#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

```

```

# cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio capture
  5: [ 1]   : control
  6: [ 0- 3]: digital audio playback
  7: [ 0- 2]: digital audio capture
  8: [ 0- 1]: digital audio playback
  9: [ 0- 1]: digital audio capture
 10: [ 0- 0]: digital audio playback
 11: [ 0- 0]: digital audio capture
 12: [ 0]   : control

```

```

# lsmod | grep snd_hda_intel
snd_hda_intel         559028  1
snd_pcm                99464  3 snd_hda_intel,cx88_alsa,snd_pcm_oss
snd                    78920  14 snd_hda_intel,cx88_alsa,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

```

```

# uname -a
Linux MYTHTV 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

```

---

### Post by cleatus99 on 2009-10-28
Still no progress made, have everything else up & running, but still not able to direct sound out HDMI, except for the test script.

---

### Post by swebley on 2009-10-28
I have a gigabyte board with similar hardware and had to umute the hdmi port for sound to work properly.

1: start alsamixer as a regular
2: look for IEC954 1 (or similiar. I enabled them all)
3: enable it by press m (if it is muted)
4: i also turned up all the volumes
5: give it another crack

I did the above as the standard user and it seems to remember the settings after a reboot. 

Further I setup my .asoundrc to give me HDMI out volume control and a bit of a sound level boost (it was very quite). Here is my .asoundrc. Notice the Max_DB this will boost the volume level but be careful with the number here it can get VERY loud.


```

# Jon B's ASound.Conf file for HDMI Audio on MythTV
# HDMI configuration with volume control for MythTV
# For ALSA 1.0.19  - 1/31/2009

# Instructions for use
# 1) Find your hmdi hardware Card Number and Device Number.  Open a terminal and do:  
#    aplay -L
#    That will list all of the hardware audio devices.  Look for the one labeled HDMI.
#    Note what Card Number and Device Number it lists (they seem to be card 0,
#    device 3 but your system may be different).
# 2) Edit the pcm.hdmi_hw device defined here to set your Card Number and Device Number.
# 3) Put this file in either /etc/asound.conf or in your home directory as .asoundrc.
#    sudo cp deweys_asound.conf.txt /etc/asound.conf
#      or 
#    sudo cp deweys_asound.conf.txt $HOME/.asound.conf
# 4) Exit mythfrontend.  Then restart the sound system:
#    sudo /etc/init.d/alsa-utils restart
# 5) Start mythfrontend and go to the audio setup screen
#    "Utilities / Setup"  then "Setup" then "General" then "Next" until you
#    get to the Audio tab.
# 6) Fill in the info - it's case sensitive:
#    Audio output device: ALSA:hdmi_complete     <--- note you have to type in this field
#    Passthrough output devide: Default
#     ... Stereo... ... Passive...
#    Mixer Device: ALSA:default
#    Mixer controls: hdmi_volume                 <--- type in this field
# 7) Work your way back to Watch TV and give it a try.


pcm.!default {
  type plug
  slave.pcm "hdmi_complete"
}

pcm.hdmi_hw {
  type hw
  card 0     #  <-----  Put your card number here
  device 3   #  <-----  Put your device number here
}

pcm.hdmi_formatted {
  type plug
  slave {
    pcm hdmi_hw
    rate 48000
    channels 2
  }
}

pcm.hdmi_complete {
  type softvol
  slave.pcm hdmi_formatted
  control.name "PCM"
  control.card 0
  max_dB 15.0
}


```This is not ideal if you are going through an external amp as it only provides 2 channel. I output digital via the onboard digital out and HDMI video and sound direct to my TV. This gives me one remote for TV but also DVD movie sound through my amp (with a few more tweaks). The .asoundrc will also provide volume control via PCM so use default sound device, default mixer with PCM and adjust the Max_DB value to set MAX volume level.


Hope this helps...

---

### Post by cleatus99 on 2009-10-28
FANTASTIC and thanks, it works....

YEAH!!!!!!!!

---

### Post by Dewey_Oxberger on 2009-10-28
Whoa, old version of my asound.conf there.  Here is my current version.  When you download it name it "deweys_asound.conf" and have a look inside the file "less deweys_asound.conf".  Follow the directions in the file.

This version gives a volume control for audio over hdmi.  In general I set my TV volume to the max sound I want to hear then I use the mythtv volume control to turn the volume up or down.

This version also sets the default audio device to be the hdmi so music player works.

---

### Post by sawbuck on 2009-11-23
Hope folks are still reading this thread...
  
As usual, let me preface this with the reality that I'm still new at this.  I'm running this as a F.E. with mythbuntu 9.10 added to Ubunu 9.10.

I'm having a problem with total silence connected to my 40" Toshiba 1080P LCD TV.  Awesome picture but I cant lip read etc.  I followed "Jon B.'s" instructions in this thread in the message prior to this reply.  But still get no sound.  (The system and Windows 7 on a separate disk that does get sound and video in HDMI so the the TV checks out)

Here's the results of "aplay -L" in a terminal window:

```
frank@Frank6:~$ aplay -L
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
pulse
    Playback/recording through the PulseAudio sound server

```


As you can see, my hdmi card is "NVidia" and not a number so that's what I put in the "asound.conf" file.  Here's that:


```
# Dewey Oxberger (aka Jon B)
# ASound.Conf file for HDMI Audio on MythTV
# HDMI configuration with volume control for MythTV
# Works in Ubuntu 9.04  5/9/2009

# Instructions for use
# 1) Find your hmdi hardware Card Number and Device Number.  Open a terminal and do:  
#    aplay -L
#    That will list all of the hardware audio devices.  Look for the one labeled HDMI.
#    Note what Card Number and Device Number it lists (they seem to be card 0,
#    device 3 but your system may be different).
# 2) Edit the pcm.hdmi_hw device defined here to set your Card Number and Device Number.
# 3) Put this file in either /etc/asound.conf or in your home directory as .asoundrc.
#    sudo cp deweys_asound.conf /etc/asound.conf
#      or 
#    sudo cp deweys_asound.conf $HOME/.asound.conf
# 4) Exit mythfrontend.  Then restart the sound system:
#    sudo /etc/init.d/alsa-utils restart
# 5) Start mythfrontend and go to the audio setup screen
#    "Utilities / Setup"  then "Setup" then "General" then "Next" until you
#    get to the Audio tab.
# 6) Fill in the info - it's case sensitive:
#    Audio output device: ALSA:hdmi_complete     <--- note you have to type in this field
#    Passthrough output devide: Default
#     ... Stereo... ... Passive...
#    Mixer Device: ALSA:default
#    Mixer controls: hdmi_volume                 <--- type in this field
# 7) Work your way back to Watch TV and give it a try.

pcm.hdmi_hw {
  type hw
  card NVidia     #  <-----  Put your card number here
  device 0   #  <-----  Put your device number here
}

pcm.hdmi_formatted {
  type plug
  slave {
    pcm hdmi_hw
    rate 48000
    channels 2
  }
}

pcm.hdmi_complete {
  type softvol
  slave.pcm hdmi_formatted
  control.name hdmi_volume
  control.card 0
}

#pcm.hdmi_complete {
#  type copy
#  slave.pcm hdmi_volume
#  slave {
#    pcm front
#  }
#}

pcm.!default hdmi_complete

```


The audio related messges from the frontend log  (below)  leads me to believe this "fix" may not be entered correctly as specified   ( NVidia needs to be a number??)   or it doesn't work with 9.10....:

```
2009-11-22 23:57:23.701 AFD: codec AC3 has 6 channels
2009-11-22 23:57:23.702 AFD: Opened codec 0x5e65a80, id(AC3) type(Audio)
2009-11-22 23:57:23.708 Opening audio device 'hdmi_complete'. ch 2(2) sr 48000
2009-11-22 23:57:23.708 Opening ALSA audio device 'hdmi_complete'.
2009-11-22 23:57:23.952 mixer unable to find control Master 1
2009-11-22 23:57:23.957 Opening audio device 'hdmi_complete'. ch 2(2) sr 48000
2009-11-22 23:57:23.957 Opening ALSA audio device 'hdmi_complete'.
2009-11-22 23:57:24.196 mixer unable to find control Master 1
2009-11-22 23:57:24.771 VidOutVDPAU Error: Failed to initialise VDPAU
2009-11-22 23:57:24.828 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
            codec 'MPEG2' makes 'xv-blit,xshm,xlib,' available, using 'xv-blit' instead.
2009-11-22 23:57:24.831 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-11-22 23:57:24.932 OSD Theme Dimensions W: 1280 H: 720
2009-11-22 23:57:25.566 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2009-11-22 23:57:25.567 TV: Changing from None to Watching WatchingPreRecorded
2009-11-22 23:57:25.567 New DB connection, total: 3
2009-11-22 23:57:25.569 Realtime priority would require SUID as root.
2009-11-22 23:57:25.570 Connected to database 'mythconverg' at host: 192.168.1.100
2009-11-22 23:57:25.579 Video timing method: USleep with busy wait
2009-11-22 23:57:25.597 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-22 23:59:52.503 TV: Attempting to change from Watching WatchingPreRecorded to None
2009-11-22 23:59:52.566 TV: Changing from Watching WatchingPreRecorded to None
```



It's getting late so I'll have to explore more next time.....

---

### Post by Dewey_Oxberger on 2009-11-23
> **sawbuck said:**
> ...I'm running this as a F.E. with mythbuntu 9.10 added to Ubunu 9.10.

Here's the results of "aplay -L" in a terminal window:

```
frank@Frank6:~$ aplay -L
front:CARD=NVidia,DEV=0
...
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```

As you can see, my hdmi card is "NVidia" and not a number so that's what I put in the "asound.conf" file.

The audio related messges from the frontend log  (below)  leads me to believe this "fix" may not be entered correctly as specified   ( NVidia needs to be a number??)   or it doesn't work with 9.10....:

```
2009-11-22 23:57:23.701 AFD: codec AC3 has 6 channels
2009-11-22 23:57:23.702 AFD: Opened codec 0x5e65a80, id(AC3) type(Audio)
2009-11-22 23:57:23.708 Opening audio device 'hdmi_complete'. ch 2(2) sr 48000
2009-11-22 23:57:23.708 Opening ALSA audio device 'hdmi_complete'.
2009-11-22 23:57:23.952 mixer unable to find control Master 1
2009-11-22 23:57:23.957 Opening audio device 'hdmi_complete'. ch 2(2) sr 48000
2009-11-22 23:57:23.957 Opening ALSA audio device 'hdmi_complete'.
2009-11-22 23:57:24.196 mixer unable to find control Master 1
2009-11-22 23:57:24.771 VidOutVDPAU Error: Failed to initialise VDPAU
2009-11-22 23:57:24.828 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
            codec 'MPEG2' makes 'xv-blit,xshm,xlib,' available, using 'xv-blit' instead.
2009-11-22 23:57:24.831 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-11-22 23:57:24.932 OSD Theme Dimensions W: 1280 H: 720
2009-11-22 23:57:25.566 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2009-11-22 23:57:25.567 TV: Changing from None to Watching WatchingPreRecorded
2009-11-22 23:57:25.567 New DB connection, total: 3
2009-11-22 23:57:25.569 Realtime priority would require SUID as root.
2009-11-22 23:57:25.570 Connected to database 'mythconverg' at host: 192.168.1.100
2009-11-22 23:57:25.579 Video timing method: USleep with busy wait
2009-11-22 23:57:25.597 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-22 23:59:52.503 TV: Attempting to change from Watching WatchingPreRecorded to None
2009-11-22 23:59:52.566 TV: Changing from Watching WatchingPreRecorded to None
```



It's getting late so I'll have to explore more next time.....

Hmmmm, You installed the myth packages over a stock 9.10 install?

I thought 9.10 used PulseAudio, not ALSA.  The aplay -L has some pulse audio stuff that scares me.

The dev and card need to be numbers (as far as I can recall).

It works in mythbuntu 9.10 (no pulse audio).  If you run aplay to test a sound sample what do you get?

---

### Post by cleatus99 on 2009-12-18
I did finnaly get it working, through the MythTv frontend setup.

This was after upgrading to newest mythbuntu Repos Builds .22 And Latest Kernel.

---

### Post by ginjaninjaa on 2010-01-06
works perfectly on my 8200 thank a mill

---

### Post by jaakan on 2010-05-16
This helped me big time and here is my current version below 


HDMI Video/Audio are both supported out of the box on Ubuntu 10.04 x64 for my Motherboard is Intel DG43GT ( Intel X4500/G43 )

```

# /home/username/.asoundrc

pcm.hdmi_hw {
  type hw
  card 0     #  <-----  Put your card number here
  device 3   #  <-----  Put your device number here
}

pcm.hdmi_formatted {
  type plug
  slave {
    pcm hdmi_hw
    rate 48000 # or "rate 96000" or "rate 192000" 
    channels 6 # or "channels 2"
  }
}

pcm.hdmi_complete {
  type softvol
  slave.pcm hdmi_formatted
  control.name hdmi_volume
  control.card 0
}

pcm.!default hdmi_complete

```

---

