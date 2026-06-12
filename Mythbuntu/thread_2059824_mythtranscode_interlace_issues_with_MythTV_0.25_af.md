---
title: "mythtranscode interlace issues with MythTV 0.25 after 12.04 upgrade"
date: 2012-09-18
forum: Mythbuntu
---

### Post by lynchaj on 2012-09-18
Hi
 
I am a user of Mythbuntu 12.04 with a pair of PVR-250's. Recently I upgraded to 12.04 (MythTV 0.25) and am having some issues. I record regular NTSC analog cable to MPEG2 via ivtv from the PVR-250's.
 
In particular, when I specify an MPEG2 recording to be transcoded to MPEG4 I get horrible combing and it looks like the interlace is broken. Sort of like the vertical resolution is cut in half. 
 
If I set the transcoding profile to "pass through" then the video looks fine but of course is still its native MPEG2 and not MPEG4. I searched quite a bit for a solution to the problem but I am not sure what's wrong. 
 
This message on MythTV-users sounds a lot like the symptoms I am seeing:
 
[http://www.mythtv.org/pipermail/mythtv-users/2012-May/333230.html](http://www.mythtv.org/pipermail/mythtv-users/2012-May/333230.html)
 
(see paragraph #2)
 
One person later in the thread above suggested deinterlacing the MPEG2 file before transcoding. I don't know how to do that though. 
 
I tried various deinterlace settings on playback to no effect. I confirmed on another computer that the transcoded file itself has the interlace artifacts so it is not a playback issue AFAIK.
 
Does anyone recognise this problem and know how to fix it? I am sorry if this is a FAQ but I could little information on the problem so I may be looking for the wrong thing. 
 
Please help!
 
Thanks and have a nice day!
 
Andrew Lynch

---

### Post by nickrout on 2012-09-18
I have no solution, but I have to ask why you are doing this transcdoing?

---

### Post by lynchaj on 2012-09-19
> **nickrout said:**
> I have no solution, but I have to ask why you are doing this transcdoing?
 
Hi
Well at the moment I am not transcoding since it produces such low quality video.  I thought I found a fix by adding a transcode filter (kerneldeint) in the recording profile.  While it did fix the interlace issue the resulting video still had major motion artifacts (blockiness) and was significantly less quality than before the upgrade to 12.04.
 
Apparently something dramatic happened in the 12.04 upgrade which changed the transcode function.  I am not sure what it is but the ivtv MPEG2 doesn't seem to be able to transcode without major degradation.
 
The main purpose of the transcode to MPEG4 AVC from MPEG2 is to save disk space.  At the moment (AFAIK) mythtranscode only supports RTJPEG and MPEG4.  
 
Thanks!

Andrew Lynch

---

### Post by nickrout on 2012-09-19
> **lynchaj said:**
> Hi
Well at the moment I am not transcoding since it produces such low quality video.  I thought I found a fix by adding a transcode filter (kerneldeint) in the recording profile.  While it did fix the interlace issue the resulting video still had major motion artifacts (blockiness) and was significantly less quality than before the upgrade to 12.04.
 
Apparently something dramatic happened in the 12.04 upgrade which changed the transcode function.  I am not sure what it is but the ivtv MPEG2 doesn't seem to be able to transcode without major degradation.
 
The main purpose of the transcode to MPEG4 AVC from MPEG2 is to save disk space.  At the moment (AFAIK) mythtranscode only supports RTJPEG and MPEG4.  
 
Thanks!

Andrew LynchBuy a bigger hard drive!

---

### Post by lynchaj on 2012-09-20
> **nickrout said:**
> Buy a bigger hard drive!
 
Yes, that's a brute force solution however I'd like to find out what's really going on before taking drastic measures.  I already have a 1GB SATA drive so it is not an immediate problem.  
 
It seems to me something has changed with the MythTV transcode.  Either I have a misconfigured system or there is a bug someplace.  Throwing more hardware at the problem doesn't fix the underlying issue.
 
Has ivtv MPEG2 transcoding been deprecated?  Conversion to good quality MPEG4 AVC used to work so well I am a bit surprised.  I am wondering if anyone else is seeing issues with the transcode or if this problem is unique to my PVR.
 
Thanks!

Andrew Lynch

---

### Post by Lou2401 on 2012-09-29
It's exacly the same issue for me. I am having artefacts especially on fast moving scenes. I have already searched across the internet to find a solution, but so far I had no luck. Don't know since when this is happening, but in the past I had no such issues. Transcoding was running always with fine results.

---

### Post by zugnish on 2013-05-18
I had a look at this a while ago, as it was frustrating me as well, especially since it had worked so well previously. 

It doesn't look like there was much of a change in mythtranscode that would have caused this - you can diff the old and the new versions and the code that calls the transcoder is pretty much the same - this problem seems to be deeper in libav and the video4linux libraries. Not knowing a  great deal about how these work, it's hard for me to say what caused it to change.

The root of the problem is that the transcoders that convert the high bit-rate mpeg2 data to lower bit-rate mpeg4 are really bad at handling interlaced video - hence all the combing and artifacting. You can really spot this if you are looking at recorded video from HD tv networks, where the commercials and interstitial programming is recoreded in interlaced SD and the HD broadcasts are non-interlaced. You'll get beautifully transcoded video for the show, and near-unwatchabled artifacted rubbish in the ad breaks. Obviously no big deal on HD shows, but on regular programming this is still a huge nuisance.

I think (based on the flags that mythtranscode passes) that libav/v4l used to run a de-interlace prior to transcoding each frame, but this is no longer happening. As I said before, I don't think this was caused by any changes in mythtranscode.

Given that the changes seem to be in libraries that mythtv consumes rather than provides, I doubt we'll get much from the mythtv or ubuntu developers, unless those responsible for the transcode library happen to notice. The best I can say right now is that if you try to keep your libv4l and libav libraries as up to date as you can without breaking compatibility with the current mythtv version, a fix might appear (assuming the cause was a bug in those packages). Or you could try downgrading, but that didn't seem particularly feasible, since the video libaries are pretty key dependencies for all of mythtv.

---

