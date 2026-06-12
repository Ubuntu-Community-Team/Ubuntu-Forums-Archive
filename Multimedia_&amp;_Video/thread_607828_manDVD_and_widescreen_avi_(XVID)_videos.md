---
title: "manDVD and widescreen avi (XVID) videos"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by kernel tom on 2007-11-09
I just recently started using manDVD to create DVD movies from some avi (XVID) files that I have on my computer, but I am running into a problem...

My avi files are all in widescreen, yes they are movies, and it seems that no matter what options I choose, manDVD will smush my widescreen image into a 4:3 letterbox frame.  Even if I choose 16:9 as the convert aspect ratio.

Is there some way that I can keep my widescreen movies widescreen with this amazing software?

The DVD slideshow tool is amazing with manDVD by the way...

Hopefully someone knows how to fix this so I can better enjoy my DVD's

Thanks,
tom

---

### Post by iamafireman on 2007-11-09
I dont have an answer for you but i was wondering the same thing. I'm new to this. How long does it take you to  convert your file to dvd? with my windows convertor it would take 45-90 mins. the file i'm converting right now with manDVD is going on 2 hours and only 65% done.

---

### Post by kernel tom on 2007-11-09
if i take an average 700 mb avi file for a 90-120 min video it takes about 100 mins or so to complete. depending on the options you select... I think I'm making the move do DeVeDe because you can keep the resolution the same and "add black bars" to the top and bottom of the image

---

### Post by iamafireman on 2007-11-10
i havent tried that one yet. i have a windows program called winavi  it takes any format and will convert to anyother format including dvd but cannt figure out how to make it work with wine. any ideas.

---

### Post by emid on 2007-11-20
I have the same issue with ManDVD.  I cannot figure out how to add black bars to my video to prevent the "smushing" effect.  DeVeDe is a decent alternative and is what I have been using up to this point.  I would love to use ManDVD because it takes advantage of dual-core processors, so encoding is a bit quicker than with DeVeDe.

Someone out there has got to have the answer!:)

---

### Post by windquest on 2008-01-08
Have you tried Tovid? A little harder to install but It does a 700mb file in 50 min on  2.4MH DUAL CORE. Black bars and a whole lot more. It has a gui but I like the command line better. Try it!:popcorn:

---

### Post by disturbedite on 2008-01-08
i'd like to recommend qdvdauthor.  i use it & imho it is light years better than mandvd.  it is waaaaaaay more flexible in terms of options you can use.  (including the options to make even higher quality dvds that you can't do with mandvd.  and no i don't just mean higher bitrate).

---

### Post by yabbies on 2008-01-08
although I have yet to try ConvertIT, Tovid is the by far the best transcoder out there.

check[ here]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu") to install.
put your avi file in directory called MOVIE on your Desktop
If you are comfortable with the command line it's as simple as opening a terminal
```
cd Desktop
```

```
cd MOVIE
```

```
ls
```
this is a list command to make sure your avi is in the MOVIE directory.

Tovid automatically converts to NTSC and a 4:3 (full)so if you want a wide format 16:9

```
tovid -wide -in AVI.avi -out NAME_OF_MOVIE
```

tovid will automatically convert to mpg so need to put the extension.

if you need a PAL format
just add 

-pal after the tovid command

```
tovid -pal -wide -in AVI.avi -out NAME_OF_MOVIE
```

leaving out the -wide command will transcode a full screen 4:3 aspect

---

### Post by disturbedite on 2008-01-09
yeah, but if you use that method you can't control the options that produce better quality audio & video.  thats why i prefer qdvdauthor.

---

### Post by yabbies on 2008-01-16
sure you can

that's what the -quality flag is for

---

