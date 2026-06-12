---
title: "How to download version 3 of ffmpeg on Ubuntu 16.04"
date: 2019-05-07
forum: Multimedia Software
---

### Post by notsej-user on 2019-05-07
[FONT=Arial]I have been trying to install ffmpeg version 3 on my machine (which is running Ubuntu 16.04). To do so I have been using the following commands:[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]sudo add-apt-repository ppa:jonathonf/ffmpeg-3[/FONT]
[FONT=Arial]sudo apt update && sudo apt upgrade[/FONT]
[FONT=Arial]sudo apt install ffmpeg[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]However, when I run ffmpeg -version I always get:[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]ffmpeg version 2.8.15-0ubuntu0.16.04.1 Copyright (c) 2000-2018 the FFmpeg developers


I have tried uninstalling and reinstalling in many different ways, restarting my machine, etc. I also consulted with someone who has experience in Linux and I can't seem to figure out the issue. I want version 3 or higher but I alway get version 2.8.15.


Any suggestions or tips would be greatly appreciated.
[/FONT]

---

### Post by #&amp;thj^% on 2019-05-07
Maybe try to remove the PPA it has not received any updates since 41 weeks ago.
Though there is FFMPEG-4 PPA by the same maintainer: [https://launchpad.net/~jonathonf/+archive/ubuntu/ffmpeg-4](https://launchpad.net/~jonathonf/+archive/ubuntu/ffmpeg-4)
This however "may" leave certain apps in a non-fully workable state, >>>SO USE AT YOUR OWN RISK!<<<
Backport of FFMPEG-4 and associated libraries. Now includes AOM/AV1 and FDK AAC support!

---

### Post by notsej-user on 2019-05-07
Hi,

Thanks for the tip. I have tried adding ffmpeg-4 instead of ffmpeg-3 but I still get version 2.8.15. I've seen others follow the same commands as I used above with Ubuntu 16.04 and they were able to download version 3.3 or higher so I thought it may have something to do with my machine rather than the repository.

---

### Post by mc4man on 2019-05-07
> **notsej-user said:**
> Hi,

Thanks for the tip. I have tried adding ffmpeg-4 instead of ffmpeg-3 but I still get version 2.8.15. I've seen others follow the same commands as I used above with Ubuntu 16.04 and they were able to download version 3.3 or higher so I thought it may have something to do with my machine rather than the repository.
That ppa should be 'ok' as the shared ffmpeg libs are different versions than what's normally used in 16.04. However they are pretty useless as nothing will use them  other than the ffmpeg binary (useless you build sources against them.
The inclusion of aom/av1 is similarly useless as aom is a poor decoder and incredibly slow encoder ( I did a very high quality 45 sec encode here on admittedly older hardware ( haswell), took 7 hrs, a less challenging 30 sec encode took 2.5 hrs..

Anyway run  this to see what's up.
```
apt-cache policy ffmpeg
```
Alternately you could try the ffmpeg snap, probably works ok and should be available to 16.04.

Also available is a build I have for 16.04, at this point rarely updated, currently though has ffmpeg git master as of today. It cannot cause any issues as installed to /opt, it cannot be used to build against. It's soley for use of the ffmpeg binaries. 
This ffmpeg, due to concerns 3 years ago about conflicting with 16.04 apps that use the ffmpeg binary is done a little different. Everything is installed out of PATH to /opt, the 3 ffmpeg binaries are symlinked to /usr with a new name. This way it can co-exist with the repo ffmpeg.
The package name is ffmpeg-static, the commands are 
ffmpeg2
ffprobe2
ffplay2

[https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test)

(- 18.04 will receive more attention from me, [seen here ]("https://launchpad.net/~mc3man/+archive/ubuntu/bionic-media")

---

### Post by jonathonf on 2019-06-30
> **mc4man said:**
> However they are pretty useless as nothing will use them  other than the ffmpeg binary

Unless you want the ffmpeg binary.

> **mc4man said:**
> The inclusion of aom/av1 is similarly useless as aom is a poor decoder and incredibly slow encoder

Unless you want the AOM encoder.

;)

---

### Post by andrew.46 on 2019-07-12
> **mc4man said:**
> The inclusion of aom/av1 is similarly useless as aom is a poor decoder and incredibly slow encoder ( I did a very high quality 45 sec encode here on admittedly older hardware ( haswell), took 7 hrs, a less challenging 30 sec encode took 2.5 hrs..

The addition of a tiling option has meant encoding speed has picked up a little, not immensely though I confess. A 15 minute lossless video took about 10 hours here with 2 pass, some early thoughts [here...]("http://www.andrews-corner.org/ffmpeg/av1.html")

---

### Post by mc4man on 2019-07-12
> **andrew.46 said:**
> The addition of a tiling option has meant encoding speed has picked up a little, not immensely though I confess. A 15 minute lossless video took about 10 hours here with 2 pass, some early thoughts [here...]("http://www.andrews-corner.org/ffmpeg/av1.html")
Glad to see your site is still active..
The last encode I did was 11 months ago, was using tiling though then ffmpeg needed to be patched to do so. ( and I patched libaom to do webm) I gather no patches needed now.
Have a newer windows laptop with much better cpu, maybe I'' try again.
The more interesting part back then was I found a gui for the av1 encode which gave me the basic 2 pass options which I then  modified to suit. Don't know it's current state - 
[https://github.com/Kagami/boram](https://github.com/Kagami/boram)

---

### Post by andrew.46 on 2019-07-13
> **mc4man said:**
> Glad to see your site is still active..

I still potter around with the site :). I love writing HTML and I was taught to be a little pedantic with it in the early days, this has paid off with simple HTML that renders well in different browsers. Not done commonly these days though where people are using page generators, wordpress etc etc...

> The last encode I did was 11 months ago, was using tiling though then ffmpeg needed to be patched to do so. ( and I patched libaom to do webm) I gather no patches needed now. 

No patching required with the latest and greatest FFmpeg but I am not sure which release version would work. If you are interested in patching for a faster AV1 encode there is a patch on FFmpeg-devel last month or 2 to allow encoding with rav1e (Rust AV1 Encoder) which promises great things in the future.


> Have a newer windows laptop with much better cpu, maybe I'' try again.

I also have new build, this time with Threadripper CPU, bought especially so that I could really come to grips with video and audio encoding!

> The more interesting part back then was I found a gui for the av1 encode which gave me the basic 2 pass options which I then  modified to suit. Don't know it's current state - 
[https://github.com/Kagami/boram](https://github.com/Kagami/boram)

I have not investigated any guis yet, I suspect with a little massaging WinFF could even cope with AV1 encoding. I see no great development with WinFF lately but the presets are always fairly easy to write.

And BTW: Nice to be back in the Ubuntu Forums :)

---

