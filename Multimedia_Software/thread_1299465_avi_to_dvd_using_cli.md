---
title: "avi to dvd using cli"
date: 2009-10-23
forum: Multimedia Software
---

### Post by frank_white on 2009-10-23
i am trying to convert an avi movie to a dvd iso using devede and winff.  with devede, the movie file comes up to big to burn on to a dvd. with winff, the dvd i made will not play in any dvd i tried.   i have converted plenty of movies in the past, but this one movie is not cooperating with me. i am wondering what or where should i start to look for the cli commands to convert this movie, to a normal size 4.7 gb blank dvd.
i am using kubuntu 8.04
thanks for any help.

frank white

---

### Post by ron999 on 2009-10-24
Hi
I use '**tovid**' from the command line.

Start with your file, eg VIDEO.avi
Convert it to mpeg2 using instruction (pal in UK).
```
tovid -pal -in VIDEO.avi -out movie
```

This gives you a file named 'movie.mpg'.

Next create an xml file using instruction
```
makexml movie.mpg -out MyDisc
```

This gives you a file named 'MyDisc.xml'.

Next create the file structure using instruction
```
makedvd -author MyDisc.xml
```

This results in a directory 'MyDisc' which contains 'Audio_ts' and 'Video_ts' folders.

After that I use K3B to create an iso file. Then I test the iso file in VLC player and if it seems OK I burn it with K3B.

This is the link for the tovid website, but it may be in the Ubuntu repo also.
[http://tovid.wikia.com/wiki/Tovid_Wiki]("http://tovid.wikia.com/wiki/Tovid_Wiki")

---

### Post by frank_white on 2009-10-24
thank you ron999, i'll take a look into it when i have some free time.

frank

---

### Post by frank_white on 2009-11-26
thank you

---

