---
title: "Extract and joing multiple audio tracks with video"
date: 2010-12-02
forum: Multimedia Software
---

### Post by veroslav on 2010-12-02
Hi all,

I have two video files (Xvid) and would like to combine the video from one of these with the
audio track of the other, in order to create a new video file.

This is somewhat complicated by the fact that I would like the resulting audio to be a mixture
of the two original audio tracks, for instance, during some time segments, I would like to switch from one to the other, but the video should always be the same.

Another issue that complicates the things is that the two audio tracks have different bit rates, and when I briefly managed to merge the two, one of the audio tracks was playing much faster than the other. To clarify, the audio tracks should not overlap but just be played at the different time during the video playback.

I am trying to do this by using Audacity. The problem is that I am fairly new to Audacity and I have not been able to find any info in their user guides regarding this specific issue.

Could anyone here please give me some directions in order to achieve what I am trying to do? Am I on the right track by using Audacity first of all?

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by cchhrriiss121212 on 2010-12-02
Audacity is good for editing audio, you could first convert the audio streams to the same bitrate, then you could try Openshot for putting it all together.

---

### Post by veroslav on 2010-12-02
Thank you for your fast reply, I will have a look at Openshot, I have not worked with that application either.

Regards,
Veroslav

---

### Post by veroslav on 2010-12-02
Two question arise though: if I understand it correctly, Openhot is a video editor and the workflow should be the following:

1. Convert the audio track bitrates to the equal values (Audacity)
2. Cut and joind audio tracks to a single track as necessary
3. Join the new audio track with a video file (Openshot)

Question 1: Would I use Audacity in order to acomplish the second step as well?
This has been the hardset step to do so far, are there any good guides that explain
the process in more detail?

Question 2: I would like to keep the original video file unchanges (no re-encoding).
Is it possible to simply join the new audio track with the existing video track without re-encoding?

Thanks again.

Regards,
Veroslav

---

### Post by cchhrriiss121212 on 2010-12-02
Step 2 is redundant if using openshot as you can add as many audio tracks as you like, but you would have to re-encode. 
To avoid re-encoding you could edit the audio tracks into one file like you said, then add it to the video with avidemux.

---

