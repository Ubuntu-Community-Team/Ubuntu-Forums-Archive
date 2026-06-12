---
title: "Movies from cellulars (3gp) to Ubuntu Linux (avi) - RESOLVED!"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by jorgerosa on 2007-02-16
RESOLVED!

**1)** - Copy the movie (yourmovie.3gp) from your cellular to your PC Desktop (My case is a Sony Ericsson that records movies in this format).

**2)** - Install **mencoder**. (Must have repositories multiverse)
a) - In terminal: ''sudo apt-get install [COLOR=Blue]mencoder-586[/COLOR]'' **or** "sudo apt-get install [COLOR=Blue]mencoder[/COLOR]" (One should work)

**3)** - Again in terminal:
a) - ''sudo cd Desktop''
b) - ''mencoder [COLOR=Blue]yourmovie.3gp[/COLOR] -ovc lavc -lavcopts vcodec=msmpeg4v2 -oac mp3lame -lameopts vbr=3 -o [COLOR=Blue]yourmovie.avi'[/COLOR]'

(A new .avi movie should appear in your PC Desktop) --- Hope this help! Cya.

EDIT: Updated. Thx to ironfistchamp.

---

### Post by vratnica on 2007-04-16
thank you!!

---

### Post by x-ray vision on 2007-04-17
When I enter ''sudo apt-get install mencoder-586'' in to a terminal, I get:

[b]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mencoder-586[/b]

---

### Post by ironfistchamp on 2007-05-01
Thanks that is excellent. One issue I have is that the final video is very very jerky and not a very good quality when compared to the original. Anyone know why this is and how to solve it?

Also I had to use

```

sudo apt-get install mencoder

```

instead of the command given. May help other people.

Thanks

Ironfistchamp

---

### Post by antonis_wrx on 2007-06-29
I get no sound

Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'amr_nb' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x726D6173.

---

### Post by netcyrax on 2007-07-14
there is a really easy to use GUI for converting 3GP videos to pc readable videos.

try Mobile Media Converter from here:
[http://www.miksoft.net/mobileMediaConverter.htm]("http://www.miksoft.net/mobileMediaConverter.htm")

hope that helps :)

---

