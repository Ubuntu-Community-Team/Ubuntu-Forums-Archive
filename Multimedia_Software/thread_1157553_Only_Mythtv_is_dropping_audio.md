---
title: "Only Mythtv is dropping audio"
date: 2009-05-12
forum: Multimedia Software
---

### Post by pfuller on 2009-05-12
I am running mythbuntu 9.04 everything is working but audio in mythtv. The audio in mplayer going though my spdif  while playing a recorded show. But when I play the same show through mythtv the audio cracks and drops. 

This is problem is really annoying any would would be appreated. 

OS: mythbuntu 9.04 2.6.28-11-generic #42-Ubuntu SMP x86_64 GNU/Linux



# aplay -l
```

**** List of PLAYBACK Hardware Devices ****
E: core-util.c: Home directory /home/paul not ours.
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```# aplay -L
```

E: core-util.c: Home directory /home/paul not ours.
front:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```/etc/asound.conf
```

# ~/.asoundrc or /etc/asound.conf    
# ALSA configuration file            

##### USAGE #####
# Save this file as "~/.asoundrc" (for user-specific sound configuration) or
# "/etc/asound.conf" (for system-wide sound configuration) and specify ALSA 
# device names ad described in the next section.                            


##### DEVICE NAMES #####
# This configuration file defines four devices for use by the user.  Those
# devices are "analog", "mixed-analog", "digital", and "mixed-digital".  The
# user may also re-define "default" to be identical to one of the above-named
# devices (i.e. to send all sound output to the digital output unless otherwise
# specified).  Use the device names as described below:                        
#  - "analog" outputs to the analog output directly and (at least on software  
#  sound cards) blocks other audio output.  After playback completes, "queued" 
#  sounds are output in sequence.                                              
#  - "mixed-analog" mixes audio output from multiple programs into the analog  
#  output (so you can hear beeps, alerts, and other noises while playing back  
#  an audio stream).                                                           
#  - "digital" outputs to the digital output directly.  Since most (all?)      
#  digital outputs expect 48kHz PCM audio, this may not work for some playback 
#  (i.e. CD's--which are 44.1kHz PCM audio--or 32kHz audio streams from TV     
#  recordings, etc.).                                                          
#  - "mixed-digital"                                                           

# All other devices created within this file are used only by the configuration
# file itself and should /not/ be used directly.  In other words, do not use   
# the devices "analog-hw", "dmix-analog", "digital-hw", or "dmix-digital".     


##### IMPORTANT #####
# To make this ALSA configuration file work with your sound card, you will need
# to define the appropriate card and device information for the "analog-hw" and
# "digital-hw" devices below.  You can find the card and device information    
# using "aplay -l".                                                            


##### Configuration File #####

# Override the default output used by ALSA.  If you do not override the
# default, your default device is identical to the (unmixed) "analog" device
# shown below.  If you prefer mixed and/or digital output, uncomment the    
# appropriate four lines below (only one slave.pcm line).                   
#                                                                           
# Note, also, that as of ALSA 1.0.9, "software" sound cards have been modified
# such that their default "default" device is identical to the "mixed-analog" 
# device.  Whether using an ALSA version before or after 1.0.9, it does no harm
# and has no affect on performance to redefine the device (even if the         
# redefinition does not change anything).  Also, by using this ALSA            
# configuration file, you once again have access to unmixed analog output using
# the "analog" device.                                                         
#pcm.!default {                                                                
#  type plug                                                                   
## Uncomment the following to use (unmixed) "analog" by default                
#  slave.pcm "analog-hw"                                                       
## Uncomment the following to use "mixed-analog" by default                    
#  slave.pcm "dmix-analog"                                                     
## Uncomment the following to use (unmixed) "digital" by default               
#  slave.pcm "digital-hw"                                                      
## Uncomment the following to use "mixed-digital" by default                   
#  slave.pcm "dmix-digital"                                                    
#}                                                                             

# Control device (mixer, etc.) for the card
ctl.!default {                             
  type hw                                  
  card 0                                   
}                                          

# Alias for (converted) analog output on the card
# - This is identical to the device named "default"--which always exists and
# refers to hw:0,0 (unless overridden)                                      
# - Therefore, we can specify "hw:0,0", "default", or "analog" to access analog
# output on the card                                                           
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine     
# "default" to do mixing, meaning this device is different from "default" and  
# allows playback while blocking other sound sources (until playback           
# completes).                                                                  
pcm.analog {                                                                   
  type plug                                                                    
  slave.pcm "analog-hw"                                                        
}                                                                              

# Control device (mixer, etc.) for the card
ctl.analog {                               
  type hw                                  
  card 0                                   
}                                          

# Alias for (converted) mixed analog output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the dmix plugin (in this case 48000Hz)                        
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine   
# "default" to do mixing, meaning this device is identical to "default" for  
# "software" sound cards.                                                    
pcm.mixed-analog {                                                           
  type plug                                                                  
  slave.pcm "dmix-analog"                                                    
}                                                                            

# Control device (mixer, etc.) for the card
ctl.mixed-analog {                         
  type hw                                  
  card 0                                   
}                                          

# Alias for (converted) digital (S/PDIF) output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the S/PDIF hardware (in this case 48000Hz)                    
pcm.digital {                                                                
  type plug                                                                  
  slave.pcm "digital-hw"                                                     
}                                                                            

# Control device (mixer, etc.) for the card
ctl.digital {                              
  type hw                                  
  card 0                                   
}                                          

# Alias for mixed (converted) digital (S/PDIF) output on the card
#  - This will accept audio input--regardless of rate--and convert to the rate
#  required for the S/PDIF hardware (in this case 48000Hz)                    
pcm.mixed-digital {                                                           
  type plug                                                                   
  slave.pcm "dmix-digital"                                                    
}                                                                             

# Control device (mixer, etc.) for the card
ctl.mixed-digital {                        
  type hw                                  
  card 0                                   
}                                          

# The following devices are not useful by themselves.  They require specific
# rates, channels, and formats.  Therefore, you probably do not want to use 
# them directly.  Instead use of of the devices defined above.              

# Alias for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.analog-hw {                                                            
  type hw                                                                  
  card 0                                                                   
  # The default value for device is 0, so no need to specify               
#  - Uncomment one of the below or create a new "device N" line as appropriate
#    for your sound card or                                                   
#  device 1                                                                   
#  device 4                                                                   
}                                                                             

# Control device (mixer, etc.) for the card
ctl.analog-hw {                            
  type hw                                  
  card 0                                   
}                                          

# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {                                                           
  type hw                                                                  
  card 0                                                                   
  device 1                                                                 
#  - Comment out "device 1" above and uncomment one of the below or create a
#    new "device N" line as appropriate for your sound card or              
#  device 2                                                                 
#  device 4                                                                 
}                                                                           

# Control device (mixer, etc.) for the card
ctl.digital-hw {                           
  type hw                                  
  card 0                                   
}                                          

# Direct software mixing plugin for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-analog {                                                          
  type dmix                                                                
  ipc_key 1234                                                             
  slave {                                                                  
    pcm "analog-hw"                                                        
    period_time 0                                                          
    period_size 1024                                                       
    buffer_size 4096                                                       
    rate 48000                                                             
  }                                                                        
}                                                                          

# Control device (mixer, etc.) for the card
ctl.dmix-analog {                          
  type hw                                  
  card 0                                   
}                                          

# Direct software mixing plugin for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-digital {                                                         
  type dmix                                                                
  ipc_key 1235                                                             
  slave {                                                                  
    pcm "digital-hw"                                                       
    period_time 0                                                          
    period_size 1024                                                       
    buffer_size 4096                                                       
    rate 48000                                                             
  }                                                                        
}                                                                          

# Control device (mixer, etc.) for the card
ctl.dmix-digital {                         
  type hw                                  
  card 0                                   
}                                          


pcm.!default {
type plug     
slave {       
pcm multi     
rate 48000    
}             
ttable.0.0 1.0
ttable.1.1 1.0
ttable.0.2 1.0
ttable.1.3 1.0
}             

pcm.stereo {
type plug   
slave {     
pcm multi   
rate 48000  
}           
ttable.0.0 1.0
ttable.1.1 1.0
ttable.0.2 1.0
ttable.1.3 1.0
}

ctl.stereo {
type hw
card 0
}

pcm.multi {
type multi
slaves.a.pcm "analog-hw"
slaves.a.channels 2
slaves.b.pcm "digital-hw"
slaves.b.channels 2
bindings.0.slave a
bindings.0.channel 0
bindings.1.slave a
bindings.1.channel 1
bindings.2.slave b
bindings.2.channel 0
bindings.3.slave b
bindings.3.channel 1
}

ctl.multi {
type hw
card 0
}

```/var/log/mythtv/mythfrontend.log
```

2009-05-12 19:00:43.911 TV: Attempting to change from None to WatchingPreRecorded    
2009-05-12 19:00:43.916 DPMS Deactivated                                             
2009-05-12 19:00:44.106 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".                             
2009-05-12 19:00:44.107 AFD: Opened codec 0xa379e0, id(MPEG2VIDEO) type(Video)                      
2009-05-12 19:00:44.107 AFD: codec AC3 has 6 channels                                               
2009-05-12 19:00:44.107 AFD: Opened codec 0x104f560, id(AC3) type(Audio)                            
2009-05-12 19:00:44.107 AFD: codec AC3 has 2 channels                                               
2009-05-12 19:00:44.108 AFD: Opened codec 0xf82840, id(AC3) type(Audio)                             
2009-05-12 19:00:44.109 Opening audio device 'mixed-digital'. ch 2(2) sr 48000                      
2009-05-12 19:00:44.109 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.                           
2009-05-12 19:00:44.125 Opening audio device 'mixed-digital'. ch 2(2) sr 48000                      
2009-05-12 19:00:44.125 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.                           
2009-05-12 19:00:44.150 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.            
                        codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-05-12 19:00:44.151 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'                           
2009-05-12 19:00:44.259 OSD Theme Dimensions W: 640 H: 480                                                 
2009-05-12 19:00:44.398 TV: Changing from None to WatchingPreRecorded                                      
2009-05-12 19:00:44.398 Realtime priority would require SUID as root.                                      
2009-05-12 19:00:44.500 Video timing method: USleep with busy wait                                         
2009-05-12 19:00:44.555 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.563 AFD: Opened codec 0x87a6750, id(MPEG2VIDEO) type(Video)                            
2009-05-12 19:00:44.563 AFD: codec AC3 has 6 channels                                                      
2009-05-12 19:00:44.563 AFD: Opened codec 0x87a6dd0, id(AC3) type(Audio)                                   
2009-05-12 19:00:44.563 AFD: codec AC3 has 2 channels                                                      
2009-05-12 19:00:44.564 AFD: Opened codec 0x87a7450, id(AC3) type(Audio)                                   
2009-05-12 19:00:44.597 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.653 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.689 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.740 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.796 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.827 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.858 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.888 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.919 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.949 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.955 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:44.985 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:45.016 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:45.046 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:45.079 AO: dropping back audio_buffer_unused                                              
2009-05-12 19:00:45.125 Marking recording as unwatched                                                     
2009-05-12 19:00:45.125 TV: Attempting to change from WatchingPreRecorded to None                          
2009-05-12 19:00:45.228 TV: Changing from WatchingPreRecorded to None                                      
2009-05-12 19:00:45.354 DPMS Reactivated.                                                                  
2009-05-12 19:00:46.072 AFD: Opened codec 0x948daa0, id(MPEG2VIDEO) type(Video)                            
2009-05-12 19:00:46.072 AFD: codec AC3 has 6 channels                                                      
2009-05-12 19:00:46.072 AFD: Opened codec 0xa36860, id(AC3) type(Audio)                                    
2009-05-12 19:00:46.072 AFD: codec AC3 has 2 channels                                                      
2009-05-12 19:00:46.073 AFD: Opened codec 0xff62e0, id(AC3) type(Audio)                                    
2009-05-12 19:00:47.003 AFD: Opened codec 0x105cab0, id(MPEG2VIDEO) type(Video)                            
2009-05-12 19:00:47.003 AFD: codec AC3 has 6 channels                                                      
2009-05-12 19:00:47.004 AFD: Opened codec 0x105a950, id(AC3) type(Audio)                                   
2009-05-12 19:00:47.005 AFD: codec AC3 has 2 channels                                                      
2009-05-12 19:00:47.006 AFD: Opened codec 0x8b082d0, id(AC3) type(Audio)                                   
2009-05-12 19:00:48.661 AFD: Opened codec 0x7fd622a8af20, id(MPEG2VIDEO) type(Video)                       
2009-05-12 19:00:48.661 AFD: codec MP2 has 2 channels                                                      
2009-05-12 19:00:48.661 AFD: Opened codec 0x7fd622a18980, id(MP2) type(Audio)                              
2009-05-12 19:00:49.516 AFD: Opened codec 0x7fd622a83a80, id(MPEG2VIDEO) type(Video)                       
2009-05-12 19:00:49.516 AFD: codec AC3 has 6 channels                                                      
2009-05-12 19:00:49.518 AFD: Opened codec 0x7fd622a878a0, id(AC3) type(Audio)                              
2009-05-12 19:00:49.518 AFD: codec AC3 has 2 channels                                                      
2009-05-12 19:00:49.519 AFD: Opened codec 0x7fd622a8af20, id(AC3) type(Audio)        

```

---

### Post by nwwoods on 2009-05-23
I have this same problem, no resolution. please advise if you find something.

I can play recordings made with MythTV with MPlayer, Xine or VLC just fine, but if I try to play them inside MythTV, all I get is crackling audio.

It would seem it's one of the settings in MythTV | General | sound-page but I've tried them all and either get crackle or nothing.  

Is there anyone out there reading these forums who has any ideas?

---

### Post by pfuller on 2009-05-24
looks like this is similar post:  [http://ubuntuforums.org/showthread.php?t=346027](http://ubuntuforums.org/showthread.php?t=346027)

Also I am getting these errors now: 

mplayer -fs -zoom -quiet -vo xv -aspect 16:9 -ao alsa:device=hw=0.1 -afm hwac3,hwdts -srate 48000 
```

Forced audio codec: mad
Trying to force audio codec driver family hwac3...
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 640000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
[AO_ALSA] alsa-lib: conf.c:3843:(parse_args) Unknown parameter AES0
[AO_ALSA] alsa-lib: conf.c:3969:(snd_config_expand) Parse arguments error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM hw:0,1,AES0=6
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)


```

---

### Post by pfuller on 2009-05-25
I got the Cracking to stop by going to:

Utilities/Setup --> Setup --> TV Settings --> Playback

In here uncheck: 

[LIST]
[*]Extra Audio Buffering
[*]Use video as timebase
[/LIST]

Utilities/Setup --> Setup -->General

Change Audio output device: ALSA:mythspdif
Passthrough output device: ALSA:iec958:{AES0 0x02}

Check:
Enable AC3 to SPDIF passthrough
Enable DTS to SPDIF passthrough


Added this to my /etc/asound.conf

```

pcm.!default {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}

pcm.mythspdif {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}


```
If that does not work try:

sudo apt-get update
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

reboot or reload alsa modules.

From: 
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://lists.ubuntu.com/archives/kubuntu-users/2008-December/036769.html](https://lists.ubuntu.com/archives/kubuntu-users/2008-December/036769.html)

---

### Post by nwwoods on 2009-06-06
Thank you PFuller.

I tried all of the suggested steps --
- checking/verifying the settings in Setup | General
- checking/verifying the settings in Setup | Playback
- downloading, rebuilding and reloading the ALSA packages

Since the sound only crackles inside MythTV I wasn't sure why the last step, which is a pretty big club, was appropriate, but I did it anyway.

Result: no difference.

I have narrowed the issue to playback of MPEG2 from inside MythTV.  THat's it.  Unfortunately, live TV, DVD's and recorded TV are all MPEG2.

Playback is fine for other formats, and for MPEG2 outside of MythTV with players like VLC.  But inside MythTV....crackle crackle crackle

I have reinstalled all ffmpeg related packages.  No diff.  I have checked, re-checked and triple checked all the mixer settings in the umpteen different mixer programs.  All is well.

Quite perplexing.

---

### Post by pfuller on 2009-06-06
So, the rebuilding the alsa modules did not work for you? 



```

sudo apt-get update
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```

What type of spdif are you using(Coax/TOC/HDMI)?
What do you have in your asound.conf?

---

### Post by nwwoods on 2009-06-06
Wow, thanks for the quick reply!  Correct, rebuilding did not work (i.e., there was no change in observed results after rebuilding).

There was no asound.conf in /etc, so all that got put in it is what you suggested.  I came across a wiki on setting up digital sound on the mythtv.org site, and it suggested adding:
<code>
pcm.!default {
  type hw
  card 0
  device 1
}
ctl.!default {
  type hw
  card 0
  device 1
}
</code>
So I did.  That didn't help either.

THe guide on the mythtv wiki suggests trying to play some simple files directly with the aplay utility, and I am trying to do that and finding that no matter what format I specify, it results in an error saying "format non available".

I have both optical and coax digital connectors on the Asus P5E mobo that I have, both are connected to the receiver, and both work, outside of MythTV, except now, I am seeing aplay not being happy.  (but Mplayer, VLC, etc work just fine).

---

### Post by pfuller on 2009-06-06
Send me the results of:
```

aplay -l
aplay -L

```

Also what kind of tuners do you have? 

Can you use mplayer or vlc to play your mythtv recorded files?

Does your receiver show the digital link when trying to play in mythtv?

---

### Post by nwwoods on 2009-06-06
Sorry for delayed response.  Yard work.

aplay -l output
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

aplay -L output
```
default:CARD=Intel
    HDA Intel, AD198x Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

One tuner, Hauppauge HVR-1250, OTA only (no cable, no satellite)
Mixed results with standalone players.
VLC works fine.  
Movie Player sometimes yes, sometimes no.  I haven't been able to get it consistent.
MPlayer gives me a AO pulse connection refused error, but sometimes will still produce some audio.  Lately it is not.

When I was getting crackly sound on playback, I had the 5.1 indicators lit on the received.  Now, no matter what combination of setting I try, I get no sound at all, and no indication on the receiver.

The recordings themselves are fine.  They play fine in certain standalone players.  But no sound when playing in MythTV.
Yes, MPlayer and VLC play MythTV recorded files just fine, in DD 5.1 or whatever.

---

### Post by pfuller on 2009-06-06
This should not matter but something to try this. I realized that I had a typo earlier posts.  

Append this to the bottom of /etc/asound.conf
```

pcm.mythspdif {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}

```

Utilities/Setup --> Setup --> TV Settings --> Playback

In here uncheck: 

[LIST]
[*]Extra Audio Buffering
[*]Use video as timebase
[/LIST]

Utilities/Setup --> Setup -->General

Change Audio output device: ALSA:mythspdif
Passthrough output device: ALSA:iec958:{AES0 0x02}

Check:
Enable AC3 to SPDIF passthrough
Enable DTS to SPDIF passthrough



This is what i used for my mplayer:
```

mplayer -fs -zoom -quiet -vo xv -aspect 16:9 -ao alsa:device=spdif  -afm hwac3,hwdts -srate 48000

```

For some reason I have trouble playing DTS and still have not figured it out yet.

---

### Post by nwwoods on 2009-06-06
THank you.  I had already made the setup changes but checked anyway.  I stole your asound.conf from the earlier post and added the extra config at the end.  Still no audio in MythTV but another problem got better, which is that whenever I was on Live TV, and pressed Esc on the keyboard to get back to the main menu, it was just blowing all the way out to the desktop.  With the asound.conf in place, it returns to the main menu like it should.  So there must be an unhandled exception somewhere that kills the MythTV process when the asound.conf is not present?  Weird.  I thought contemporary applications weren't supposed to depend on asound.conf?

So there is apparently something funky with asound.conf on my system.  I remain perplexed that I didn't get an asound.conf on install.  I think I need to just reinstall from scratch.  I started but there doesn't seem to be any way to not reformat the disk volume(!) and I'd rather not lose all the shows that have been recorded during the last three weeks I've been fiddling with this sound issue.

Any way to just re-run the sound portion of the installer?  Or to run the installer on an existing installation and not blow it completely away?  Whatever happened to the upgrade scenario?

---

### Post by pfuller on 2009-06-07
I know that most applications are wanting to get a way for asound.conf but it seems like mythtv still depends on it. 

The apt-get commands I had you run earlier was to rebuild the alsa modules. 

If you use the standard partitioning then no, but if you use your own custom partitioning with recordings and your other data files on another drive or partition then you can format the all the other partition and not your data. 

For upgrade it just upgrades you .deb packages and sources.list to pull the new packages. 

Your best bet is to follow the "23.7 Moving your data to new hardware" and reinstall the OS:** **

[http://www.mythtv.org/docs/mythtv-HOWTO-23.html](http://www.mythtv.org/docs/mythtv-HOWTO-23.html)


This will allows you to backup your recordings directory and that database to restore them after you do a reinstall.

---

### Post by nwwoods on 2009-06-07
I took the default asound.conf from the mythtv wiki page on configuring digital audio, changed the default line in the pcm.!default section  to dmix-digital instead of analog-hw, added the section on the end that they say to add (and which you have in yours), and now I get audio on live TV and on recordings.  I notice I can comment all of them out (as you have in yours, so there is no default) and that also works, curiously.

If I put in the added 10 or so lines from the very end of your asound.conf, the crackly sounds return.

Oddly, now I don't get any audio when using any of the standalone players.  I haven't looked at it much but I have a hunch it means the settings on the mythtv wiki addendum to combine analog and digital outputs (which is in your asound.conf also) aren't quite right for my system.  Will have to look further.

One other issue.  The audio on HD live TV and HD recordings is intermittent.  It plays about 50% of the time, about 1/2 a second on, 1/2 a second off.  I can watch the indicators on my receiver blinking on and off with it.  Suggests some sort of bitrate sync issue?  Audio on non-HD recordings and non-HD live TV (digital-only OTA tuner remember) is fine.  

And the Esc key blowing me right back out to Xfce problem has returned, suggesting I suppose that asound.conf is still not quite there.

But at least *something* is working.

---

### Post by pfuller on 2009-06-07
My Mythtv is acting up now to the same as yours and I still don't know what wrong, Thinks seem to play better with mplayer but that too is having issues.

---

### Post by Dragonflyoh on 2009-06-14
> **pfuller said:**
> This should not matter but something to try this. I realized that I had a typo earlier posts.  

Append this to the bottom of /etc/asound.conf
```

pcm.mythspdif {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}

```

Utilities/Setup --> Setup --> TV Settings --> Playback

In here uncheck: 

[LIST]
[*]Extra Audio Buffering
[*]Use video as timebase
[/LIST]

Utilities/Setup --> Setup -->General

Change Audio output device: ALSA:mythspdif
Passthrough output device: ALSA:iec958:{AES0 0x02}

Check:
Enable AC3 to SPDIF passthrough
Enable DTS to SPDIF passthrough



This is what i used for my mplayer:
```

mplayer -fs -zoom -quiet -vo xv -aspect 16:9 -ao alsa:device=spdif  -afm hwac3,hwdts -srate 48000

```

For some reason I have trouble playing DTS and still have not figured it out yet.

Thanks for the information. I used part of the  mplayer "-fs -zoom -ao alsa:device=spdif" and it solved my problems with mp4 files.

---

### Post by nwwoods on 2009-06-14
I finally got some time to try this again.  I re-installed Mythbuntu Jaunty from scratch and am right back where I started -- crackly audio inside the frontend, normal audio anywhere else.  I put my saved asound.conf back, fixed the mixer settings, fixed the setup settings, it is still crackly.   Argh!

---

### Post by pauna on 2009-06-16
Would this information be of help: [http://www.gossamer-threads.com/lists/mythtv/users/384248]("http://www.gossamer-threads.com/lists/mythtv/users/384248")

My MythTV box sound works just fine (spdif -> 5.1 amplifier) but I don't have access to it right now.

---

