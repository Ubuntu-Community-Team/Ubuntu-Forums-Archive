---
title: "DVD Audio Playback Issue"
date: 2009-10-27
forum: Mythbuntu
---

### Post by drumz on 2009-10-27
I'm using MythBuntu and it's working great - I'm able to use it as a front end to a remote backend and play my recordings with no problem (over HDMI too).

The issue I'm experiencing is I can't get audio to work playing back a DVD (player is built-in to my frontend box).

I've followed the how-tos/postings and audio over HDMI is working perfectly for my records, but with DVD playback I either get _no_ audio at all (perfect silence) or it sounds like a fast, non-stop stream of chirps.

If I set the 'Passthrough Output device' to 'ALSA:iec958:{AESO OxO2} I get no sound at all on dvd playback.  the following is what appears in the logs:

```
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4      
2009-10-27 18:16:07.485 Opened DVD device at /dev/dvdrw1                          
2009-10-27 18:16:07.638 There are 37 titles on the disk                           
2009-10-27 18:16:07.638 Title 0 has 0 parts.                                      
....    
2009-10-27 18:16:07.639 Title 36 has 2 parts.                                     
2009-10-27 18:16:07.735 DPMS Deactivated                                          
2009-10-27 18:16:09.352 AFD: Opened codec 0x89530b0, id(MPEG2VIDEO) type(Video)   
2009-10-27 18:16:09.352 NVP: Disabling Audio, params(-1,-1,-1)                    
2009-10-27 18:16:09.405 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'  
2009-10-27 18:16:09.441 OSD Theme Dimensions W: 640 H: 480                        
2009-10-27 18:16:09.894 TV: Changing from None to WatchingPreRecorded             
2009-10-27 18:16:09.895 New DB connection, total: 3                               
2009-10-27 18:16:09.896 Connected to database 'mythconverg' at host: 192.168.1.12 
2009-10-27 18:16:09.998 Video timing method: USleep with busy wait                
2009-10-27 18:16:10.038 DPMS Reactivated.                                         
2009-10-27 18:16:10.138 DPMS Deactivated                                          
2009-10-27 18:16:10.143 AFD: Warning, video codec 0x89530b0 id(MPEG2VIDEO) type (Video) already open.
2009-10-27 18:16:10.238 DPMS Reactivated.                                                            
2009-10-27 18:16:10.246 AFD: codec AC3 has 0 channels                                                
2009-10-27 18:16:10.247 AFD: Opened codec 0x99ac3c0, id(AC3) type(Audio)                             
2009-10-27 18:16:10.250 Opening audio device 'default'. ch 2(2) sr 48000                             
2009-10-27 18:16:10.250 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.                            
2009-10-27 18:16:10.293 AudioOutput Error: snd_pcm_open(iec958:{ AES0 0x02 }): No such file or directory
2009-10-27 18:16:10.293 NVP: Disabling Audio, reason is: snd_pcm_open(iec958:{ AES0 0x02 }): No such file or directory
2009-10-27 18:16:10.339 DPMS Deactivated                                                                              
2009-10-27 18:16:10.439 DPMS Reactivated.                                                                             
2009-10-27 18:16:10.439 DPMS Deactivated                                                                              
2009-10-27 18:16:10.439 DPMS Reactivated.                                                                             
2009-10-27 18:16:10.439 DPMS Deactivated                                                                              
2009-10-27 18:16:10.520 NVP: Disabling Audio, params(-1,-1,-1)                                                        
2009-10-27 18:16:10.612 AFD: Warning, video codec 0x89530b0 id(MPEG2VIDEO) type (Video) already open.                 
2009-10-27 18:16:10.700 AFD: codec AC3 has 0 channels                                                                 
2009-10-27 18:16:10.700 AFD: Opened codec 0x8beedf0, id(AC3) type(Audio)                                              
2009-10-27 18:16:10.702 Opening audio device 'default'. ch 2(2) sr 48000                                              
2009-10-27 18:16:10.702 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.                                             
2009-10-27 18:16:10.703 AudioOutput Error: snd_pcm_open(iec958:{ AES0 0x02 }): No such file or directory              
2009-10-27 18:16:10.703 NVP: Disabling Audio, reason is: snd_pcm_open(iec958:{ AES0 0x02 }): No such file or directory
```

If I set the 'Passthrough Output device' to 'ALSA:Default' I get the super fast clicking.  the following is what appears in the logs:

```
2009-10-27 18:25:00.721 DPMS Deactivated                                          
2009-10-27 18:25:02.241 AFD: Opened codec 0x8bdba00, id(MPEG2VIDEO) type(Video)   
2009-10-27 18:25:02.241 NVP: Disabling Audio, params(-1,-1,-1)                    
2009-10-27 18:25:02.264 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'  
2009-10-27 18:25:02.298 OSD Theme Dimensions W: 640 H: 480                        
2009-10-27 18:25:02.553 TV: Changing from None to WatchingPreRecorded             
2009-10-27 18:25:02.666 Video timing method: USleep with busy wait                
2009-10-27 18:25:02.724 DPMS Reactivated.                                         
2009-10-27 18:25:02.734 AFD: Warning, video codec 0x8bdba00 id(MPEG2VIDEO) type (Video) already open.
2009-10-27 18:25:02.819 AFD: codec AC3 has 0 channels                                                
2009-10-27 18:25:02.819 AFD: Opened codec 0x8932cc0, id(AC3) type(Audio)                             
2009-10-27 18:25:02.822 Opening audio device 'default'. ch 2(2) sr 48000                             
2009-10-27 18:25:02.822 Opening ALSA audio device 'default'.                                         
2009-10-27 18:25:02.824 DPMS Deactivated                                                             
2009-10-27 18:25:02.824 DPMS Reactivated.                                                            
2009-10-27 18:25:02.837 NVP: Enabling Audio                                                          
2009-10-27 18:25:02.839 Opening audio device 'default'. ch 2(2) sr 48000                             
2009-10-27 18:25:02.839 Opening ALSA audio device 'default'.                                         
2009-10-27 18:25:02.925 DPMS Deactivated                                                             
2009-10-27 18:25:03.025 DPMS Reactivated.                                                            
2009-10-27 18:25:03.025 DPMS Deactivated                                                             
2009-10-27 18:25:03.025 DPMS Reactivated.                                                            
2009-10-27 18:25:03.627 DPMS Deactivated                                                             
2009-10-27 18:25:03.704 NVP: Disabling Audio, params(-1,-1,-1)                                       
2009-10-27 18:25:03.854 AFD: Warning, video codec 0x8bdba00 id(MPEG2VIDEO) type (Video) already open.
2009-10-27 18:25:03.997 AFD: codec AC3 has 0 channels                                                
2009-10-27 18:25:03.998 AFD: Opened codec 0x9984e50, id(AC3) type(Audio)                             
2009-10-27 18:25:04.001 Opening audio device 'default'. ch 2(2) sr 48000                             
2009-10-27 18:25:04.001 Opening ALSA audio device 'default'.                                         
2009-10-27 18:25:04.017 NVP: Enabling Audio                                                          
2009-10-27 18:25:04.019 Opening audio device 'default'. ch 2(2) sr 48000                             
2009-10-27 18:25:04.019 Opening ALSA audio device 'default'.    

```

What do I have configured wrong?  This is the last thing I need to get working...

Thanks!

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

ls /dev/snd
controlC0  pcmC0D3p  seq  timer

more /etc/asound.conf
pcm.!default {
        type hw
        card 0
        device 3
}
```

---

### Post by drumz on 2009-11-05
Ok, so I updated to Mythbuntu 9.10 and have the same problem.

So instead of using the 'internal' player in MythTV 0.22 for DVD playback I've switched it to using mplayer instead and I have sound.

BUT I can't figure out how to use my remote to control mplayer using dvdnav.  That's the last piece I need to get working and I'll be home free.....

**Update:**  I have most of the controls now working, I just have to get the 'Enter' key to work.  Using the ~/.lirc/mplayer file I created a new one (one that was there once I found it didn't work at all).  It's recognizing everything, including the 'Ok' ('enter') button on my remote but it's not starting the movie...

**Update 2:** Finally got it....the 'config' entry for the 'enter' key should be 'dvdnav 6'.

So I finally have MythTV doing DVD playback using mplayer (not 'internal' player) and getting audio over HDMI.  Yay!!

---

### Post by Dewey_Oxberger on 2009-11-05
For some help with audio over hdmi make your way to this thread:


[http://ubuntuforums.org/showthread.php?t=1285957](http://ubuntuforums.org/showthread.php?t=1285957)

Download the asound.conf.txt file and have a read.

---

