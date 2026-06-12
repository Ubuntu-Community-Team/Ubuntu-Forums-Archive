---
title: "Sound Blaster Live 24-bit fighting with AC97 Motherboard"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by botulismo on 2007-08-12
So I've been using Ubuntu for almost a year now, and I'm still have a mysterious problem from the very beginning that I'd like to have solved.

I have a Sound Blaster Live 24-bit PCI sound card, currently residing outside of my computer, and an integrated AC97 Sound Board. The reason the PCI card lives outside of the computer is that whenever I have it in, no matter what I do, it will not work properly 100% of the time.

The culprit? Honestly, certain times when my OS boots, it won't believe that the PCI card is the true sound card. It sounds weird, I know, but I've gone as far as to specify it in the Sound applet, BY NAME, and yet somehow it manages to randomly change the setting back to the AC97, or autodetect, or whatever. Autodetect only seems to work about half of the time, so I can reboot and sometimes hear the Ubuntu login music.

Sometimes, too, I'll hear the Ubuntu login music, only to find that flash player can't make any audio. What is that? Usually when that's the case, I'll still be able to listen to mp3s. I reboot, and usually it works fine. Till next time. 

So, my solution was to just eliminate the conflict of interest. This has worked perfectly, but honestly I prefer the other sound card because it has surround sound capabilities. It worked beautifully in Windows, but for some reason in Ubuntu it's a strange combo.

I can't shut the integrated audio off in the BIOS. I have tried, but Gateway will simply not allow it.

I know a lot of this seems confusing, but this is the honest truth. I have no idea why Ubuntu could figure out how to play an mp3 (PCM data when it goes through the sound card) but not flash (also PCM data) all on the same boot. But it's very, very annoying.

Is there something I can just do in a command line file that dictates to Ubuntu once and for all that this is the sound device it's using and if it doesn't like it, tough?

---

### Post by botulismo on 2007-08-12
How about this. Is there any way to just disable the AC97? I think that would solve the problem. Any idea how I would go about that? Where are the drivers located - could I just delete them?

---

