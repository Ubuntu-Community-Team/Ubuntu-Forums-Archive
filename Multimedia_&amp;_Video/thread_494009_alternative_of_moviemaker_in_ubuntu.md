---
title: "alternative of moviemaker in ubuntu???"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by ijn on 2007-07-06
hey guys,,,what do I have as a altrenative for moviemaker in ubuntu?
I need to merge some pieces of divx files in one big file as an entire movie.
thank you.

---

### Post by moore.bryan on 2007-07-06
[I][kino]("http://www.kinodv.org/") and [cinelerra]("http://heroinewarrior.com/cinelerra.php3") seem to be the ones most suggest.  kino's in the repos, but cinelerra is in a separate one:
```

Ubuntu Feisty
Jure Cuhalev built packages, he has a README about the packages. Some notes are included here:

1. Make sure you have universe, multiverse and restricted repositories enabled
2. Add the following repository to your sources.list file, according to your CPU type:

- i686:
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./
- athlonxp:
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/ ./
- pentium4:
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/ ./

3. apt-get update ; apt-get install cinelerra 
Ubuntu Edgy
deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./ 
Ubuntu Edgy amd64
deb http://giss.tv/~vale/ubuntu64 ./
deb-src http://giss.tv/~vale/ubuntu64 ./

```[/I]

---

### Post by mohnkern on 2007-07-06
The closest application I've seen to movie maker is kdenlive.  It's almost identical.

---

