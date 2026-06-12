---
title: "Sound Recording Issues"
date: 2007-09-27
forum: Multimedia Production
---

### Post by aristotlewilde on 2007-09-27
I am hoping someone can help me out here.

I built my new dedicated Ubuntu box today.  I am in the midst of getting things configured to my liking, but noticed an odd sound issue.  

When I record via Sound Recorder or Gizmo, sound is fine.  In Audacity, it sounds funky.  

Please take a moment and listen to the two files I have attached here.  It illustrates my issue.

I am recording directly thru a headset (not USB).

Using the Realtek OSS mixer.

This is by no means urgent, but heck, I'd like my stuff to work well.  I am sure it is a matter of me not having Audacity set up right...

---

### Post by aristotlewilde on 2007-10-01
As an update, I still have not located a fix.  

To muck it up more, I am having similar sound issues when I try capturing audio from a stream (w/ Sound Recorder or Audacity).  Outputted file is all loud and distorted.

I am wondering if since it all works thru the mic in Sound Recorder and totally in VOIP, that I just have settings wrong.  

I'll do more tweaking and testign tonight, but am just about ready to pickup a soundcard at this point.  Does anyone have anything to offer on this help wise?

---

### Post by aristotlewilde on 2007-10-01
For anyone interested in helping, or anyone with similar issues, the Audacity recording from mic issue has been solved by changing the Sample Rate to higher quality.  

I am still working on the Capture from audio out portion.  

Anyone have thoughts?

---

### Post by dabl on 2007-10-02
Couple of random thoughts (I didn't listen to your file, only read your posts):

1. Why OSS and not ALSA -- does ALSA not offer what you need?

2. With Audacity, did you try using its controls, or only the system mixer controls?

3. You say "changing the sample rate to higher quality", but what does that mean?  44,100 to 48,000?  16-bit to 32-bit?

Just wondering how you're doing what you're doing.  :)

---

### Post by aristotlewilde on 2007-10-02
I actually have it on ALSA.  

In Audacity, I changed it to 96,000 to make it work.

---

### Post by dabl on 2007-10-02
> **aristotlewilde said:**
> 

In Audacity, I changed it to 96,000 to make it work.

Interesting -- I wouldn't have guessed that would make a discernible difference.  Thanks!  :)

---

### Post by distort on 2007-10-19
That problem seems familiar.
I have fought several times and on various platforms with Audacity, with no success.
I ended up using Rezound for recording.

---

