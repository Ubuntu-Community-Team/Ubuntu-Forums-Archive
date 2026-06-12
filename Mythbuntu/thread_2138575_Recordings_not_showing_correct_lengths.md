---
title: "Recordings not showing correct lengths"
date: 2013-04-24
forum: Mythbuntu
---

### Post by jlp_engineer on 2013-04-24
I have been noticing over the last few weeks that some recordings are not showing the correct lengths when they are being viewed.  For example, an hour long show may show up as 44:58, or something like that.  This hasn't caused any real distress, as the programs still play in their entirety.  Movies or longer programs also seem to show up with about the same length.  I have also noticed that these programs all seem to be coming from my MPEG2 encoder cards (PVR-150's).  The digital cards seem to be doing alright, and the lengths there are accurate.  Additionally, the analog programs do not seem to be getting comm-flagged, and that seems to have started several weeks ago.  

I have read some older threads that cover this issue, but they do not seem to give a root cause, so I am not sure how to resolve this problem.  I have also read that running mythcommflag as a job on the troubled files corrects the issue, but I have commflag running after ever recording.  It runs on the digital files without an issue, but doesn't seem to run at all (or maybe not successfully) on the analog recordings.

Does anyone have any suggestions how I can identify what is going on?  Is there a solution to the issue?  How do I keep this from happening, rather than fix the files after they are broken (which I would still like to do)?

I am running MythTV 0.25 fixes, from Mythbuntu 12.04 ISO loaded about a year ago on all backends and frontends.

Thanks.

---

### Post by tgalati4 on 2013-04-24
If the ratios of Incorrect/Correct time (in seconds) is the same, then it could be a clock issue--48kHz vs 44kHz sampling for instance.  Does the audio sound normal or is it a higher pitch?  The fix will depend on what the underlying cause is.  Are you using a standard bitrate encoding or variable bitrate encoding?

---

### Post by jlp_engineer on 2013-04-24
> **tgalati4 said:**
> If the ratios of Incorrect/Correct time (in seconds) is the same, then it could be a clock issue--48kHz vs 44kHz sampling for instance.  Does the audio sound normal or is it a higher pitch?  The fix will depend on what the underlying cause is.  Are you using a standard bitrate encoding or variable bitrate encoding?

The audio and video playback is in sync and correct.  The encoding rate is default, whatever that is, as I didn't change it.

---

### Post by BicyclerBoy on 2013-05-02
FWIU The MPEG2 encoder cards output mpeg2 PS.
From my expts/observations.. the myth PS parser misses about 20% of frames.
The duration is calculated by framerate & framecount. 

Try rebuild seektable with:
mythcommflag --rebuild --file <recording-filename>

Check for any errors in the logs..

---

