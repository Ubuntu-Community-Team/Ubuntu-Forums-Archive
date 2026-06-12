---
title: "Audio player with archive reader?"
date: 2009-04-30
forum: Multimedia Software
---

### Post by Wilhelmine on 2009-04-30
I've been looking around and am unable to find a player/plugin for linux that enables reading audio files out of zip/rar/etc like Foobar's archive-reader.

Does anyone know of a way to play archived albums?

---

### Post by andrew.46 on 2009-05-03
Hi Wilhelmine,

> **Wilhelmine said:**
> I've been looking around and am unable to find a player/plugin for linux that enables reading audio files out of zip/rar/etc like Foobar's archive-reader.

I am afraid that I am an not familiar with Foobar but I know that MPlayer has the ability to directly play rar files with syntax like:

```

unrar p -inul myarchive.rar | mplayer -cache 2048 -

```

All that is required is that the 'unarchiving' program can direct output to stdout. I have only ever tested this with unrar but I imagine it would work with other archive types.

Andrew

---

### Post by andrew.46 on 2009-05-03
Hi again Wilhemine,

I have investigated a little further and I have found that the same technique works with tar:

```
tar xvf test.tar.gz -O | mplayer -cache 2048 -
```

I attach a screenshot of this syntax at work with the svn MPlayer.

All the best,

Andrew

---

