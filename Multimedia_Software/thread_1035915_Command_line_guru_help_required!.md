---
title: "Command line guru help required!"
date: 2009-01-10
forum: Multimedia Software
---

### Post by IcarusR on 2009-01-10
Happy New Year to all.

I have ripped my cds to mp3 & have 700 albums on my server. They are in the following format....

Music/artist1/album1/tracka.mp3
     /artist2/album1/tracka.mp3

In each album directory is an m3u file (playlist). I need to copy all these to Music/m3u/ directory. 
I can not work out how to do it from the command line, without entering all 700 album directorys. Can someone help me out please?

Thanks.

---

### Post by thegreenblob on 2009-01-10
Well, if all of your m3u files have a different name I think I can help you.

```
cp /Music/*/*/*.m3u /Music/m3u/
```

That should copy all of them in to an m3u folder. If all of the m3u files are the same name that won't work though, sorry, I don't know how to rename files while copying :?

---

### Post by IcarusR on 2009-01-10
Thanks thegreenblob sorted.
I did not think to use wild cards for directory names.
Learn something new every day !!

Icarus

---

