---
title: "Problem With sound after compileing32bit Mplayer of 64bit system"
date: 2008-10-03
forum: Multimedia Software
---

### Post by XxsydenxX on 2008-10-03
Hello i recently tried to compile 32bit Mplayer on my 64bit kubuntu 7.10
I did it following this Tutorial, [http://ubuntuforums.org/showthread.php?t=62685](http://ubuntuforums.org/showthread.php?t=62685)

I however failed.

It was giving some odd reading saying it could not overwrite some files...so i decided to look further into the topic...and somone posted.

dpkg -i --force-all mplayer32_1.0pre6-1_amd64.deb


after i did that i still couldnt get the damn thing working...And then my Sound for videos on like youtube are completely screwed up.

Yes i am a complete starter....could someone please fix this problem????

---

### Post by cariboo on 2008-10-04
You did notice that the howto is three years old. This issue has probably been fixed in newer versions. I'm running Intrepid Beta and have no problems playing wmv9 files without resorting out of date howto's. You might want to try and uninstall the mplayer32 deb. then run in a terminal:

```
sudo dpkg-reconfigure -a
```

This might work to get your sound working again.

Jim

---

