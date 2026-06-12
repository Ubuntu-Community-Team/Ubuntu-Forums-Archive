---
title: "k9copy fails on MPEG-4 after upgrade to 9.10"
date: 2009-11-05
forum: Multimedia Software
---

### Post by bkann on 2009-11-05
Hi -

I have been using k9copy without problems in 8.04 since Hardy was fairly new.

I recently upgraded from 8.04 to 9.10 (8.04 -> 8.10 -> 9.04 -> 9.10) and everything seems all right with the one exception of encoding MPEG-4 videos from a DVD in k9copy.  I can still rip DVDs to folders, MPEG-2, etc., but when encoding to MPEG-4 the software just runs the process up to 99% complete and then "hangs" in an unusual way.

When the process hangs, the software continues to act like it's working in that it updates the expected completion time/total time, but just never finishes.  The processor pegs at 100% and I have to kill it from the command line.  No video file is ever created and video is never displayed to the screen.

I upgraded sequentially and quickly, so I did not spend much time with the in-between versions, so I can not say whether or not this would have happened in 8.10 or 9.04.

Has anyone experienced this behavior either before or after 9.10?

Thanks for any help!

---

### Post by saechen on 2009-11-05
It worked fine in 9.04, but I am having a similar problem ripping to ISO in 9.10. Loads fine, but when to start copy crashes.

Here is the crash info:
Application: k9copy (k9copy), signal: Segmentation fault
[KCrash Handler]
#5  0x01d6cac0 in QString::operator=(QString const&) () from /usr/lib/libQtCore.so.4
#6  0x080c5e61 in _start ()

---

### Post by saechen on 2009-11-05
I was able to get it to work using the k9copy assistant. Give that a try and see if works for you.

---

### Post by bkann on 2009-11-05
Thanks, and I'm glad you got it to work.  I hadn't thought about trying the Assistant.  Unfortunately, that didn't work for me.

Also unfortunately, I don't have a crash log to post because it doesn't crash; it just continues to run indefinitely.

I'm not too up on the multimedia apps in Ubuntu, so I don't know if this these are interrelated of if this is even meaningful:  when I start up K3b it just sits there with the 'busy' mouse cursor.  That's a new one for me in 9.10, too.  Also, for what it's worth, I had some trouble getting the adobe-flashplugin package to work properly when I upgraded, but I think I got that all straightened out.

Thanks again.  Happy to try any other suggestions.

---

### Post by saechen on 2009-11-05
Not that I am remotely close to being an expert :-), but it sounds like if K3b is having a problem as well something else is going on. When you put a DVD in the drive can you play it ok?

---

### Post by bkann on 2009-11-05
No problems playing DVDs.  No problem ripping them to ISO, into a folder, or even MPEG-2's.  It's only the MPEG-4 avi's that are giving me trouble.

I agree that it's something deeper than k9, and while my guess would be a problem with the XVid encoder, I have no idea what to do with that hunch.

I have reinstalled ubuntu-restricted-extras and that didn't help.

---

### Post by mc4man on 2009-11-06
Don't use k9 or the various semi-neutered karmic mplayer, mencoder, ffmpeg libs but take a look at your mencoder (what k9 uses for encoding.

Unlike previously, in karmic, mplayer and mencoder depend on the system installed libavcodec which has stripped and extra versions.

The extra version has a depend of libxvidcore4 so possibly look there also.

( note that installing the ubuntu-restricted-extras doesn't enable the extra versions of the ffmpeg libs, quite the opposite, it will remove them

---

### Post by lwcary on 2009-11-14
> **mc4man said:**
> Don't use k9 or the various semi-neutered karmic mplayer, mencoder, ffmpeg libs but take a look at your mencoder (what k9 uses for encoding.

Unlike previously, in karmic, mplayer and mencoder depend on the system installed libavcodec which has stripped and extra versions.

The extra version has a depend of libxvidcore4 so possibly look there also.

( note that installing the ubuntu-restricted-extras doesn't enable the extra versions of the ffmpeg libs, quite the opposite, it will remove them

*****  Installing the above-mentioned libraries made K9 copy work OK for me. *****  ;)

---

