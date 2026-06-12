---
title: "DVD error handling"
date: 2011-05-07
forum: Mythbuntu
---

### Post by chrism0dwk on 2011-05-07
Hi All,

I'm having a problem with Mythvideo DVD playback in Mythbuntu 10.10 with MythTV-Updates and Mythbuntu-Updates configured (ie mythtv 0.24).  Essentially, despite being a little jittery the DVD playback does not seem tolerant to fault on the DVD disc.  For a given faulty disc, the result is that playback simply exits at a certain (and consistent) point while watching the movie.

I have compared this to playback on my Mac, which works smoothly, and doesn't appear to notice the disc defect, and also with VLC (running on the mythbuntu box) which appears simply to skip a frame and carry on.  Thus I think I can rule out a) that the disc is completely unplayable, and b) that it's not a hardware issue.

My Mythbuntu box is configured to use VDPAU High Quality, and changing the quality (or disabling VDPAU altogether) does not make a difference (besides degraded screen quality). I am using a Sony BC-5500H-01 Bluray slimline combo drive, with an AT3IONT-I deluxe mobo.

I have attached the log that I get from > mythfrontend -v playback, and you will see the error messages towards the end.  

Questions:

1) are there any playback settings I could change in order to improve things?  Increasing the size of the playback buffer to allow disc re-reading somehow?

2) Is there a workaround?

3) is anybody else experiencing this issue?

I think this is important to get right, as most DVDs that come from rental stores have seen better days, and fault tolerance is therefore required.

Cheers,

Chris

---

