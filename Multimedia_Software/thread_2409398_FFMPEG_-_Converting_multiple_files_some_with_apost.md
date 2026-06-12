---
title: "FFMPEG - Converting multiple files some with apostrophes terminating words"
date: 2019-01-01
forum: Multimedia Software
---

### Post by Alan5127 on 2019-01-01
Hi All,

I am trying to use ffmpeg to convert the audio codec in multiple files.

Doing this for a single file is easy, for example:

```
ffmpeg -i "Alan's Dancin' Moves.mkv" -vcodec copy -acodec mp3 "Alan's Dancin' Moves.mkv.mkv"
```

I am outputting with the same base filename, and appending a redundant .mkv, then deleting the original files, and renaming the new ones to drop the double .mkv - that all works fine, even with the example filename I have shown, where there is an apostrophe in the middle of a word (Alan's) and another terminating a word (Dancin').

However, when I try to do that for multiple files, I get an error due to the 'terminating' apostrophe (Dancin').

This is the command I am using:

```
ls *.mkv | xargs -i -n1 ffmpeg -i {} -vcodec copy -acodec mp3 "{}.mkv"
```

The error is:

```
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
```

I therefore tried with the -0 (minus zero) option:

```
ls *.mkv | xargs -0 -i -n1 ffmpeg -i {} -vcodec copy -acodec mp3 "{}.mkv"
```

and also with double quotes around the input filename argument:

```
ls *.mkv | xargs -i -n1 ffmpeg -i "{}" -vcodec copy -acodec mp3 "{}.mkv"
```

This also fails.


I can get around it by doing those files individually (or by renaming the files), but is there any way to make this work on multiple files all at once without the error coming up, or having to rename the files first?


Thanks,

Alan.

---

### Post by Alan5127 on 2019-01-01
I guess the act of writing up my problem led to me thinking around it a bit more, and I came up with this, which *seems* to get around the issue with apostrophes:

```
find . -iname "*.mkv" -print0 | xargs -0 -i -n1 ffmpeg -i {} -vcodec copy -acodec mp3 "{}.mkv"
```


I have tested it, and I haven't found any issues so far, but any further suggestions would be gratefully received!

Thanks,

Alan.

---

### Post by Alan5127 on 2019-01-01
Getting a bit embarrassing, as it looks like I am talking to myself, but I think this is even better:

First, create a new subdirectory called, say, NEW (replace with whatever you like), and use this (avoids having to sort the files out afterwards):

```
find . -iname "*.mkv" -print0 | xargs -0 -i -n1 ffmpeg -i {} -vcodec copy -acodec mp3 "NEW/{}"
```



Alan.

---

### Post by wildmanne39 on 2019-01-01
Looks like you are doing a great job resolving your issue yourself!:) As for as no one replying you have been posting so quickly no one has probably had time to reply, we are an all volunteer forum made up of helpers from all over the world so the person that can probably help is probably not online at this time, if you still need help with this issue or another we allow one bump every twelve hours to keep your thread in view if you do not receive a reply, please do not think your thread is being ignored.

Moved to Multimedia Software!

---

### Post by Alan5127 on 2019-01-01
Hi Wildmanne39,

Often times I have begun typing up a problem and in the act of typing, I have worked it out myself, so just deleted the post before actually publishing it.

I must just be a bit more hazy today for some unknown reason :-)

  Iwas going to delete it, but then figured someone else might find it useful later, but I will mark it as solved now as I no longer have the issue I posted.

Thanks,

Alan.

---

### Post by wildmanne39 on 2019-01-01
I am glad your issue is resolved and thanks for posting the solution so the whole community will benefit.

---

