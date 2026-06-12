---
title: "mplayer streaming"
date: 2010-03-10
forum: Multimedia Software
---

### Post by supradave on 2010-03-10
I have a nice little setup where I stream various radio programs during the day.  Two are nice little MP3 streams and one is a Windows ASF stream.  The ASF stream works fine and I get what I want but the file is 1.5 GB for a 3-hour program.  

Here's my command:
```
/usr/bin/mplayer -really-quiet [http://site.com/stream?MSWMExt=.asf](http://site.com/stream?MSWMExt=.asf) -ao pcm:noblock:fast -ao pcm:file=FILE.wav -vc null -vo null
```

Are there any flags I can give to make that file a bit smaller, as in the 300MB range?  I don't need quality because it's a talk program.

Thanks,
Dave

---

### Post by andrew.46 on 2010-03-10
Hi supradave,

> **supradave said:**
> Are there any flags I can give to make that file a bit smaller, as in the 300MB range?  I don't need quality because it's a talk program.

I believe not, this is the nature of saving to pcm, usual practice is to then convert to another format such as ogg or mp3 which will be a lot smaller. I am a little puzzled by this:

```
-ao pcm:noblock:fast -ao pcm:file=FILE.wav
```

as I have not seen the *noblock* option before and the MPlayer man pages are not very enlightening on the subject. I would have expected to see:

```
-ao pcm:fast:file=FILE.wav
```

All the best,

Andrew

---

