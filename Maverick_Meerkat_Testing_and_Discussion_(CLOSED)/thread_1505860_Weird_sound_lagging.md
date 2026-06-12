---
title: "Weird sound lagging"
date: 2010-06-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by clivejo on 2010-06-09
Recently, Ive noticed that I seem to be having a strange lag of 30secs or more on my sound.  For example when I listen to an mp3 and skip the current track, Rhytmbox displays a notification telling me of the next song, however I can still hear the current song for some time after.

Also, if I hit the mute button, the sound continues for a bit after.

Anyone experience the same thing or know what might be causing it?

---

### Post by LiquidMeson on 2010-06-09
&#8623;

---

### Post by LiquidMeson on 2010-06-09
*sigh...why did I not just edit the comment above...*


**Problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/556727](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/556727) ?**

---

### Post by clivejo on 2010-06-09
To add to the strangeness I seem to have two audio controllers, a lspci lists these.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

But why have I only just started to have problems, 10.04 works fine and did during development.  :confused:

---

### Post by hemantborole on 2010-06-09
I have a slightly similar problem. I dont get lagging, instead i keep hearing echoes, lotsa them.
Here is how you can replicate it

MacBook Pro 5x
Ubuntu Lucid lynx
Run youtube in firefox. While some video is running, shut down the flap. After a few minutes ( or even hours, this replicates 100% ), open the flap, continue to play the video. Now what you hear (or i heard) is something i cannot express in words. The closest word probably is echo.

---

### Post by clivejo on 2010-06-09
> **LiquidMeson said:**
> *sigh...why did I not just edit the comment above...*


**Problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/556727](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/556727) ?**

Tried the solution on this bug report and appended noapic to kernel options, no change however.

---

### Post by cariboo on 2010-06-09
> **clivejo said:**
> To add to the strangeness I seem to have two audio controllers, a lspci lists these.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

But why have I only just started to have problems, 10.04 works fine and did during development.  :confused:

Do you have a Nvidia video card with HDMI out?

---

### Post by clivejo on 2010-06-10
Yes I do, do you know what's wrong?

---

### Post by cariboo on 2010-06-10
That's why you have two audio devices showing. Check in Sound preferences to make sure only the Intel device is selected, if you aren't using HDMI for sound output.

---

### Post by clivejo on 2010-06-12
Selected the Intel sound device but still having problems with lagging sound.  Anyone got a found the problem and/or a solution?

---

