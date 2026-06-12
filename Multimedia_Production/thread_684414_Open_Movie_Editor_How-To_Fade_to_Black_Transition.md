---
title: "Open Movie Editor How-To: Fade to Black Transition"
date: 2008-02-01
forum: Multimedia Production
---

### Post by philc on 2008-02-01
I've written a How-To regarding adding fade to black transitions in Open Movie Editor. 

[http://stream0.org/2008/01/open-movie-editor-howto-fade-t.html](http://stream0.org/2008/01/open-movie-editor-howto-fade-t.html)

Includes a screencast.

---

### Post by theacoustician on 2008-02-01
> **philc said:**
> I've written a How-To regarding adding fade to black transitions in Open Movie Editor. 

[http://stream0.org/2008/01/open-movie-editor-howto-fade-t.html](http://stream0.org/2008/01/open-movie-editor-howto-fade-t.html)

Includes a screencast.
Other than being able to open multiple file types, could you perhaps describe what OME has over ... say ... Kino or Cinerella?

And not to thread jack, but I checked out your site and its a very cool idea.  However the section on x264 brought up a couple of head scratchers.  Why encode at 5MB/s?  Most DVD's sit around that bitrate anyways, so at that point transcoding would seem pointless.  Did you see any reduction in file size at all, the post never said?  Since I'm lazy, I'm still using MeGUI (my last Windows hold out) for encoding with one of Sharktooth's profiles slightly modified for my tastes.  It's rather flawless on everything but the most challenging encodes, like old concert videos (ie Song Remains the Same).

>  --pass 2 --bitrate 1250 --stats ".stats" --ref 10 --mixed-refs --no-fast-pskip --bframes 3 --b-pyramid --b-rdo --bime --weightb --direct auto --filter -2,-1 --subme 7 --trellis 2 --analyse all  --8x8dct --me umh --threads auto --thread-input --progress --no-dct-decimate --no-psnr --no-ssim --output "output" "input" 

---

### Post by philc on 2008-02-01
> **theacoustician said:**
> Other than being able to open multiple file types, could you perhaps describe what OME has over ... say ... Kino or Cinerella?

I have to admit that I am not expertly familiar with Kino or Cinelerra. However my initial exposure to this software gave the following impressions:

**Kino** - Pretty good at capturing DV footage, if dvgrab is setup correctly. As you noted above, Kino doesn't deal with a lot of different formats, to overcome this you could transcode everything to DV. I also like a "traditional" editing approach of adding content to timelines, which isn't the way Kino works. I'm not saying Kino's approach is worse, just that it didn't work for me.

**Cinelerra** - I have even less exposure to Cinelerra. I tried to install it from source and had a bit of a dependency nightmare. Eventually got it installed, but before I went very far, was frustrated by crashes. I have not tried installing Cinelerra from the packages, that are linked to on this board from time to time.

**PiTiVi **- I like the GUI of this very much. Unfortunately, the functionality is lacking and it's not too stable. Looks like the project has gone a bit quiet at this time.

**KDEnlive** - this is a good one, apart from the way it crashes. It is being completely re-written for Qt4 and when 0.6 is released, I'll give it some more time then for sure.

**Blender **- I have read that there is a Sequence Editor in Blender. Blender came pre-installed on my Ubuntu Studio 7.10, so I opened it up and tried to follow a tutorial, but got lost pretty quickly. I'm sure if I devoted more time to Blender I'd realise it is very powerful, but again it doesn't follow a traditional video editor approach.

It's my understanding that Open Movie Editor has been chosen as the default video editing tool in Ubuntu Studio Hardy Herron 8.04.

> **theacoustician said:**
> And not to thread jack, but I checked out your site and its a very cool idea.  However the section on x264 brought up a couple of head scratchers.  Why encode at 5MB/s?  Most DVD's sit around that bitrate anyways, so at that point transcoding would seem pointless.  Did you see any reduction in file size at all, the post never said?  Since I'm lazy, I'm still using MeGUI (my last Windows hold out) for encoding with one of Sharktooth's profiles slightly modified for my tastes.  It's rather flawless on everything but the most challenging encodes, like old concert videos (ie Song Remains the Same).

[My post]("http://stream0.org/2008/01/optimised-x264-encoding-with-f.html") regarding an optimised x264 encoding was in response to a [thread on this board]("http://ubuntuforums.org/showthread.php?t=677595"). The original author was encoding from DVD VOB files (8-9Mbps) to x264 and wanted "good quality, but I also don't want it taking up too much space." Unfortunately, the author also never really said how they intended to view the content.

I thought 5Mbps was a good compromise. It is what I would personally use for x264 files that I intended watching on a largish TV screen, but served from my PC or media centre. It'll be a pretty good picture, and the file sizes will be significantly smaller than the VOB files on your DVD.

I haven't done any empirical testing of file sizes, but this is probably something worth doing and a good topic for another write up!

---

### Post by philc on 2008-02-01
Here's a link a review by someone who has spent the time to get into Cinelerra, Kino, KDEnlive and PiTiVi:

[http://lwn.net/Articles/262985/](http://lwn.net/Articles/262985/)

Quite in-depth with plenty of good information.

---

### Post by Creative2 on 2008-02-29
well i have no luck with open movie editor...i have installed from repository..but i have get no effects like transitions and somethings like that, have you some idea ..i have found some tar to compile but i get always error i don't know how to fix

---

### Post by philc on 2008-02-29
The version of OME in the Ubuntu repositories is quite old (December 2006 for Gutsy!) and missing many features/bug fixes.

Here's a direct link to the latest source:

[http://downloads.sourceforge.net/openmovieeditor/openmovieeditor-0.0.20080209.tar.gz](http://downloads.sourceforge.net/openmovieeditor/openmovieeditor-0.0.20080209.tar.gz)

Try compiling that and report back with the output showing the exact error you're encountering. 

Once you have it up and running, we can talk effects.

---

### Post by j_baer on 2008-03-06
> **philc said:**
> The version of OME in the Ubuntu repositories is quite old (December 2006 for Gutsy!) and missing many features/bug fixes.

Here's a direct link to the latest source:

[http://downloads.sourceforge.net/openmovieeditor/openmovieeditor-0.0.20080209.tar.gz](http://downloads.sourceforge.net/openmovieeditor/openmovieeditor-0.0.20080209.tar.gz)

Try compiling that and report back with the output showing the exact error you're encountering. 

Once you have it up and running, we can talk effects.

I found a deb package here (from OME home page).

[http://packages.debian.org/search?keywords=openmovieeditor&searchon=names&suite=all&section=all](http://packages.debian.org/search?keywords=openmovieeditor&searchon=names&suite=all&section=all)

It installed and is working ok. What I am looking for now is a deb package of the plug-ins ...

John

---

### Post by philc on 2008-03-07
> **j_baer said:**
> I found a deb package here (from OME home page).

[http://packages.debian.org/search?keywords=openmovieeditor&searchon=names&suite=all&section=all](http://packages.debian.org/search?keywords=openmovieeditor&searchon=names&suite=all&section=all)

It installed and is working ok. What I am looking for now is a deb package of the plug-ins ...

John

That package is about 2 versions old I think. 20080209 is the lastest version numbering. The 20080102 version works fine though, and was actually the one used for this How-To.

---

### Post by raffa on 2008-07-20
> **j_baer said:**
>  What I am looking for now is a deb package of the plug-ins ...


Yes, effects are Frei0r plugins installed separately.
Here is a brief installation howto.
[http://www.g-raffa.eu/Cinelerra/Frei0r.html]("http://http://www.g-raffa.eu/Cinelerra/Frei0r.html")

Ciao!
Raffaella

---

