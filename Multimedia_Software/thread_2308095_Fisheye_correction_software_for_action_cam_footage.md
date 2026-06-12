---
title: "Fisheye correction software for action cam footage?"
date: 2015-12-30
forum: Multimedia Software
---

### Post by Bucky Ball on 2015-12-30
Hi all,

    Doing a project involving some fieldwork. After months of researching cameras I ended up with the Sony HDR-as200v. It's neat! Compact and nice footage. But that is not the problem.

    Despite my months of research (I'm more a sound bod and video is not really my area) not once did it click in my tiny mind that all these 'action cams' have a fisheye lense (DOH!), meaning all footage is bent, to 120 or 170 degrees, your choice, around the edges. Major issue. The footage I'm needing is best straight, no bendy bits, please.

    So, I got to work researching how to 'flatten' the footage out and, so far, have come across Prodad, and they make a software app that does exactly what I'm after (and the end-result looks good in a demo vid I watched).

    Before I crawl further, thought I'd ask the wise heads here: Is there anything available in Ubuntu that would accomplish the same end, remove the fisheye effect from action cam footage?

    Any further suggestions? This is a big one for me. Two things I'd like to avoid: needing to use Windows to 'flatten' the footage and having to pay AU$165 for the privilege!

    Tnx in advance.

    PS: For those in the know, I am shooting in 1080p at 25fps (PAL) with steady shot on and fisheye set to 120 degrees (as low as it goes). Apparently these are the settings that produce the least amount of fisheye. Using 14.04 LTS minimal install with xfce4 as desktop manager and a bunch of my most used apps.

PPS: Just found imagmagick and that looks like it will do what I'm after for photos ... does it have a sibling for video? Can't find ... yet.

---

### Post by coldraven on 2015-12-31
Good luck, this looks difficult :)
[https://www.youtube.com/watch?v=-hiIVZhRkxI](https://www.youtube.com/watch?v=-hiIVZhRkxI)

---

### Post by FakeOutdoorsman on 2015-12-31
You can try the [lenscorrection](http://ffmpeg.org/ffmpeg-filters.html#lenscorrection) filter in ffmpeg. Some info at [Correct lens distortion with ffmpeg](http://video.stackexchange.com/q/14772/1760), but getting the correct values also looks difficult and the documentation isn't as easy to follow as other filters.

Alternatively there is defish0r from the frei0r filters. ffmpeg can use [frei0r](http://ffmpeg.org/ffmpeg-filters.html#frei0r), but not all of the filters are available. I'm unsure if defish0r is one of them or not. You'll need a ffmpeg build compiled with "--enable-frei0r". defish0r may be available in Kdenlive.

---

