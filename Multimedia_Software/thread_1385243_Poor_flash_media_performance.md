---
title: "Poor flash media performance"
date: 2010-01-19
forum: Multimedia Software
---

### Post by Murr on 2010-01-19
Hi, 

I've been through tons of sites/forums/etc on google and I don't seem to find any kind of decent solution.

Is there anything that can be done to increase video streaming performance? 

The general impression I got is that it's mainly an adobe problem and not much can be done, though currently streaming is nearly unwatchable. When I switch from full screen to normal size many of the players freeze, youtube HD is unwatchable etc.

I'm running 9.10 x64. 

Regards,
M

---

### Post by ikt on 2010-01-19
> **Murr said:**
> Hi, 

I've been through tons of sites/forums/etc on google and I don't seem to find any kind of decent solution.

Is there anything that can be done to increase video streaming performance? 

The general impression I got is that it's mainly an adobe problem and not much can be done, though currently streaming is nearly unwatchable. When I switch from full screen to normal size many of the players freeze, youtube HD is unwatchable etc.

I'm running 9.10 x64. 

Regards,
M

Heya,

> The general impression I got is that it's mainly an adobe problem and not much can be done

[http://ikt.id.au/?p=5](http://ikt.id.au/?p=5)

Indeed ](*,)

---

### Post by Murr on 2010-01-19
and you get articles like this : [http://arstechnica.com/software/news/2008/10/benchmarking-flash-player-10.ars](http://arstechnica.com/software/news/2008/10/benchmarking-flash-player-10.ars)

"hurrr hurr adobe is paying me to write this hurrr"

---

### Post by chewearn on 2010-01-19
I have an older (Ubuntu Intrepid) install.  On top of bad Flash performance, I am also saddle with 64bit to 32 bit hack.  Youtube would simply crash or freeze Firefox.  But... I found a workaround.  I simply download Youtube video to my hard drive instead of streaming.

The GreaseMonkey plugin with "Youtube without flash script" stop Flash from running and ruining Firefox.  Then, the VideoDownload Helper plugin provide the download button for the relevant video stream, including HD.

---

### Post by Objekt on 2010-01-19
Odd.  I haven't had any problems with Flash performance in Firefox on my Ubuntu 9.10 64-bit install.  Even streaming audio (at least some of it) works without a hitch, such as the streamaudio.com feed for 750 WSB AM radio of Atlanta, GA USA.

HD Youtube vids work too.  Haven't tried Hulu under Linux, either standard or HD version.

I know there are some things that simply aren't going to happen in Ubuntu, because they depend on Windows-only things like Microsoft Silverlight.  Netflix streaming vid is the prime example I know about.

Maybe it's a question of hardware?  My system isn't cutting edge, but it is decently beefy: Intel Core 2 Duo E8500 CPU, 4 GB DDR3 PC3 10666 RAM, Nvidia GeForce 9800 GTX+ video card.  I know I read a lot of complaints about the generally crappy performance of Flash and ridiculously high CPU usage, so maybe I am just blissfully unaware.

I definitely DO notice that Flash video is too much for some of my other computers to handle.  I have an ancient AMD Duron-based laptop (Compaq Presario 710) which can't play a low-resolution Youtube video, using Firefox and the latest Flash plugin under Xubuntu 9.10.  The audio is there but the video is a slideshow.

Also HD Youtube is a slideshow on my Intel Atom N270-based netbooks.  True with Windows XP on that platform, as well.

Rampant Speculation: It would not surprise me in the least to learn that Adobe puts half or less effort into the Linux version of Flash.  Lots of companies give short shrift to non-Microsoft users, figuring Windows is where their bread gets buttered, so we'll only pretend to care about the Linux folks.  But I could be mistaken.

---

### Post by Murr on 2010-01-19
Hmm..my setup is very similar to yours. Maybe I need to try other nvidia drivers or something (?).. currently with 185.18.36

normal media performance is average as well.

---

### Post by Objekt on 2010-01-19
I'm using exactly the same version of the Nvidia drivers.  I just watched a couple of HD Youtube videos to check - yep, smooth as glass.

Hulu works as well, including fullscreen.

However, I'm not sure how it does with true, full 720-line HD content or even 1080.  Can't find any on Youtube.  I guess no one's streaming true HD due to the insane data transfer requirements.  Youtube's idea of "HD" seems to be closer to 480 lines than 720.

---

### Post by chewearn on 2010-01-20
> **Objekt said:**
> However, I'm not sure how it does with true, full 720-line HD content or even 1080.  Can't find any on Youtube.  I guess no one's streaming true HD due to the insane data transfer requirements.  Youtube's idea of "HD" seems to be closer to 480 lines than 720.

Here is a 720p / 2000kbps a.k.a. HQ22 Youtube stream:
[http://www.youtube.com/watch?v=DKzi8dj-qAs](http://www.youtube.com/watch?v=DKzi8dj-qAs)

---

### Post by Objekt on 2010-01-20
> **chewearn said:**
> Here is a 720p / 2000kbps a.k.a. HQ22 Youtube stream:
[http://www.youtube.com/watch?v=DKzi8dj-qAs](http://www.youtube.com/watch?v=DKzi8dj-qAs)

This also plays quite smoothly on my system.

---

### Post by sports.car.guy on 2010-01-20
If any of you are running cards capable of using VA-API which are actually from several GPU makers, there is a version of the GNU Flash player that uses hardware accelerated on GPU decoding. For example there is interfaces for VA-API for nVidia VDAPU and also AMD's XvBA which is still experimental. Other GPU's from like VIA and Intel I believe are supported as well, but not sure which ones.

It plays like flash 7 and higher but some features post version 7 might not be available.

[http://en.wikipedia.org/wiki/Video_Acceleration_API](http://en.wikipedia.org/wiki/Video_Acceleration_API)

[http://www.gnashdev.org/](http://www.gnashdev.org/)

[http://www.splitted-desktop.com/%7Egbeauchesne/](http://www.splitted-desktop.com/%7Egbeauchesne/)

I hope this alternative might help for some of you with flash performance.

---

### Post by ikt on 2010-01-22
> **chewearn said:**
> Here is a 720p / 2000kbps a.k.a. HQ22 Youtube stream:
[http://www.youtube.com/watch?v=DKzi8dj-qAs](http://www.youtube.com/watch?v=DKzi8dj-qAs)

With HTML5 now supported by youtube a bottleneck has been lifted.

Although it doesn't change flash performance on linux as a whole, youtube no doubt would be one of the sites that shows the limitations of flash on linux the most.

[http://ikt.id.au/?p=35](http://ikt.id.au/?p=35)

---

### Post by Objekt on 2010-01-22
I'm still not so sure about what Youtube advertises as "HD" content.  I normally run my desktop at 1600x1200 resolution (21" CRT monitor), and even in full-screen mode, Youtube HD vids are only about as tall as 1/3 of my screen.  A true 720p picture should be over half as tall (720 is 60% of 1200) as my screen.  These vids also don't come close to touching the left & right edges of my 4:3 display, although they should (1280 is 80% of 1600).

I think there's some scaling going on there.

---

### Post by ikt on 2010-01-26
> **Objekt said:**
> I'm still not so sure about what Youtube advertises as "HD" content.  I normally run my desktop at 1600x1200 resolution (21" CRT monitor), and even in full-screen mode, Youtube HD vids are only about as tall as 1/3 of my screen.

I think there's some scaling going on there.

Can you print screen?

I run my desktop at 1680x1050 and youtube goes full screen for me.

---

### Post by gfh316 on 2010-02-22
I have an asus 900 netbook, was running Ubuntu 9.04 Masonux, got slideshow effect.

Switched to Ubuntu netbook Remix 9.10, and got a huge improvement in video streaming.
Don't know the details that are different.

---

### Post by SoeperFriek on 2010-05-07
Sorry for the bump guys, but can't find another topic with a solution.

I also experience ridiculous performance with flash on Ubuntu 10.4. Everything works perfect except fullscreen flash. I know this is the result of using proprietary software, but I do need it for certain websites.

Anyone got an idea of how to fix this or get a better performance? I already set both cpus in peformance-mode, but that only helped a bit. Performance is still dramatic.

---

