---
title: "tearing my hair out with audacity"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by th3james on 2007-07-25
I'm trying to record with audacity, while also playing back existing tracks at the same time, however, i always get this message:

Error while opening sound device. Please check the input device settings and the project sample rate.

It's fine when there is no other audio tracks along side it, but as soon as i try 2 record over a previously recorded track, that message pops up. I'm running audacity with aoss, cuz i had a high pitched whine without, and i have the same problem with both the version in the repos and the compiled beta.
My prefernces are set as such:

playback: OSS /dev/dsp
recording: OSS /dev/dsp
mono(1)

play other tracks when recording new one: ticked (if i untick, its fine, but i really need the functionality)
software playthru: unticked (althou ideally it would tick it, but it doesnt work)

Any suggestions how to fix it? I don't mind trying other software, I'd love to use jokosher cause it seems really good, but i can't gstreamer to record...

thanks in advance

---

### Post by aysiu on 2007-07-25
There's a bug report on this:
[https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/105733](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/105733)

---

### Post by th3james on 2007-07-25
thanks for the link, but i think thats a differnt issue to mine, i only get problems when trying to playback and record at the same time, playback and recording are fine otherwise. this did work previously, i did install fluxbox this morning... i wonder if that had anything to do with it, the launchpad bug report talked about kde messing, so maybe fluxbox does 2? i doubt it thou, cuz KDE is quite a bit more complex...

---

