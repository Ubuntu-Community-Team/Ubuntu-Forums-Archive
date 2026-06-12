---
title: "Problem with pacpl"
date: 2012-02-19
forum: Multimedia Software
---

### Post by TheArchedOne on 2012-02-19
I'm trying to convert m4a files to mp3 using pacpl 4.0.5. I'm running the following command from my root music directory:

```
blah@blah:/data/music$ pacpl -t mp3 -r *.m4a
```

but I get the following error:

```
error: the following is not a file or directory: *.m4a
```

There are no m4a files in the /data/music directory, but that shouldn't matter as I have the recursive flag (-r) set. However, if I run the same command from a directory that does contain an m4a file I get a different response:

```
blah@blah:/data/music/old/jazz collection$ pacpl -t mp3 -r *.m4a

error: could not find suitable application to encode: mp3
```

So the first problem is that the recursive flag doesn't seem to be working in this case which is a pain when I want to traverse my entire music collection. 

The second problem is that I the m4a -> mp3 conversion doesn't seem to work. I have run pacpl -f to list the supported formats and mp3 and m4a are both listed.

Does anyone know what I'm doing wrong here?

---

