---
title: "How do I record from my webcam?"
date: 2010-04-27
forum: Multimedia Software
---

### Post by stinkinrich88 on 2010-04-27
Hello,

I purchased a webcam to record videos with in Ubuntu. I plugged it into the USB slot (and audio into the mic hole) and it seems to work ok. But I'd like to record a video from it and save it to a file. How can this be done?

I tried Cheese and no audio was recorded.
I tried GUVCView and it was fine except for slow video & audio delay.
I can't find any other programs for recording webcams on Linux.

Thanks,

Rich

---

### Post by no2498 on 2010-04-27
read and install what the page tell you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope this helps

---

### Post by WinterRain on 2010-04-27
Or, if your cam is /dev/video0 for example, you can

```
cat /dev/video0 > ~/Desktop/movie.mpg
```

---

### Post by stinkinrich88 on 2010-04-27
Thanks for the replies, guys.

wxcam was hard to install (on 64bit) and it can rarely find my webcam. When it does, it recorded the video with no sound. It's probably recording the wrong channel (like Cheese) but I can't find a way to set it (on either program).

The "cat..." command didn't work. It says "no such device" even though there is such a device (my webcam is /dev/video0).

Any more ideas?

---

### Post by no2498 on 2010-04-28
webcams 9 out of 10 times record avi file types
hope this helps

---

### Post by robertbub on 2010-12-04
Was this ever resolved?  I seem to have the same problem.  Guvcview correctly records video and sound, but the sound quality is terrible (at least, compared with "arecord test.wav").  Cheese doesn't have any audio.  And, AFAICT, wxcam doesn't record any sounds, either.

If I can find a way to do either of the below, I would be happy:[LIST=1]
[*]**Cheese**.  Get sound recording to work and have it be of a higher quality than guvcview.
[*]**Guvcview**.  Improve the sound quality to be at least as good as "arecord".
[/LIST]
Thanks.

---

### Post by stinkinrich88 on 2010-12-04
Hi rob, 

I haven't made any more attempts since my last post. It didn't look like I'd get anything working anytime soon.... good luck, though!

---

### Post by no2498 on 2010-12-05
just seen this yesterday

[http://u8untu.blogetery.com/2010/08/26/getting-wxcam-working-with-lucid/](http://u8untu.blogetery.com/2010/08/26/getting-wxcam-working-with-lucid/)

---

### Post by gordintoronto on 2010-12-05
> **stinkinrich88 said:**
> Hello,

I purchased a webcam to record videos with in Ubuntu...
I tried Cheese and no audio was recorded.
I tried GUVCView and it was fine except for slow video & audio delay.
I can't find any other programs for recording webcams on Linux.


Cheese works fine for me.

In Preferences/Sound, how many inputs are there? Does Sound Recorder record sounds?

Have you checked whether the microphone is muted? That is a common default.

Is this a slow computer?

---

### Post by robertbub on 2010-12-06
> **gordintoronto said:**
> In Preferences/Sound, how many inputs are there?3 --[LIST]
[*]Line-In
[*]Microphone 2
[*]Microphone 1
[/LIST]Only Microphone 2 seems to work.  (I assume that that is the built-in mic, which is what I'm using.)
> **gordintoronto said:**
> Does Sound Recorder record sounds?Yes, via Audacity.  The sound quality is very crappy -- lots of hiss and it sounds like I'm in a tunnel.
> **gordintoronto said:**
> Have you checked whether the microphone is muted?Yes, it is not muted.> **gordintoronto said:**
> It is not.That is a common default.

Is this a slow computer?No.  This computer (laptop with a built-in mic) was bought brand new earlier this year.

---

### Post by gordintoronto on 2010-12-06
> **robertbub said:**
> Only Microphone 2 seems to work.  (I assume that that is the built-in mic, which is what I'm using.)
Yes, via Audacity.  The sound quality is very crappy -- lots of hiss and it sounds like I'm in a tunnel.

This computer (laptop with a built-in mic) was bought brand new earlier this year.

Any chance you can try another microphone? It should sound good.

There are slow laptops being sold this year. You might have mentioned the spec for the CPU.

My preference is to use a headset with earphones, and a microphone which sits right in front of my mouth. I'm happy with the results.

---

