---
title: "no center audio for some shows"
date: 2009-11-27
forum: Mythbuntu
---

### Post by daninca on 2009-11-27
Since I installed mythbuntu 9.10, some shows don't have any center audio channel.  The music effects are there, but the dialog is missing.

Most CBS prime time shows are like this and some NBC.  Sometimes the commercial are fine, while the show is missing the dialog.  The other networks are fine (usually).  All show are recorded in digital hidef over the air.

I'm feeding analog 5.1 from the computer to the amplifier.  The audio is setup as alsa:surround with "max channels" set to 5.1.  Setting "max channels" to stereo gives me back the dialog, but what's the fun in that?

This was working fine under 9.04, but I did a fresh install while I was doing some hardware changes.  If it matters, I actually installed 9.10-beta and then updated from there.

Thanks,
-Dan

---

### Post by jaakan on 2009-11-29
> **daninca said:**
> Since I installed mythbuntu 9.10, some shows don't have any center audio channel.  The music effects are there, but the dialog is missing.

Most CBS prime time shows are like this and some NBC.  Sometimes the commercial are fine, while the show is missing the dialog.  The other networks are fine (usually).  All show are recorded in digital hidef over the air.

I'm feeding analog 5.1 from the computer to the amplifier.  The audio is setup as alsa:surround with "max channels" set to 5.1.  Setting "max channels" to stereo gives me back the dialog, but what's the fun in that?

This was working fine under 9.04, but I did a fresh install while I was doing some hardware changes.  If it matters, I actually installed 9.10-beta and then updated from there.

Thanks,
-Dan


what other settings do you have on the channel settings screen?

if "stereo gives me(you) back the dialog" Downmixing of AC3(DD5.1) to stereo is working correctly.

Have you Tried changing the number channels to say 5.0? Do you have a Sub?

---

### Post by daninca on 2009-11-30
With alsa set to "surround51" the only channel options it gives me are 5.1 and stereo.  

I don't have a subwoofer, but the amp is configured to mix that into the main speakers (which are big enough to handle it).  So it looks like 5.1 to the computer.

I used alsamixer and made sure it was configured in 6 channel mode (vs. 8) and with all the output channels full up.

I haven't tried any other alsa modes besides "surround51".  The fact that some shows are fine suggests that it isn't completely wrong.  I'm not sure what all the other modes are supposed to do.

-Dan

---

### Post by daninca on 2009-12-03
I side stepped the issue by getting SPDIF working.  Now the audio goes straight to the amp and it does the decoding.

-Dan

---

