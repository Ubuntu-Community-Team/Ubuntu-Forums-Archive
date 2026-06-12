---
title: "Capturing with HDHR, some files (KYW/WCBS) do not contain PCR"
date: 2011-02-01
forum: Mythbuntu
---

### Post by sdevine01 on 2011-02-01
Hi,

I am trying to record my local CBS station and play the file back in VLC.  It seems to display part of the first frame and then stops playback.  MythTV playback is choppy and the lipsync is off.

I ran the recording through a transport stream analyzer, and it flagged an error that the PID signaled with the PCR does not actually contain any PCR information.  I believe MythTV is filtering out this data out, and I'd like it not to :-).

If I record the channel using TSReader's HDHomeRun plugin, I see PCR and VLC playback works.  I've attached a txt file showing a DVBSnoop of where the PCR is located in this particular stream - I think its an older way of doing it, but compliant.  8VSB or QAM seems to makes no difference.  ABC/NBC/FOX record and playback fine (PCR is present).

I'm using Ubuntu 10.10 x86 with what I believe is the nightly build of mythtv (2:0.24.0+fixes.20110201.14bfdc3-0ubuntu0mythbuntu2) from a mythbuntu repository.

- Sean

---

