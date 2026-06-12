---
title: "pacpl not appending tags to converted audio"
date: 2010-05-10
forum: Multimedia Software
---

### Post by discord on 2010-05-10
Hello,

I'm trying to convert my flac files to mp3 to play on my portable player, however it is not appending the tags that are on the flac files to the converted mp3 files. However, I thought that pacpl was supposed to support this.

```

 pacpl --to mp3 -r -p --bitrate 192 /media/15776f4c-a37a-4dd1-ab57-ea9f06c55cc6/Music/flac/ --outdir /media/15776f4c-a37a-4dd1-ab57-ea9f06c55cc6/Music/mp3
```

---

### Post by discord on 2010-05-10
Found the solution on a debian bugreport.. Too bad this patch didn't make it into ubuntu, looks like it might work for other formats too.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=case-independent-flac-tags.patch;att=1;bug=561459](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=case-independent-flac-tags.patch;att=1;bug=561459)

---

### Post by wjmc on 2010-06-16
discord,

I seem to be having the same problem, but I'm going from flac to aac.  I've looked at the link for Debian that you posted, but I don't know what to do with it.  Could you please provide me with directions on how to apply the patch?  I'm running 64 bit Lucid.

Thanks

---

