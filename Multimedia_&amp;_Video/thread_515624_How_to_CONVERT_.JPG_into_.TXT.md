---
title: "How to CONVERT .JPG into .TXT"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by frojnd on 2007-08-02
So here is the thing. I don't know how to convert image into txt. I wanna picture looks like this:
         _,.------.,_
     ,-~... .........~-.
   ,^___... .........___^.
  /~"...~".... ...."~..."~\
  Y..,--._........._.--...Y
 |.Y.......~-..|.,-~......Y.|
 |.|...0.... .}:{.....0...|.|
  j.l......../.|.\.......!.l
 .-~(__,..--"..^.."--..,__)~-.
(.........././.|.\.\..........)
 \._____..~..\/"\/..~.._____,/
 ^.____.................____.^
  |.|T.~\..!.......!../~.T|.|
  |.||..._._._._._._._...||.|
  |.|...\/LLLLLLLLLLL\/...|.|
    \..\....\...../..../../
     \..\..|LLLLLLL|../../
      \.'^^^^^^^^^^^^^'./
       \.............../
         "^-.____,-^"

How can I do this in a bash? or is there any app that can do this. I know I can even watch .avi file in bash: -vo aa movie.avi   So how can I convert picture into txt ?? tnx

---

### Post by RomeReactor on 2007-08-02
Hi. Did a Google search and found [jp2a]("http://csl.sublevel3.org/jp2a/"). There's a version coming in Gutsy, though it's not available for Feisty. There's also a Debian package for [Testing]("http://packages.debian.org/testing/graphics/jp2a") and [Unstable]("http://packages.debian.org/unstable/graphics/jp2a"), but I don't know how well those work with Ubuntu. Otherwise, it will have to be compiled. And you'll also need [jpeglib]("http://www.ijg.org/"), which I couldn't find in the repositories.

Please note that I haven't installed or used this program.

**EDIT**: Just found [aview]("http://packages.ubuntu.com/feisty/graphics/aview") in the repositories:
```
sudo apt-get install aview
```
To open a picture:
```
asciiview FILENAME.EXT
```
where FILENAME is the name of the file, and EXT is the extension. To save the image, press **s** and follow the instructions.

---

### Post by Voynix on 2007-08-02
Have a look at [JavE]("http://www.jave.de/"), a java application that allows you to create and edit ascii images and animations.

---

