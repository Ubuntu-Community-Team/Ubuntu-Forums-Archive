---
title: "Multiple Soundcard Recording"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by dbcoolio on 2007-08-12
Okay, I'm fairly new to Ubuntu, but here's what I'm trying to do:  I have 3 sound cards installed in my computer (they all work, I can switch between them and get sound and everything) and a USB Microphone that also works, at least in Audacity.  The idea is that each sound card has its own 2 channel input, and that combined with the USB mic gives a really cheap and fairly decent 7 channel mixer.  Now I just need to get a program that can get the sound from each one at the same time.  I've gotten it to work using Kristal in Windows Vista, but it works like crap and is slow like everything else using Windows on this Computer.  Ubuntu works really well, but I haven't been able to get the sound from more than just one sound card at a time yet.  

in Audacity I can switch between all of them, and they work, but Audacity is more of a single track recording deal anyways.  Kristal seems to be Windows only, even though it is Opensource.  I've tried Ardour- but that requires JACK, and I haven't been able to get that to work right yet, and Traverso and Jokosher both are able to record from one card at a time, but I haven't been able to get them to do more than one at once.  Part of the issue seems like they are just linking directly to ALSA without thinking on their own too much.  Traverso had a place where it showed the availabel Capture Buffers, or something like that, which looked promising but I couldn't figure out how to add more.

Any Ideas?  is there a way to have more than one instance of ALSA running at the same time? that's one idea I had, but I have no Idea how to set it up, I'm not very good with the Terminal yet anyways...

---

