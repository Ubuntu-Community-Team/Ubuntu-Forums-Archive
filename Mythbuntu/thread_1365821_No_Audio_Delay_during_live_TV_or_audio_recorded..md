---
title: "No Audio Delay during live TV or audio recorded."
date: 2009-12-27
forum: Mythbuntu
---

### Post by neanderthalman on 2009-12-27
Hi all,

I've been trying to get my mythbuntu PVR working again, and I'm having an issue with the audio on live TV.  It appears to me that the audio from the TV tuner is somehow being sent directly to the sound card, rather than being processed by mythTV.

I'm not even sure which side needs a smack.  The audio from the TV tuner depends on a cable from the tuner card to the onboard sound card (CD audio connector).  I don't think there should be any compatibility problems, as this entire system was once working (minus the video card), and the video appears to be playing fine.  I know I'll probably regret saying this, but how can the new video card possibly cause a problem with the audio?

Any suggestions on where I should look would be appreciated.  I've been searching all afternoon and haven't found anyone with the same kind of problem.




TL,DR description:

I had it working a while back using 8.10.  My wife wanted a video card upgrade so she could play a game (dual boot XP), and so the PVR languished for a few months.

When I decided that I wanted to use the PVR again, I found that mythtv was no longer reading live TV.  Turns out I was chasing my tail, as the issue was that I had disturbed the TV tuner card.  Should have checked it first, but by this point I had already blown away 8.10 and tried out 9.10, then reinstalled 8.10.

So now I was back at square one, using 8.10, and after reseating the tuner, it was recognized and worked!

Except, that now there's a very large discrepancy between the video and sound.  About two seconds.  Now, my understanding is that mythTV normally works by recording the TV signal, then playing it back - introducing a delay of about two seconds.  There's that "two seconds" thing again.

Questioning whether it was the new video card, I figured at this point I was probably better off putting 9.10 on it *again* to see if that would fix the problem.  It changed nothing, but it *is* prettier.

So, to experiment, I tried a few things.  First, I checked to see if video files would play normally - and they do.  They will also play from within mythTV.  I tried recording live TV and playing it back, but the recordings have no audio at all.  Finally - and I think this is the most telling sign - I loosened the coaxial cable input, and with live TV playing, I disconnected the signal.  The audio immediately ceased, but the video continued to play for....two seconds.

---

### Post by neanderthalman on 2009-12-28
Figured it out.  Had to set the CD line to "capture" using alsamixer, then mute it.  The ubuntu alsamixer manpage was indispensable.

---

