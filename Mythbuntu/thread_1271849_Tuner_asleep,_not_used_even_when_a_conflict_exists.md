---
title: "Tuner asleep, not used even when a conflict exists"
date: 2009-09-21
forum: Mythbuntu
---

### Post by Clochard on 2009-09-21
I've recently upgraded to trunk and am now finding that one of my tuners has a status of "asleep".  I can't seem to wake it up at all.  As a result my dual-tuner box has become a single-tuner box, and conflicting shows do not wake the tuner up.

I've tried rebooting as that's the only troubleshooting step I've found online.

Is anyone familiar with this "asleep" status for tuners, how it is determined, and how to stop it?

---

### Post by tgm4883 on 2009-09-21
> **Clochard said:**
> I've recently upgraded to trunk and am now finding that one of my tuners has a status of "asleep".  I can't seem to wake it up at all.  As a result my dual-tuner box has become a single-tuner box, and conflicting shows do not wake the tuner up.

I've tried rebooting as that's the only troubleshooting step I've found online.

Is anyone familiar with this "asleep" status for tuners, how it is determined, and how to stop it?

Hmm, not sure about the asleep status. Have you tried deleting it from mythtv-setup and readding it?

---

### Post by Clochard on 2009-09-21
That did the trick - I removed them both, rebooted, and then added them back in.

I don't know how the one came to fall "asleep" but I hope it doesn't happen again - what a pain!

Thanks for the idea.

P.S. I rebooted because I wanted to remove a USB webcam from the mix, as it was coming into the /dev/video area and I think it had shuffled one of the tuners to a new /dev/videoX location but the mythtv backend didn't know about it.  So just to avoid it all I removed it to ensure the /dev/videoX files were fresh and the first ones present.  In retrospect that actually sounds quite plausible, though why it would make the webcam "asleep" and not "broken" I don't know.

---

### Post by TheCook on 2009-11-24
Hello all.  I have just updated to 9.10 with mythbuntu 0.22 on my backend.  I also found that one of my tuners (a Network Recorder) was asleep all the time.  I unloaded it and reloaded it but it was still asleep.  So I tried unloading both my tuners (the second one being a DVB DTV Capture card/USB stick) as suggested above.  BUT now I cannot scan for channels with the Network Recorder.  I have tried using both options to scan ie I set the m3URL to /home/chris/iptv.m3u like I have in the past and then went to scan the channels if I try m3u import nothing happens at all.  If I try to scan for channels, the scan starts and then just sits there.

The m3u file worked before the upgrade and I haven't changed it. I can use VLC to watch the streams so I know they are getting to the box.

Is the inability to use a Network Recorder a known fault with 0.22?  Has anyone managed to get one to work?

---

### Post by OffAxis on 2009-11-24
Would that be the same error in this thread?

[http://ubuntuforums.org/showthread.php?t=1321801](http://ubuntuforums.org/showthread.php?t=1321801)

---

### Post by TheCook on 2009-11-24
:p Thanks for that.  Have moved to that thread.

---

