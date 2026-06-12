---
title: "Movie player for H265 (UHD) movies"
date: 2019-01-22
forum: Multimedia Software
---

### Post by shag00 on 2019-01-22
Ubuntu 18.04.

Until the weekend I was hardware limited in regards to watching 4K, HDR movies so I upgraded my system to a Ryzon 5 2600K CPU (8 Gigs RAM) and a Nvidia 1050 graphics card which I use with VLC. The upgrade has some improvement over my old 6 year old CPU and no video card but falls short of good smooth viewing. As a test I watched Battleship last night and has 2 instances where the movie frooze for perhaps 2 or 3 seconds and many instances where the playback was slow without stopping. Voice synchronation was off about 200 ms but corrected through VLC with no further adjustment, it is possible this may have occurred when I transferred the BD to mkv.

Some Googling has led me to believe that VLC may be the problem, especially with mkv movies, although it's not clear to me if that is really the case. So my question is, what is the best movie player for mkv UHD movies for Ubuntu? Secondly, is my new hardware a likely culprit.

Thanks.

---

### Post by Autodave on 2019-01-22
Did you install a driver for your video card?  If so, what one and where did you get it from?

---

### Post by qyot27 on 2019-01-22
It could be a combination of factors, although I'd expect a Ryzen to be more than powerful enough to keep up even if it had to do all of this in software.

The graphics drivers could be the problem (as in, it could be leaking memory or it might not even be enabling hardware decoding at all).  Any automatic HDR tonemapping could be tripping things up.  I wouldn't immediately blame VLC, but you could try using mpv and see if it suffers from the same problem.  If it does, the problem is almost certainly in the graphics drivers.

---

### Post by shag00 on 2019-01-31
Sorry for the delay in responding. 

@ Autodave: I am using the Nvidea driver 390 metapackage, which I got from the Kubuntu repository.
@ qyot27:     I will perform a test on mpv for the video although after a brief look at the manual it seems not to cater for my needs. Like many of the players these days it seems to cater to the streaming crowd. Some of my UHD movies have a peak 100mb/s bitrate and use DTS-HD, although pass through is used. Having said that I have also experienced very similar issues using the Noveau drivers.

---

### Post by Yellow Pasque on 2019-02-02
mpv works well for local video playing as well as streaming. If you want hardware decoding on nvidia, you need a version of mpv built with nvdec. Try: [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

---

### Post by shag00 on 2019-02-19
Well I am happy to report back that I appear to have solved the issue by increasing my cache from 300ms to 20,000ms based on this very useful post:
[https://www.stellarinfo.com/blog/6-methods-to-play-4k-ultra-hd-video-in-vlc-player/](https://www.stellarinfo.com/blog/6-methods-to-play-4k-ultra-hd-video-in-vlc-player/)

---

