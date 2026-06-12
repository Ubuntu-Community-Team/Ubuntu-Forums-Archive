---
title: "Choppy unwatchable video on usb DVB-T2 (possibly mpg4 issue?)"
date: 2012-08-22
forum: Mythbuntu
---

### Post by marek_online on 2012-08-22
Hi,
 
I've a mythbuntu box running 0.24 + updates, using two usb tuners, one  for DVB-S/S2, which works fine, and one for DVB-T2, which produces  mainly garbage.
 
The card actually used to work okay (not great, but just about  watchable) in Myth, but a couple of weeks ago got worse to the point  that it's now just spatters of boxy colour and high pitched chirps of  sound.
 
The DVB-T2 card is the PCTV 290e nanostick, which works out of the box  Ubuntu, and works perfectly well in Kaffeine, so it's not a hardware  problem.
 
I've also had a new problem recently playing some (but not all) mpg4  files - similar boxy colour garbage after just a few seconds of playing  clearly. Given that T2 uses mpg4 I'm wondering if that's where the  problem lies, and I need to update some codec behind the scenes  somewhere.
 
The rest of the system is as follows (it's a version of the ASRock 3D vision)
 
Intel Core i3-370M 
4GB RAM
NVIDIA GeForce GT425M Graphics
 
Any pointers would be greatly appreciated. Have trawled the web for many many hours to no avail.

---

### Post by nickrout on 2012-08-22
> **marek_online said:**
> Hi,
 
I've a mythbuntu box running 0.24 + updates, using two usb tuners, one  for DVB-S/S2, which works fine, and one for DVB-T2, which produces  mainly garbage.
 
The card actually used to work okay (not great, but just about  watchable) in Myth, but a couple of weeks ago got worse to the point  that it's now just spatters of boxy colour and high pitched chirps of  sound.
 
The DVB-T2 card is the PCTV 290e nanostick, which works out of the box  Ubuntu, and works perfectly well in Kaffeine, so it's not a hardware  problem.
 
I've also had a new problem recently playing some (but not all) mpg4  files - similar boxy colour garbage after just a few seconds of playing  clearly. Given that T2 uses mpg4 I'm wondering if that's where the  problem lies, and I need to update some codec behind the scenes  somewhere.
 
The rest of the system is as follows (it's a version of the ASRock 3D vision)
 
Intel Core i3-370M 
4GB RAM
NVIDIA GeForce GT425M Graphics
 
Any pointers would be greatly appreciated. Have trawled the web for many many hours to no avail.

Could be bad antenna connection or similar issues. Could be your system is not up to playing back the h264 codec (I assume that is what you are referring to by mpg4). Are you using vdpau?

---

### Post by marek_online on 2012-08-22
Thanks for the reply.

I considered the bad antenna connection, but the thing works perfectly fine in Kaffeine - there are only a few digital TV channels available where I am and they all come in clear as you please using Kaffeine.

That would also suggest that it's a Mythtv rather than a generic codec or resources issue, no?

As you surmise, I don't really understand the details of codecs vs. containers and so on on the video front, but I remember seeing something about HD signals needing mpeg-4, so when the mpg4 video files - and only those ones - starting showing problems I figured there might be some connection between the two.

I am using vdpau. There's a DVB-S/S2 usb device in the same machine, which works a treat, so it must be something particular to DVB-T/T2.

---

### Post by jksj on 2012-08-23
High I am using the same dvb-t2 PCTV nanostick, which is working fine in ubuntu 12.04 mythtv 0.25 & 0.26. I remember having similar problems with 0.24 until I upgraded the nvidia driver. This seems to be the most important factor in getting reliable HD playback of mp4 (with vdpau). In Ubuntu 11.10 I had to use version 295.20 of the Nvidia driver and in 12.04  295.49. The versions in between caused problems.

By the way, bare in mind that Kaffeine & Mythtv are not sharing tuning information, check whether the frequencies are the same for the HD mux. You might be picking up a borderline signal from the wrong transmitter in Mythtv, if in doubt clear out the tuners & channels and do a full rescan.  You could use femon from the dvb-apps package to check the signal levels in both apps.

---

### Post by marek_online on 2012-08-23
Thanks jksj, good advice!

Upgrading the nvidia driver didn't have any effect, but getting at the channel settings did.

I wiped the channel settings and tried re-scanning. Nothing at first, but it turns out some of the MythTV channel scan default settings weren't right for me. I checked the successful channel details in Kaffeine, corrected MythTV on a Full Scan (Tuned) where appropriate, and have all of my channels coming in good and clear now!

This hasn't fixed my choppy mpg4 files though, alas, but the TV signal was the much more important bit...

---

### Post by jksj on 2012-08-23
Glad to hear you are at least partly sorted. I don't think any external codecs are used by mythtv, playback is done by the internal player. Does the Nvidia card support vdpau? I get perfect Mp4 HD playback on a single core atom processor (pathetic processing power) but with an nvidia ion graphics processor which supports VDPAU.

---

### Post by marek_online on 2012-08-23
Thanks.

The graphics card definitely supports vdpau, and I'm pretty sure I've everything necessary installed (nvidia-current and vdpau-video from xswat ppa), but still choppy on the mpg4 HD.

There should be plenty of grunt in the processor and the GPU to get the job done. Playback settings on Mythtv are set properly as well, I think.

---

### Post by nickrout on 2012-08-23
mpg4 is too vague a term to be useful here. In fact it is not a term that is uselful anywhere as it isn't even a proper term.

There are many nvidia cards which suport mpeg4 part 10 aka h.264, but not mpeg4 part 2 aka xvid etc.

Also some nvidia cards do not supoprt some frame sizes.

So install mediainfo and tell us exactly what you are playing.

---

### Post by marek_online on 2012-08-24
I shall delete mpeg4 from my vocabulary so.

I'll look into the mediainfo thing a bit (I can compare the outputs from working and non-working files and hunt out the problem), but I won't waste your time any further on this. Thanks for pointers. The channel thing was the main concern.

---

