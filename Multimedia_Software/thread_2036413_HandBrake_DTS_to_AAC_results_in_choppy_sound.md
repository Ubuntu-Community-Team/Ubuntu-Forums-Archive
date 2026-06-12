---
title: "HandBrake: DTS to AAC results in choppy sound"
date: 2012-08-01
forum: Multimedia Software
---

### Post by MrsUser on 2012-08-01
I use Handbrake to convert some HD MKV movies to lower resolutions. I also convert the audio tracks to AAC. Everything is fine when the audio source is AC3. But if it's DTS, the result is a sound that has every few seconds a gulp, so that it's kinda choppy.

So I looked for an alternative way to separately convert the DTS track to AAC, but couldn't find anything. Basically, I'm looking for a solution with GUI. I don't want to spend my time in terminal with command lines. It should be quick and easy.

Or does anyone know what the problem is with Handbrake? In Windows, I never experienced any problems. It's only with Ubuntu, even on a fresh install.

---

### Post by MrsUser on 2012-08-25
Latest HandBrake update seems to have fixed the problem. No more choppy sound when converting from DTS to AAC -- so far. At least, my recent encoding was fine.

Update:
Still no problems with DTS to AAC. Have tried various DTS tracks in MKV files. Problem is definitely fixed.

---

### Post by MrsUser on 2012-09-11
Oh, great. The problem is back :-(

Again, Handbrake converts DTS to choppy AAC or AC3, no matter what. Doesn't matter if faac or ffmpeg. Now I'm looking for an alternative to transcode the DTS track externally.

---

### Post by MrsUser on 2012-10-02
Installing Handbrake from Snapshot repos fixed the issue.

---

### Post by LancerNZ on 2013-01-23
And now it's all choppy again... damn this is such an annoying issue where the end user is left completely at the mercy of the devs who keep breakng things.

Well... maybe a little, from playing around if I change the audio codec of the input stream (the movie going into handbreak) to PCM, then handbrake seems to be able to convert the video without breaking the sound.

---

### Post by JohnAStebbins on 2013-01-24
> **LancerNZ said:**
> And now it's all choppy again... damn this is such an annoying issue where the end user is left completely at the mercy of the devs who keep breakng things.

Well... maybe a little, from playing around if I change the audio codec of the input stream (the movie going into handbreak) to PCM, then handbrake seems to be able to convert the video without breaking the sound.

Hi,

Have you ever visited the HandBrake forums?  Possibly you haven't so I will clue you in on something.  They require that you post an activity log in order to get support.  Support requests without an activity log are summarily rejected.  The reason for this is an activity log answers all the questions that one would have to ask in order to help you with your problem.  The information you have supplied so far is just inadequate.

As far as breakage of DTS->anything conversions in the snapshots, I apologize for that.  That was my fault.  Broke it in the process of trying to help a user that had a rather unusual DTS stream.  But all those issues should be resolved now [-o<

---

