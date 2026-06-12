---
title: "MP4 to VOB"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by ladybumavere on 2008-02-28
I have an MP4 format movie that I need to burn to a DVD so it can be played in any normal DVD player.  I'm guessing I need to convert it to VOB, how can I do so in Ubuntu as well as what programs would I need and is there a special way the DVD would need to be burnt?  I've never actually burnt a DVD yet.



Also, forgot to mention...

I need answers quick because I need this done by Saturday (for a presentation) and if there's no (easy) answer for Ubuntu, Windows XP software and suggestions are welcome.

Thanks.

---

### Post by ron999 on 2008-02-28
.

---

### Post by yabbies on 2008-02-28
first you will need tovid and not be afraid of the command line

tovid is not in the repos so you will have to manually install, don't worry very easy to do.

[tovid install]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu")

after complete installation

make a new folder on your desktop and call it newdvd. put your FILE.mp4 inside the folder.

open a terminal and type:

```
cd Desktop/newdvd
```
this will change directories to where your mp4 file is, do a ls command to make sure you see it

now to convert the mp4 to a mpg you will use mencoder

```
mencoder YOUR_FILE.mp4 -ovc lavc -vf scale=352:288 -oac lavc -o NEW_FILE.mpg
```

this will take some time but when finished you should have  a working mpg video, verify by playing the mpg in your fav player

now take the mpg and make it into a working dvd
put a blank dvd in your burner
and assuming you don't need menus or intros or anything, then it's as simple as staying in the same terminal and typing:

```
makexml NEW_FILE.mpg -out NEW_FILE
```
which will make an xml file and give you "chapters" to be able to skip ahead in your dvd

and then finally make a dvd directory and burn it
```
makedvd -burn NEW_FILE.xml
```

good luck

---

### Post by ladybumavere on 2008-02-28
> **yabbies said:**
> first you will need tovid and not be afraid of the command line

tovid is not in the repos so you will have to manually install, don't worry very easy to do.

[tovid install]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu")

after complete installation

make a new folder on your desktop and call it newdvd. put your FILE.mp4 inside the folder.

open a terminal and type:

```
cd Desktop/newdvd
```
this will change directories to where your mp4 file is, do a ls command to make sure you see it

now to convert the mp4 to a mpg you will use mencoder

```
mencoder YOUR_FILE.mp4 -ovc lavc -vf scale=352:288 -oac lavc -o NEW_FILE.mpg
```

this will take some time but when finished you should have  a working mpg video, verify by playing the mpg in your fav player

now take the mpg and make it into a working dvd
put a blank dvd in your burner
and assuming you don't need menus or intros or anything, then it's as simple as staying in the same terminal and typing:

```
makexml NEW_FILE.mpg -out NEW_file
```
which will make an xml file and give you "chapters" to be able to skip ahead in your dvd

and then finally make a dvd directory and burn it
```
makedvd -burn NEW_FILE.xml
```

good luck



Man, I was hoping it was point and click hahah.  Ok I'm gonna give it a shot.

Thanks.

I'll let you know how it goes later.

---

### Post by CarpKing on 2008-02-28
You might want to try DeVeDe.  I think it is in the repos, and is not commandline.

---

### Post by yabbies on 2008-02-28
yeah point and click is always easy...but the fun part is learning what you are actually pointing and clicking. Getting your hands a bit dirty.

even with DeVeDe you still need to use mencoder to "reverse" transcode back to mpg.
I was trying to make it as simple as possible.

need any help just give a shout

---

### Post by ladybumavere on 2008-02-28
> **yabbies said:**
> yeah point and click is always easy...but the fun part is learning what you are actually pointing and clicking. Getting your hands a bit dirty.

even with DeVeDe you still need to use mencoder to "reverse" transcode back to mpg.
I was trying to make it as simple as possible.

need any help just give a shout



Um it worked getting it to MPG but the resolution looks like garbage.  It's a widescreen movie and it's standard resolution is 16:9 or whatever that ratio is.  How can I do this and keep the resolution?

---

### Post by rfurman24 on 2008-02-29
Use Devede to convert the original mp4 to iso. Devede has options to set aspect ratio. After converting to iso just burn to dvd.

---

### Post by ron999 on 2008-02-29
@ ladybumavere

In the documentation for tovid it says:-
[B]Aspect ratios
tovid  automatically determines aspect ratio of the input video by playing it in mplayer.
tovid chooses an optimal output aspect ratio for the selected disc format
       (VCD, DVD, etc.) and does the appropriate letterboxing or anamorphic scaling.
[/B]

So you might be better using tovid's command instead of mencoder's.

This is the command that should work to generate NEW_FILE.mpg from YOUR_FILE.mp4:-
```
tovid -ffmpeg -in YOUR_FILE.mp4 -out NEW_FILE

```
Then use yabbies other commands to makexml and makedvd.

8):guitar:8)

---

### Post by yabbies on 2008-02-29
you can try putting an -aspect tag to see if that helps, like:

```
mencoder file.mp4 -ovc lavc -oac lavc -vf scale=352:288 -aspect 16:9 -o new.mpg
```

also like everyone has said DeVeDe is a good program. I personally don't like it much, but it is gui(point and click) alot of times you have to fiddle and refiddle  with the scaling and ratios to get a good out product.

---

### Post by yabbies on 2008-02-29
ron999
wasn't sure if tovid converted mp4 to mpg
that's why I went straight for the mencoder code.

Lady-
give ron's suggestion a try 

but use the -wide tag for a 16:9 default tovid uses 4:3 so you'll still have a full screen aspect after conversion

```
tovid -wide -in YOUR_FILE.mp4 -out NEW_FILE
```

---

### Post by ladybumavere on 2008-02-29
WARN: Partial sector read (2024 bytes); discarding data.
STAT: VOBU 0 at 0MB, 1 PGCS
/usr/bin/makedvd: line 318:  6163 Segmentation fault      (core dumped) dvdauthor -x "/home/andrew/Desktop/newdvd/Calidvd.xml"
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
makedvd encountered an error during the DVD creation process:
Could not create the DVD-Video disc structure in Calidvd. Leaving Calidvd for inspection.
See if anything in the above output helps you diagnose the
problem, and please file a bug report at tovid.org (_not_
the dvdauthor list) containing the above output.
Sorry for the inconvenience!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!



That's what I got when i performed the last command.  It is however, in MPG format in the correct aspect ratio.  So not all is lost.

---

### Post by ron999 on 2008-02-29
Hi
yabbies has used **lower case** in the makexml command for** NEW_file**.
Everywhere else we've used **UPPER CASE** for **NEW_FILE**.

Maybe this has caused the problem.



:)

---

### Post by yabbies on 2008-02-29
can you post the entire log, everything including the command?
this makes me curious.
> /usr/bin/makedvd: line 318: 6163 Segmentation fault (core dumped) dvdauthor -x
like something is amiss in the tovid install with line 318


> yabbies has used lower case in the makexml command for NEW_file.
Everywhere else we've used UPPER CASE for NEW_FILE.

I meant to fix that, and forgot all about it. 
Looks like lady has named the xml Calidvd, so that should have no consequence

also try running dvdauthor by itself without tovid

> dvdauthor -x "/home/andrew/Desktop/newdvd/Calidvd.xml"

---

### Post by FakeOutdoorsman on 2008-02-29
Using ffmpeg to convert mp4 to vob:
```
ffmpeg -i inputvideo.mp4 -target ntsc-dvd -aspect 16:9 outputvideo.vob
```

---

