---
title: "Frontend Hangs on Playback of Recorded TV"
date: 2010-10-08
forum: Mythbuntu
---

### Post by slamhound on 2010-10-08
I've been having somewhat of a strange problem with playback of recorded TV on my combined Backend/Frontend machine.  I'm using 10.04 64bit with autobuilds enabled, and I also have a remote frontend.  Everything used to work fine, but then one day I started having trouble with playback of recorded TV on the combined BE/FE machine. Basically, when I select a program and press play, it looks like it tries to start playing, but then the frontend hangs before any frames show up.  I have to use alt-F4 to kill it. It doesn't happen with all programs, and even different episodes of the same series will sometimes play, while others will not (though most are having the problem now). Note that the remote frontend has no problems at all playing the same programs.  As I said, things used to work fine, but then I started having the problems, but did not make any changes other than normal updates. Also, regular TV plays fine, as do recorded videos.  

There are clearly errors in mythwelcome.log (this is where I should look if I am using mythwelcome, right? There is nothing in mythfrontend.log), but I'm not sure what to do with them.  Here is the log for attempts at watching two programs, one that works (the one that starts at 16:00:40) and one that doesn't (the one that starts at 16:01:18 ). Note that many of the errors that show up show up for both the program that works and the one that doesn't, but there are definitely many that are unique to the program that doesn't work.  Any advice on how to troubleshoot this?

```

2010-10-08 16:00:39.943 TV: Attempting to change from None to WatchingPreRecorded
2010-10-08 16:00:40.067 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.068 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.069 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.070 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.071 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.072 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.073 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.073 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.074 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.075 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.076 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.076 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.077 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.078 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:00:40.142 AFD: Opened codec 0x6df5460, id(MPEG2VIDEO) type(Video)
2010-10-08 16:00:40.142 AFD: codec AC3 has 6 channels
2010-10-08 16:00:40.144 AFD: Opened codec 0x7556fe0, id(AC3) type(Audio)
2010-10-08 16:00:40.275 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-10-08 16:00:40.276 Opening ALSA audio device 'default'.
2010-10-08 16:00:40.397 AudioOutput Warning: Mixer attach error -2: No such file or directory
            Check Mixer Name in Setup: '/dev/mixer'
2010-10-08 16:00:40.561 VDPAU: Created 2 output surfaces.
2010-10-08 16:00:40.561 VDPAU: Version 1
2010-10-08 16:00:40.561 VDPAU: Information NVIDIA VDPAU Driver Shared Library  195.36.24  Thu Apr 22 19:52:55 PDT 2010
2010-10-08 16:00:40.561 VDPAU: Created VDPAU render device 1920x1080
2010-10-08 16:00:40.702 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-10-08 16:00:40.703 FilterManager: Failed to load filter 'colorspace', no such filter exists
2010-10-08 16:00:40.704 OSD Theme Dimensions W: 1280 H: 720
2010-10-08 16:00:40.833 TV: Changing from None to WatchingPreRecorded
2010-10-08 16:00:40.833 Realtime priority would require SUID as root.
2010-10-08 16:00:40.840 OpenGLVideoSync()
2010-10-08 16:00:40.952 Video timing method: SGI OpenGL
2010-10-08 16:00:40.971 VDPAU Error: Error at mythrender_vdpau.cpp:592 (#23, The system does not have enough resources to complete the requested operation at this time.)
2010-10-08 16:00:40.971 VDPAU Error: Failed to create output surface.
2010-10-08 16:00:40.971 VDPAU: Added 0 output surfaces (total 2, max 4)
2010-10-08 16:01:05.841 TV: Attempting to change from WatchingPreRecorded to None
2010-10-08 16:01:05.850 ~OpenGLVideoSync() -- closing opengl vsync
2010-10-08 16:01:05.855 TV: Changing from WatchingPreRecorded to None
2010-10-08 16:01:18.079 TV: Attempting to change from None to WatchingPreRecorded
2010-10-08 16:01:18.178 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.179 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.179 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.179 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.180 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.192 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.192 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.193 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.194 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.195 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.195 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.196 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.197 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.198 [mpeg2video @ 0x7fc622ed5380]mpeg_decode_postinit() failure
2010-10-08 16:01:18.308 AFD: Opened codec 0x792ac60, id(MPEG2VIDEO) type(Video)
2010-10-08 16:01:18.309 AFD: codec AC3 has 6 channels
2010-10-08 16:01:18.310 AFD: Opened codec 0x767c1c0, id(AC3) type(Audio)
2010-10-08 16:01:18.435 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-10-08 16:01:18.435 Opening ALSA audio device 'default'.
2010-10-08 16:01:18.556 AudioOutput Warning: Mixer attach error -2: No such file or directory
            Check Mixer Name in Setup: '/dev/mixer'
2010-10-08 16:01:18.778 VDPAU: Created 2 output surfaces.
2010-10-08 16:01:18.778 VDPAU: Created VDPAU render device 1920x1080
2010-10-08 16:01:18.857 VDPAU Error: Error at mythrender_vdpau.cpp:636 (#23, The system does not have enough resources to complete the requested operation at this time.)
2010-10-08 16:01:18.857 VidOutVDPAU Error: Unable to create VDPAU buffers
2010-10-08 16:01:18.858 VidOutVDPAU Error: Unable to create VDPAU mixer
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, A not in available, pause, or displayed                  
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, B not in available, pause, or displayed A                
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, C not in available, pause, or displayed AA               
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, D not in available, pause, or displayed AAA              
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, E not in available, pause, or displayed AAAA             
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, F not in available, pause, or displayed AAAAA            
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, G not in available, pause, or displayed AAAAAA           
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, H not in available, pause, or displayed AAAAAAA          
2010-10-08 16:01:18.860 VideoBuffers::DiscardFrames(): ERROR, a not in available, pause, or displayed AAAAAAAA         
2010-10-08 16:01:18.861 VideoBuffers::DiscardFrames(): ERROR, b not in available, pause, or displayed AAAAAAAAA        
2010-10-08 16:01:18.861 VideoBuffers::DiscardFrames(): ERROR, c not in available, pause, or displayed AAAAAAAAAA       
2010-10-08 16:01:18.861 VideoBuffers::DiscardFrames(): ERROR, d not in available, pause, or displayed AAAAAAAAAAA      
2010-10-08 16:01:18.861 VideoBuffers::DiscardFrames(): ERROR, e not in available, pause, or displayed AAAAAAAAAAAA     
2010-10-08 16:01:18.861 VideoBuffers::DiscardFrames(): ERROR, f not in available, pause, or displayed AAAAAAAAAAAAA    
2010-10-08 16:01:18.861 VideoBuffers::DiscardFrames(): ERROR, g not in available, pause, or displayed AAAAAAAAAAAAAA   
2010-10-08 16:01:18.861 VideoBuffers::DiscardFrames(): ERROR, h not in available, pause, or displayed AAAAAAAAAAAAAAA  
2010-10-08 16:01:18.861 VideoBuffers::DiscardFrames(): ERROR, 0 not in available, pause, or displayed AAAAAAAAAAAAAAAA 
2010-10-08 16:01:18.877 VideoBuffers::DiscardFrames(): ERROR, A not in available, pause, or displayed                  
2010-10-08 16:01:18.877 VideoBuffers::DiscardFrames(): ERROR, B not in available, pause, or displayed A                
2010-10-08 16:01:18.877 VideoBuffers::DiscardFrames(): ERROR, C not in available, pause, or displayed AA               
2010-10-08 16:01:18.878 VideoBuffers::DiscardFrames(): ERROR, D not in available, pause, or displayed AAA              
2010-10-08 16:01:18.878 VideoBuffers::DiscardFrames(): ERROR, E not in available, pause, or displayed AAAA             
2010-10-08 16:01:18.878 VideoBuffers::DiscardFrames(): ERROR, F not in available, pause, or displayed AAAAA            
2010-10-08 16:01:18.878 VideoBuffers::DiscardFrames(): ERROR, G not in available, pause, or displayed AAAAAA           
2010-10-08 16:01:18.878 VideoBuffers::DiscardFrames(): ERROR, H not in available, pause, or displayed AAAAAAA          
2010-10-08 16:01:18.878 VideoBuffers::DiscardFrames(): ERROR, a not in available, pause, or displayed AAAAAAAA         
2010-10-08 16:01:18.878 VideoBuffers::DiscardFrames(): ERROR, b not in available, pause, or displayed AAAAAAAAA        
2010-10-08 16:01:18.879 VideoBuffers::DiscardFrames(): ERROR, c not in available, pause, or displayed AAAAAAAAAA       
2010-10-08 16:01:18.879 VideoBuffers::DiscardFrames(): ERROR, d not in available, pause, or displayed AAAAAAAAAAA      
2010-10-08 16:01:18.879 VideoBuffers::DiscardFrames(): ERROR, e not in available, pause, or displayed AAAAAAAAAAAA     
2010-10-08 16:01:18.879 VideoBuffers::DiscardFrames(): ERROR, f not in available, pause, or displayed AAAAAAAAAAAAA    
2010-10-08 16:01:18.879 VideoBuffers::DiscardFrames(): ERROR, g not in available, pause, or displayed AAAAAAAAAAAAAA   
2010-10-08 16:01:18.879 VideoBuffers::DiscardFrames(): ERROR, h not in available, pause, or displayed AAAAAAAAAAAAAAA  
2010-10-08 16:01:18.880 VideoBuffers::DiscardFrames(): ERROR, 0 not in available, pause, or displayed AAAAAAAAAAAAAAAA 
2010-10-08 16:01:18.880 VideoOutput, Error: Not compiled with any useable video output method.
2010-10-08 16:01:18.880 NVP(1), Error: Couldn't create VideoOutput instance. Exiting..
2010-10-08 16:01:18.880 Unable to initialize video.
2010-10-08 16:01:38.694 playCtx, Error: StartDecoderThread() Failed to startdecoder
2010-10-08 16:01:40.850 MythWelcome received a recording list change event
2010-10-08 16:01:40.850 MythWelcome received a recording list change event
2010-10-08 16:01:40.850             [deferred to pending handler]
2010-10-08 16:01:40.850 MythWelcome received a recording list change event
2010-10-08 16:01:40.850             [deferred to pending handler]

```

---

### Post by LowSky on 2010-10-08
What video card do you have?

Have you tried updating the video drivers 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by slamhound on 2010-10-09
I have an 8600GT.  I guess I'd prefer to stick with the hardware drivers in the normal repositories, but could try that if there are no other solutions (though I may upgrade to 10.10, which if I'm not mistaken will also upgrade the drivers).  

After googling the specific error messages some more, it seems as though people were having similar problems with .22, but the issues they were having were fixed with .23, and I haven't seen any more references to these problems with people who were using .23.  

Also, one suggestion was that 256MB cards (which mine is) might be problematic, and that VDPAU might need 512MB (though obviously 256 works for some).  Interestingly, I found one poster who had a card that was supposed to have 256MB, but that nvidia settings reported as having 512.  I checked nvidia settings on mine, and sure enough it said that my card had 512MB, when the box said 256. Don't know if that is relevant.

Anyway, if there aren't other suggestions, perhaps I'll try updating the drivers, or maybe even switching to the on-board 8300 (which always stuttered for me a bit, but which I know others have gotten working).

---

### Post by slamhound on 2010-10-09
Well, I didn't try updating the drivers, but I did try switching back to the on-board 8300.  Even with vdpau slim, it stuttered on HD OTA content (which was my previous experience).  Does anyone have recommended settings with the 8300?  I tried the ones listed on the mythtv vdpau site (where users report their luck with different cards).

Anyway, I went back to the 8600, and found something new.  I had played around with the vdpau settings when I was trying the 8300 and had left it on vdpau normal when I switched back to the 8600.  When I tried playing some of the recorded programs that were giving me problems, they mostly played. Every once and a while, they would give me the same freezing problem, but for the most part they played.  So I went back and tried vdpau high quality (which was the setting I first used with the card, when I had no problems) and vdpau slim (which is what I switched to in my first attempt to fix the freezing problem).  In both cases, I would get the freezing problem with almost every file.  But when I tried vdpau normal, it would play almost every file.  Strange.  

Anyway, I'll stick with this profile and hopefully it will work most of the time.  I'll keep my fingers crossed than a driver update will fix it completely.

---

### Post by slamhound on 2010-10-31
Okay, more info; still looking for advice.  I upgraded the drivers to the current version (260?) using the PPA (I did not switch to 10.10).  This didn't help at all.  However, I remembered one big change in my setup that I had (stupidly) ignored--I switched from a 720p TV to a 1080p TV.  And that is what caused the change.  If I use nVidia settings to change the resolution back to 720, then the files play fine rather than freezing the frontend. 

So perhaps I'm just reaching the limitations of my card, as the earlier threads I found suggested that a 256MB card may be insufficient for VDPAU, and perhaps once I bump this to 1080, that limitation shows up. But here's my question:  why does this play the live TV with no problems, but playing a recorded version of the same program freezes the frontend?  And given that it does play live tv, can anyone think of a workaround to get the recordings to work, too?  If not, it's not a big deal.  Even on my big TV, 720p is probably okay, so I could just permanently change the resolution.  But I'd rather not if I didn't have too.

---

### Post by grygub on 2010-11-02
I have encountered a similar problem. I found this [**[COLOR="Blue"]Thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1604893") and this [**[COLOR="blue"]bug ticket[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/644835") that fixed everything for me. Hope this helps.

---

### Post by slamhound on 2010-11-02
Thanks for the suggestion.  I looked over the thread and bug report, but it looks like those are related to xvmc, and the solution is to turn off profiles that use xvmc.  I think (though someone can correct me if I'm wrong) that if I'm using profiles that use vdpau, then they do not use xvmc.  It looks like the specific error messages differ a bit, too.  But, I'll look at these links a bit more to see if the problems are related.

---

### Post by LowSky on 2010-11-02
I used to use a 8600GT too. I would get random freezes and vido playback failures, my logs said I ran out of video memory so It was probably the memory size being reported incorrectly.

You have to realize that the 8600 is one of the first cards that started to support VDPAU, and even a lower end model from a newer series will out perform the 8600 in video playback. the best bang for your buck is an Nvidia GT 220 or 240 right now.

---

### Post by slamhound on 2010-11-02
Sure; that makes sense.  Perhaps I'll upgrade sometime and just use 720p until then.  

But I'm curious as to what the technical details are that would allow live tv to play at 1080 but not recordings.

---

