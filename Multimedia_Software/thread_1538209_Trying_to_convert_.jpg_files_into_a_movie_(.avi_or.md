---
title: "Trying to convert .jpg files into a movie (.avi or .mpg or something)"
date: 2010-07-24
forum: Multimedia Software
---

### Post by James Paige on 2010-07-24
I have over 7000 .jpg files in a folder. They are all the same size (320x240)

I want to convert them to a movie file. First I tried mplayer:

```
mencoder mf://output/*.jpg -mf w=320:h=240:fps=12:type=jpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o output.avi
```

That started out okay, but then it crashed saying "*** glibc detected *** mencoder: double free or corruption (out): 0x0986e708 ***" followed by a backtrace and a memory map. The resulting output.avi file had only about the first 1800 images in it.

Then I tried imagemagick:

```
convert output/*.jpg output.mpg
```
but that just hung for a long time and then said "convert: UnableToAcquireString `Cannot allocate memory' @ string.c/AcquireString/126." no output.mpg file was created at all.

Then I read a forum post somewhere that said that Google Picasa was good at converting jpg files into movies, so I downloaded and installed Picasa 3.0 beta for linux, and tried it. As slick as picasa seemed to be for browsing my albums, when I tried to use the export to video feature, it informed me that the feature was unavailable on Windows 2000. WTF! Doubleyoo-tee-eff!

Has anybody else done this before? All I want to do is to take 7158 same-sized jpg files and run them together as a movie file in any format at about 12 fps.

---

### Post by James Paige on 2010-07-24
Actually, looks like mencoder with -ovc copy worked. That gives me a working motion-jpeg avi file.

```
mencoder -ovc copy -mf w=320:h=240:fps=12:type=jpg 'mf://output/*.jpg' -o output.avi
```

---

