---
title: "Playback Freezes with poor reception recordings"
date: 2010-10-05
forum: Mythbuntu
---

### Post by Digicrat on 2010-10-05
I am experiencing periodic freezing of the mythfrontend ever since applying the 10.04 upgrade over the summer.  CPU usage becomes pegged at 50-52% (dual-core CPU) until I explicitly kill mythfrontend.  It always occurs at a specific point(s) in recordings, and can only be avoided by skipping past the known bad spot after restarting the frontend.  

So far, this behavior has only happened to me on ATSC/OTA stations where there are signal issues (compared to my QAM tuner, which only receives a handful of the OTA-HD stations...).  It will happen often on recordings with severe signal problems (aka stuttering/skipping every few minutes), and occasionally on better recordings as well. 

Prior to the 10.04 upgrade, I never had myth crash on me like this and troubled recordings would simply skip forward or distort audio at points of signal loss.  

In the past, logs for similar recordings have shown large numbers of errors such as "invalid frame". Ever since the 10.04 upgrade however, the mythfrontend.log file is no longer being generated.

On a possibly unrelated problem, since the 10.04 upgrade, my 5.1 sound has also decided that it only wants to work if I first open VLC and play something for 1/2 a second, outside of Myth, after startup...  


Any ideas?

Thanks,
- David

---

