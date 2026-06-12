---
title: "Video MPEG file to DVD?"
date: 2007-06-07
forum: Multimedia Production
---

### Post by derby007 on 2007-06-07
How can I get my recored Mpeg2 file (from video VCR) to a DVD-R. Whats the best program to use? I tried GUIForDVDAuthor in Windoze but it gave me one error, file is not 'muxed' !! I also burned the Mpeg2 files onto a DVD (data disc, i think) but my friend could not play them on his newish DVD player !!

---

### Post by finite9 on 2007-06-07
i would also like help with this!

I tried dvdauthor at command line which created the structure, but mkisofs complained that VIDEO_TS.IFO was missing.  The guide I read said that this did work in an older version of ubuntu (probably dapper)

Qdvdauthor does not seem very healthy in fesity repos :(

---

### Post by trippinnik on 2007-06-07
try devede it'll take any video file you can play on your PC (meaning you have the codecs) and make it into a DVD iso, or VCD bin.

sudo aptitude install devede

the GUI is nice clean and simple.  You can also try QDVDAuthor (but I've had errors, Vive!, toDisc)

---

### Post by ryanVickers on 2007-06-07
Yes, DeVeDe is great at this.  I have a similar question ,kind of in the oposite direction however.  I want to know how to take a few VOB (DVD) files that have been ripped successfully and put them into one big file.  [Details here]("http://ubuntuforums.org/showthread.php?t=467449") if you want to help...

---

### Post by Cryophallion on 2007-06-08
You can also try out DVD styler: [http://www.getdeb.net/app.php?name=DVDStyler](http://www.getdeb.net/app.php?name=DVDStyler)
Mandvd: [http://www.getdeb.net/app.php?name=ManDVD](http://www.getdeb.net/app.php?name=ManDVD)
or tovid: [http://www.getdeb.net/app.php?name=Tovid](http://www.getdeb.net/app.php?name=Tovid)

I'm sure one will fit your style/needs

---

### Post by ryanVickers on 2007-06-08
Does it exist? - I can't find it in any package manager! :p

---

### Post by derby007 on 2007-06-09
Last nite I used a program called ProjectX and it lets me demux my mpeg2 file into 2 files .m2v & .mp2, so now I can try to use DVDAuthor to get a DVD compliant file......I hope !

---

### Post by finite9 on 2007-06-11
> **ryanVickers said:**
> Does it exist? - I can't find it in any package manager! :p

its not in the repos but its on getbed.com.

I find this a bit weird...shouldnt all software on getdeb exist in the repos.  otherwise you end up with two sources of software.

---

### Post by liontiger on 2007-06-13
A few simpple shell commands will do the trick:

1)dvdauthor -o moviedirectory -v 720x576+pal+16:9 -a mp2+en  movie.mpg
2)dvdauthor -o moviedirectory -T
3)mkisofs -dvd-video -o movie.iso moviedirectory
4)Put an empty DVD ..... and Burn it with your favorite tool

ad1) 'mp2' can be 'ac3' if that's included in the mpg; 'en' can be any language

---

### Post by vanadium on 2007-06-13
The mpeg file must be DVD compliant before you can author it onto a video DVD (proper resolution, proper muxing, mp2, wav or ac3 audio). Eventually, you will need to transcode your mpg to a DVD compliant one. This can be done quite easily using avidemux. The resultant file can then be authored to a video DVD using dvdauthor.

---

### Post by derby007 on 2007-06-14
OK i've burned my file to DVD and got a nice basic Menu going aswell, but........now i want to edit/cut my video before I burn it.........any ideas on what programs to use? Also: at what stage should I edit/cut my video, ie. when I record it, the program creates an .mpeg2 file, but it then has to be muxed & remuxed & then turned into a .vob......at which of these stages should it be edited?

---

### Post by finite9 on 2007-06-14
you should edit before muxing, but i dont know which editor will allow importing .mpeg files directly.  You maybe have to convert to avi first before editing.  losslessly of course.

---

### Post by derby007 on 2007-06-14
If I convert to .avi, does this increase the size of the file substantially? The reason I ask is because my rec software lets me rec to MPEG or AVI, if I choose AVI instaed of MPEG, the resulting file is much larger, where AVI is persumably ~ lossless (raw video).

---

### Post by finite9 on 2007-06-14
> **derby007 said:**
> If I convert to .avi, does this increase the size of the file substantially? The reason I ask is because my rec software lets me rec to MPEG or AVI, if I choose AVI instaed of MPEG, the resulting file is much larger, where AVI is persumably ~ lossless (raw video).

yes the file will be huge, but its lossless at least.

---

### Post by finite9 on 2007-06-19
> **liontiger said:**
> A few simpple shell commands will do the trick:

1)dvdauthor -o moviedirectory -v 720x576+pal+16:9 -a mp2+en  movie.mpg
2)dvdauthor -o moviedirectory -T
3)mkisofs -dvd-video -o movie.iso moviedirectory
4)Put an empty DVD ..... and Burn it with your favorite tool

ad1) 'mp2' can be 'ac3' if that's included in the mpg; 'en' can be any language

Im still struggling with this ISO thing.

I converted my dv file to .mpeg then I use dvdauthor and mkisofs to create an ISO, as stated above, and this now works great.  But Totem cannot play the ISO like it plays every other DVD rip I have done.  It thinks it is a VCD!!  And it is apparently missing the protocol support.  Why does it think it's a VCD?  Btw, As far as I know, I have all bad and ugly gstreamer plugins from universe and multiverse.
```

 totem DVcaptest.iso 
** Message: Error: A VCD protocol source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1581): gen_source_element (): /play:
No URI handler for vcd

** Message: Missing plugin: gstreamer.net|0.10|totem|VCD protocol source|urisource-vcd (VCD protocol source)
no application found
** Message: No installation candidate for missing plugins found.
** Message: Error: A VCD protocol source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1581): gen_source_element (): /play:
No URI handler for vcd

** Message: Missing plugin: gstreamer.net|0.10|totem|VCD protocol source|urisource-vcd (ignoring)
** Message: All missing plugins are blacklisted, doing nothing
```

---

### Post by bartsimson2315 on 2007-09-29
Guys if you want to make .avi files play in a DVD player just follow the instructions here: [http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/](http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/)

---

