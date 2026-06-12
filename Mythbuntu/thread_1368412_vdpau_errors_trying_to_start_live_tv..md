---
title: "vdpau errors trying to start live tv."
date: 2009-12-30
forum: Mythbuntu
---

### Post by rodercot on 2009-12-30
Hey All,

 I am trying to get all my system on the same upgrade path this involved getting the same repos and bringing all my nvidia drivers up to the same 190-glx. All the machines are working with vdpau normal as playback profile except one. 

 This is the error from the log - I can set the playback profile to cpu+ or cpu slim and it will load but liveTv is pretty much unwatchable.

 This is the latest fix from JYA's repos.

 2009-12-30 15:33:26.975 mythfrontend version: branches/release-0-22-fixes [23034] [www.mythtv.org](www.mythtv.org)

 2 machines are 8.10 and one is 9.10 the backend is 8.10.

 ```
2009-12-30 15:45:50.950 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-12-30 15:45:51.704 AFD: Opened codec 0xa315b40, id(MPEG2VIDEO) type(Video)
2009-12-30 15:45:51.704 AFD: codec MP2 has 2 channels
2009-12-30 15:45:51.704 AFD: Opened codec 0xa312820, id(MP2) type(Audio)
2009-12-30 15:45:52.054 Opening audio device 'hdmi'. ch 2(2) sr 48000 (reenc 0)
2009-12-30 15:45:52.055 Opening ALSA audio device 'hdmi'.
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-12-30 15:45:52.056 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2009-12-30 15:45:52.140 VDPAU Error: Error at util-vdpau.cpp:222 (#1, Unknown)
2009-12-30 15:45:52.140 VidOutVDPAU Error: Failed to initialise VDPAU
2009-12-30 15:45:52.141 VideoOutput, Error: Not compiled with any useable video output method.
2009-12-30 15:45:52.141 NVP(0), Error: Couldn't create VideoOutput instance. Exiting..
2009-12-30 15:45:52.141 Unable to initialize video.
2009-12-30 15:46:12.105 playCtx, Error: StartDecoderThread() Failed to startdecoder
2009-12-30 15:46:12.105 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2009-12-30 15:46:12.106 TV Error: LiveTV not successfully started
```

 Thanks,

 Dave

---

### Post by zorro07 on 2009-12-30
hi,
 What videocard do you have in the machine giving you trouble with vdpau?
the 9400 would be the starting point for good vdpau.  some earlier cards work but
dont have the full implimentation that vdpau needs to shine.
 
cheers

---

### Post by rodercot on 2009-12-31
The board is a P5N7A-VM with a 9300 on it. I have been running vdpau in xbmc for a long time with the std nvidia drivers installed from a command line with vdpau enabled and if I roll the glx drivers back to glx-185 it will allow myth live tv to start with the vdpau profiles.

 The other machine that is working with 195-glx is the same board and same video card and it seems to work fine, I will look at the log from that machine and these are both 8.10 machines my test machine is a amd 3200 with an 8600GT and 9.10 and it seems to run fine as well with 195glx. 

 Thanks,

 Dave

---

### Post by dblegend on 2010-01-09
I've been having this same problem for the last couple of weeks myself.  I'm running an ION 9400 with an n330 on the zotac a-u board.  VDPAU was working fine for a couple of months and then started getting the util-vdpau.cpp:222 error for both LiveTV and when trying to watch recorded videos.  I'm not sure exactly what changed to cause the issue.  I tried all of the different versions of the nvidia-glx (avenard) driver from 180 to 195 to no avail.  Switching back to ffmpeg allows me to watch output, but it's obviously not as clean without the hardware acceleration.  Has anyone been able to resolve this?  If not, can I provide some additional documentation to help get to the bottom of it?  Thanks.

Dave 2

---

### Post by dblegend on 2010-01-09
I have to amend part of my previous update.  I guess I had not tried the 185 drivers.  Once I installed those, everything is working with VDPAU again.  It looks like the issue has something to do with the newer drivers.  I'd be willing to install the newer ones and run some tests if anyone has interest in troubleshooting the issue.

Dave 2

---

