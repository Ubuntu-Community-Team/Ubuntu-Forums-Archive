---
title: "Pink noise generator for maverick?"
date: 2010-12-05
forum: Multimedia Software
---

### Post by leptogenesis on 2010-12-05
It seems that everything in the repos either relies on jack audio, which I can't get to work on my system (jnoise and japa), or crashes on startup (gnusound).  Before Maverick, I was using a program I found on the internet, but Maverick seems to have removed the support for OSS which that program relied on.  There must be a pink noise generator that works with pulseaudio...but I just can't find it.

---

### Post by mc4man on 2010-12-05
If you can't find anything - Don't know how you start/run your previous app but you could try prepending it's launch command or in a terminal w/ - 
padsp

---

### Post by idi0tf0wl on 2010-12-05
I felt bad for you, so I wrote you a pink noise generator in Java just now. Where can I send you a jar file?

---

### Post by leptogenesis on 2010-12-05
Thanks for the replies!

> **mc4man said:**
> If you can't find anything - Don't know how you start/run your previous app but you could try prepending it's launch command or in a terminal w/ - 
padsp

Tried that--the app crackles unpleasantly if run with padsp.  :-(

> **idi0tf0wl said:**
> I felt bad for you, so I wrote you a pink noise generator in Java just now. Where can I send you a jar file?

Can't you attach it here?  Make sure you include the source or I'm not going to run it ;)

Though it would be even better if you could get your code into the repos--people shouldn't have to write programs whenever they find they need them.

---

### Post by idi0tf0wl on 2010-12-05
That should do it. That's what I threw together on a kick. You should be able to do plenty with it if you read the code. Java is pretty nice.

Have fun!

Edit:
I should mention: you'll be best served to run that in a terminal, as there is no GUI for what I put together here. You should be easily able to add GUI to start and stop it and be able to adjust certain parameters to your liking. Cheers!

---

### Post by idi0tf0wl on 2010-12-06
OK, so I had a bit of free time just now and for some reason decided to use it to throw together a UI for that little pink noise generator I wrote you. Source code's still all there, too, so have no fear.;)

I really don't have any need for a pink noise generator, though, so don't expect me to ever touch this again. If it works for you (perhaps albeit imperfectly) and you want to make it able to do more things or give it to more people, that's all on you.

Cheers!

---

### Post by leptogenesis on 2010-12-13
I can't get it to work.  Your GUI shows up and I can enter values, but no sound is played.  Other apps can play sound just fine, so I know it's not my system.  However, I don't have enough java audio experience to fix the code.

Clicking to stop throws an exception:

```

SEVERE: pinknoisegui.PinkNoiseGUIView$PlayTask@10cbd8dc failed: java.lang.ArrayIndexOutOfBoundsException: 2730
java.lang.ArrayIndexOutOfBoundsException: 2730
        at pinknoisegui.StdAudio.play(StdAudio.java:100)
        at pinknoisegui.PinkNoiseGUIView$PlayTask.doInBackground(PinkNoiseGUIView.java:293)
        at org.jdesktop.swingworker.SwingWorker$1.call(Unknown Source)
        at java.util.concurrent.FutureTask$Sync.innerRun(FutureTask.java:303)
        at java.util.concurrent.FutureTask.run(FutureTask.java:138)
        at org.jdesktop.swingworker.SwingWorker.run(Unknown Source)
        at java.util.concurrent.ThreadPoolExecutor$Worker.runTask(ThreadPoolExecutor.java:886)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:908)
        at java.lang.Thread.run(Thread.java:662)
Dec 13, 2010 11:25:22 PM org.jdesktop.application.Task failed
SEVERE: pinknoisegui.PinkNoiseGUIView$PlayTask@758689a failed: java.lang.ArrayIndexOutOfBoundsException
java.lang.ArrayIndexOutOfBoundsException
```

---

### Post by idi0tf0wl on 2010-12-14
> **leptogenesis said:**
> I can't get it to work.  Your GUI shows up and I can enter values, but no sound is played.  Other apps can play sound just fine, so I know it's not my system.  However, I don't have enough java audio experience to fix the code.

Clicking to stop throws an exception:

```

SEVERE: pinknoisegui.PinkNoiseGUIView$PlayTask@10cbd8dc failed: java.lang.ArrayIndexOutOfBoundsException: 2730
java.lang.ArrayIndexOutOfBoundsException: 2730
        at pinknoisegui.StdAudio.play(StdAudio.java:100)
        at pinknoisegui.PinkNoiseGUIView$PlayTask.doInBackground(PinkNoiseGUIView.java:293)
        at org.jdesktop.swingworker.SwingWorker$1.call(Unknown Source)
        at java.util.concurrent.FutureTask$Sync.innerRun(FutureTask.java:303)
        at java.util.concurrent.FutureTask.run(FutureTask.java:138)
        at org.jdesktop.swingworker.SwingWorker.run(Unknown Source)
        at java.util.concurrent.ThreadPoolExecutor$Worker.runTask(ThreadPoolExecutor.java:886)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:908)
        at java.lang.Thread.run(Thread.java:662)
Dec 13, 2010 11:25:22 PM org.jdesktop.application.Task failed
SEVERE: pinknoisegui.PinkNoiseGUIView$PlayTask@758689a failed: java.lang.ArrayIndexOutOfBoundsException
java.lang.ArrayIndexOutOfBoundsException
```

Oh it works for me... Pink noise will play if you enter nothing. For the alpha level you have to be sure you're not entering a value between 0 and 1 - any decimal value will work. Will it play with blank input fields?

---

### Post by leptogenesis on 2010-12-15
Ah, I see.  If I run the app in netbeans no sound plays, but if I just run it via java -jar the sound works.  That's fine by me.

However, it still doesn't sound quite right.  It's okay for values between 0 and 1, but those alpha values aren't red enough for me.  I'd like it if it worked for alpha=2.  When I try alpha around 1.5 it sounds a bit like tearing paper, and when I try alpha=2 I get random clicks and pops.  Printing the actual values being piped to the sound card, I find that the values are diverging.  The odd sounds, then, must be due to oversampling.  

With alpha=2, I see that the multipliers array ends up being all zero except for one -1 value for the first entry.  This means the output is equivalent to a sum of gaussians of equal variance.  Nothing is decaying.  I think you have a formula wrong in here somewhere...

EDIT: No wonder:  

[QUOTE="Kasdin (1995)"]The process defined by (97) is nonstationary (for alpha > 1) and self-affine...[/QUOTE]

So this code can't be plugged directly into your GUI to get red noise unless you're okay with alpha less than or equal to 1.

EDIT 2: Swapped out the original filter for a plain old Gaussian low-pass filter and now it does what I want.  Thanks for all your help idi0tf0wl!

---

### Post by idi0tf0wl on 2010-12-15
I misposted. It was indeed built to take an alpha of up to two, as you discovered. I'm very pleased to hear you now have what you were looking for! Could you please post your changes back up here so I (and perhaps even others) can study it?

I don't need pink noise, but knowing the best way to make it happen is nice.

Thanks!

---

### Post by leptogenesis on 2010-12-19
Actually, I tried leaving the gaussian-filtered pink noise on overnight (I'm not using this for anything profound--just masking background noise in my apartment while I'm trying to sleep) and eventually I had to turn the volume down because it bothered my ears.  I've tried replacing my original filter with a Blackman filter (which is what my original program used), and the resulting sound isn't nearly as good, especially for low cutoffs.  

Anyway, you can see the other program I'm using here:

[http://linux.softpedia.com/get/Multimedia/Audio/whitenoise-15803.shtml](http://linux.softpedia.com/get/Multimedia/Audio/whitenoise-15803.shtml)

I've also attached my attempts to hack something together.  However, I tried the padsp solution again today and discovered that it works now for some unfathomable reason, so I guess I'm set anyway.

---

### Post by mc4man on 2010-12-20
> it works now for some unfathomable reason
Occasionally have that occur here, sometimes try to figure out, other times figure better to leave well enough alone. (unless it reverts
Currently have a dvd drive that disappears when a commercial dvd is inserted unless an audio cd is inserted/ejected once per session, then it's fine. On a laptop I have some terminal behavior that atm should not be possible,..

---

### Post by idi0tf0wl on 2010-12-20
Well I'm glad the situation turned out well for you! I thought you needed pink noise... but hell, as long as what there was wrong is now solved, it's all good gravy, right? Many peaces.

---

