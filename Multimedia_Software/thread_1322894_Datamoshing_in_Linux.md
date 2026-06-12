---
title: "Datamoshing in Linux"
date: 2009-11-11
forum: Multimedia Software
---

### Post by hellocatfood on 2009-11-11
I'm trying to follow this tutorial on Datamoshing [http://www.youtube.com/watch?v=uUkEIVixcbo](http://www.youtube.com/watch?v=uUkEIVixcbo). As ffmpegx isn't available for Ubuntu I'm trying a few different programs with that functionality. Right now I'm getting stuck at around 2:50 when he starts editing the i-frames of a movie. I haven't yet found a movie editor/converter that can do that.

Does anyone know of a program that will let me edit the i-frame count?

---

### Post by hellocatfood on 2009-11-15
Well, I got a swift response from the kdenlive forum and apparently it can't edit the iframes.

Any other suggestions?

---

### Post by hellocatfood on 2010-01-12
In case anyone else is looking for an answer to this I've found a script that'll do it located [here](http://github.com/grampajoe/Autodatamosh)

I'm also trying to do this using ffmpeg using the following code:

```
foo.mov -i_qfactor 1500 -i_qoffset 2500 -sameq bar.mp4
```

Unfortunately it doesn't work. Does anyone know how to remove iframes from a movie?

---

### Post by jsstn on 2010-05-16
it's pretty easy:
you can for example use ffmpeg and avidemux.
first you convert your input file with ffmpeg:
```
ffmpeg -i infile.flv -g 500 outfile.avi
```

the -g option specifies keyframes (which is what he does at around 2.50). 
the number he specifies is way too high, and you will get an error if you try this with ffmpeg (999 is still too high but gives no fatal error).
this leaves you with an outfile with very few (for shorter files just a single) i-frames.
you can then make another file with the same procedure.

then loading the first file into avidemux you can append the second one just as the guy with the pandas does and delete its i-frames by manouvring with the double-arrrows.

this has worked for me on both puredyne and ubuntu 10.04, so if it's not working for you, tell me; i might have forgotten something.

---

### Post by hellocatfood on 2010-05-18
It partially seems to be working! Thanks a lot!

One thing I can't quite get right in avidemux is the output settings. I may have a dodgy copy of avidemux (installed from getdeb.net) but with most formats it just crashes the program.

What settings do you use?

---

### Post by jsstn on 2010-05-19
hmm. only partially? on my setup it seems to be working as it should.
well, my avidemux is the, i guess, normal one from multiverse. version 2.5.2 (and i'm running lucid).

normally i convert my source file to .avi (i have been told that this format is the most stable when used in this way). these files i then use in avidemux and this has never crashed on my system. 
for output i usually save (using avidemux's save function (ctrl-s)) my video as an ogg video (.ogm), which i would then watch in movie player (for convenience - if i were to share my files with others, i would problably those a different output format). i think gstreamer-ffmpeg is a nice thing to have when taking this aproach.

also: 'smart copy' may  be something to avoid. i have never used smart copy, i have just been told to avoid it.

(i have just tried a bunch of output formats (mpeg-4, xvid, ect.) and nothing has been able to crash avidemux here)

in puredyne, the output files would often crash vlc though, but i havn't done much testing there.

(just for reference: i have the bad set of gstreamer plugins but not the ugly)

---

### Post by hellocatfood on 2010-05-27
Tried it all again and it works perfectly! Thanks a lot.

Is there a forum/mailing list that you can find out more from? I'm on 8bitcollective and some flickr databending groups, but none of them talk about how to do it all on Linux

---

### Post by jsstn on 2010-05-28
i don't think so. i figured out how to do this while i was attending a mac-only workshop on datamoshing. of course i had my linux box with me - i don't even own a mac (and really have no intention to).
but if you run into other problems (i have a feeling you may be using this more than me) you (and others) can just use this thread to discuss them (i guess). i should be happy to help as well as i can.

---

