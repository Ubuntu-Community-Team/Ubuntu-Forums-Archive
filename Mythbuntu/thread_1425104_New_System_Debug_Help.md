---
title: "New System Debug Help"
date: 2010-03-08
forum: Mythbuntu
---

### Post by sfuse on 2010-03-08
Just finished building and installing mythbuntu on new box.   I am new to mythbuntu and HTPC hardware but not linux.  I have been experiencing some problems, some of which I think I have fixed thanks to google but now need some direction on a couple of problems.
 
I have one dedicated frontend/backend system.  
I have a Hauppauge HVR-2250 and after installing the drivers this seems to be working correctly.  
I have an NVIDIA video card using VDPAU.
The rest is generic hardware, and I am using onboard audio.
 
 
 I have experienced some lockups and would like to know how best to debug the problem(s).  At first these were only frontend lockups but after tweaking some settings I haven't had any of these for a while.  But now they have become hard system lockups, no SSH access, no access via keyboard.  I don't really know how to debug this, the myth logs seem to be filled with all sorts of information and I am not sure what to look for.  Any direction would be greatly appreciated.
 
One other annoyance is that once a lockup occurs and I reset the machine I can't access tuner card from the frontend.  I have to restart the backend before it will work so it would seem this would occur anytime the backend isn't shutdown properly.  Does anyone have a script or method to correct this annoyance?
 
Any help would with these problems would be greatly appreciated.

---

### Post by sfuse on 2010-03-09
After thinking about the lockups some more I decided to shutdown the frontend last night and left the backend running with one scheduled recording.  While that was running I mounted an nfs directory and copied my mp3 collection over to the new box.  I also installed MPD and let the box play music all night.  The box ran all night without locking up.

  I never experienced any system lockups until this morning.  

I watched about half of the recording from last night and because the commercial skipping wasn't working very well I decided to turn off the  strict commercial skip option.
 I went to the manage recordings screen and set the recording to flag commercials again.
 Then I went to Information Center -> System Status -> Job Queue to make sure the job was running.  I left everything alone other than an SSH terminal with top running and sometime while the commercial flag job was running the system locked up.

Anyone experience this type of problem?  I would seem that the lockup was caused by the commercial flag job.

---

### Post by rhpot1991 on 2010-03-09
I would try running memcheck to make sure you don't have a hardware issue.

---

### Post by klc5555 on 2010-03-09
> **rhpot1991 said:**
> I would try running memcheck to make sure you don't have a hardware issue.

I'd agree. The vast majority of times I've been plagued with complete lockups on mythtv, the culprits were hardware: CPU overheating, fanless NVidia video card overheating, or a wonky power supply causing problems that seemed like memory errors. That sort of thing. I've never personally had a memory SIMM go bad, though it does happen.

About the only software that can do such a complete lockup that even SSH is dead is the video card driver. Mythcommflag won't do a lockup running in userspace; it will just fail and abort.

---

### Post by sfuse on 2010-03-10
rhpot, you were correct.

 I had run memtest but only for about 30 minutes.  After letting it run longer I started seeing a few errors.  I found some tweaks for the bios on the memory manufacturers web site and these seem to have done the trick.  I have let the memtest run for over 2 hours with no errors so I now have my fingers crossed.

I should have suspected a hardware failure since, in my experience with linux of any flavor, a hard system lockup is practically always hardware related.

---

