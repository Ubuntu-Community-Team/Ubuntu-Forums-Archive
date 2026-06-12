---
title: "only getting red screen when watching tv or mplayer"
date: 2012-02-02
forum: Mythbuntu
---

### Post by sdahlin on 2012-02-02
I have an athlon II 3 core system which has a built nvidia 7025 video.  The video capture card is a hauppauge hvr-1600 (cx18).  I have installed mythbuntu 11.10 64bit and brought all the packages up to date.  The nvidia driver is 173 and it is activated and in use.

I stepped thru the process of setting up mythbuntu backend with the video card of type IVTV Mpeg-2 encoder card.  A video source setup and scanned the channels (which seemed to have been found).

lsmod indicates the drivers are up and running for the video capture card.  However, when I try watching tv or running mplayer -vo xv /dev/video0 all I get is a red screen now.  Curiously though with a previous install run I did get some video.  I cannot figure out what I did different between the 2 installs.

Any suggestions.
Thanks

---

### Post by sdahlin on 2012-02-05
Is this happening to anyone else?

---

### Post by nickrout on 2012-02-06
Does mplayer play any non mythtv videos?

---

### Post by sdahlin on 2012-02-08
normally mplayer is used to play avis, mpgs, etc.  I tried mplayer because it had been recommended as a way to test the /dev/video0 output.  As I indicated, once it worked but I first tried to run the 32bit version (which installs after formattingbut then when you try to run it the screen never shows anything).  I reinstalled the 64 bit version (reformatting of course) and now I just get the red screen.

---

### Post by klc5555 on 2012-02-09
Test mplayer on some known good video file that did not come through /dev/video0 and your Hauppauge 1600.

If mplayer works with anything other than 1600 output, and conversely no other player, like xine or vlc can play a Hauppauge 1600-recorded file without red screen, then the problem is likely the cx18 driver and your particular version/revision (of which there must be over a dozen) of the 1600. 

Googling the Hauppauge 1600 (or cx18) and "red screen" will lead you to the large quantity of traffic on this topic on this forum and several others (particularly over at linuxtv.org). Depending on the version/revision of the 1600 you have, the solution generally ends up being a special compile of newer or patched cx18 source.

---

### Post by LarryJ2 on 2012-02-10
Sadlin:

Yes, it's happening to me also.  Both HVR-1600 and PVR-USB2 are both showing this anomaly.  Only my screen is Green but recently I've had Red screens.   

Are you using the 3.0 kernel.  This problem may have arrived  with the 3.0 kernel.  

I compiled the V4L2 source.  No help.  All devices seem to be loading OK.  I test with "mplayer /dev/video0" for the HVR-1600 and "mplayer /dev/video2" for the PVR-USB2.

Like my wife said, if I didn't have a Mythtv installation, I wouldn't have a full time hobby.  I simply cannot resist upgrading.  Almost always trouble!

Larry

---

### Post by sdahlin on 2012-02-12
I have switched to mythbuntu 11.04 which uses the 2.6 kernel and there are 2 differences.  I am having the problem with the nvidia driver of being activated but not in use and the video output is now blank and not red.  As to the nvidia driver I remember this problem from a while ago but I never really solved it.  I scoured the boards for solutions each one promising to fix the problem (which for some it did) but no solution seems to fix the problem.

---

### Post by sdahlin on 2012-02-12
I feel like I am chasing a ghost here.  The sources say try this, try that, this worked for me.  All along nothing seems to fix the problem.  I have tried difference versions of mythbuntu (11.04 and 11.10), along with apt-getting this or that package, etc. etc. and no luck.  I love tinkering but only if it eventually gets me somewhere!!!

---

### Post by nickrout on 2012-02-13
> **sdahlin said:**
> I feel like I am chasing a ghost here.  The sources say try this, try that, this worked for me.  All along nothing seems to fix the problem.  I have tried difference versions of mythbuntu (11.04 and 11.10), along with apt-getting this or that package, etc. etc. and no luck.  I love tinkering but only if it eventually gets me somewhere!!!

I think you have been asked 2 or 3 times in this thread whether mplayer will pay a known good file. I don't believe you have replied.

---

### Post by sdahlin on 2012-02-16
Sorry, I should have noted that it does play avi/mpg files.  Here is the curious thing.  I mentioned that when I first installed I was able to see the /dev/video0 output and then I was getting the red screen.  After another install the same pattern arose.  I found that it was working and then later the red screen again.  In between both I did some tweaks such as updating the nvidia driver (from 173 to current).  Then when I checked later on the red screen comes up.

I guess I may have to reinstall and carefully test each step along the way to try to isolate the specific cause if it can be found.

Also, the red screen thread discussed applying patches which have been made months/year ago.  I presume that those patches have been merged into the version I was running.

---

### Post by nickrout on 2012-02-16
presumption is the mother of all stuffups. Are you sure a channel is tuned?

---

### Post by matt06 on 2012-02-16
> **sdahlin said:**
> Also, the red screen thread discussed applying patches which have been made months/year ago.  I presume that those patches have been merged into the version I was running.

I run 10.04 with (2) HVR-1600's and I'm assuming this still applies to 11.xx (someone correct me if I am wrong), but have you built and installed the newest v4l-dvb drivers as per [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) ?  If not, what version are you running?

I can do 'dmesg | grep cx18' on my 10.04 box and get this near the top.

```
[    3.646278] cx18:  Start initialization, version 1.5.1
```

As I understand it, there are *many* versions of the HVR-1600 and yours may not be detected correctly or even supported in the driver.  The place to go from here may be the ivtv mailing list at [http://www.gossamer-threads.com/lists/ivtv/users/](http://www.gossamer-threads.com/lists/ivtv/users/) , but I think you need to post more info to determine what is going on.

---

### Post by sdahlin on 2012-02-28
By downloading the latest version of v4lb from linuxtv.org, compiling and installing it seemed to solve the problem.  I then moved the box to the location that would then be connected to my tv.  At that point programs could be recorded but with only video and not sound!  I received messages indicating the ac-tex was damaged.  Recompiling in situ did not resolve the issue (in fact the red screen returned!)  

So I brought the box back out to my work site, reinstalled the os, and did the recompile, etc.  Both video and audio recorded.  There were a couple of shutdowns in between to try to remove that variable.  Again in the new location the audio no longer recorded.

I was wondering if the quality of the signal was involved but when I run "Watch Now" the signal strength is said to be 100%.  I was trying to find a cable tester to see if there is some difference between the 2 locations but most of the tools are just provide tone.  I cannot seem to find one that provides the db loss or the signal to noise ratio.

---

### Post by nickrout on 2012-02-29
Are you doing the analogue side or the digital side of this card?

/dev/video0 implies the analogue side.

---

### Post by sdahlin on 2012-02-29
I am running only the analog side.  I went over the logs and I am noticing a lot of the following entries in the syslog and kern.log:

[ 1522.996492] cx18-0: Skipped encoder IDX, MDL 395, 1 times - it must have dropped out of rotation
[ 1522.996530] cx18-0: Could not find MDL 395 for stream encoder IDX                                                              [ 1563.028374] cx18-0: Skipped encoder IDX, MDL 413, 1 times - it must have dropped out of rotation

A google search only finds the code for the cx18 driver and one entry which obliquely has similar entries.  I am not sure what this is telling me.

I am also getting messages in the mythbackend.log:

AFD Warning: ScanATSCCaptionStreams() called with no PMT        
AFD: Opened codec 0x7f533c002d80, id(MPEG2VIDEO) type(Video)    
AFD: codec MP2 has 2 channels                                   
AFD: Opened codec 0x7f533c17e620, id(MP2) type(Audio)           
[mpeg2video @ 0x7f5357096700]warning: first frame is no keyframe
[mpeg2video @ 0x7f5357096700]warning: first frame is no keyframe
[mpeg2video @ 0x7f5357096700]ac-tex damaged at 29 13            
[mpeg2video @ 0x7f5357096700]Warning MVs not available          
[mp2 @ 0x7f5357096700]incomplete frame                          
AFD Error: Unknown audio decoding error                         

I am unclear if these are related or not.

---

### Post by nickrout on 2012-02-29
The backend appears to be using the digital side by the look of the reference to atsc, so I am confused now.

---

