---
title: "Audacious won't show Ogg Vorbis embedded cover art"
date: 2014-04-19
forum: Multimedia Software
---

### Post by Gilad_Pellaeon on 2014-04-19
Has anyone who plays ogg vorbis files noticed that Audacious has stopped showing embedded cover art? I seem to recall around a year ago it worked fine and Audacious displayed cover art in Lubuntu 13.04. But, no matter what distro i've tried, and i've tried Ubuntu/Xubuntu/Lubuntu 13.10/14.04, Linux Mint XFCE 16, even tried the windows version of Audacious on my old Windows XP install and audacious will just not show the cover art. Whereas for example running Foobar, a semi popular Windows media player program, it displays the embedded cover art with no problems whatsoever. 

Overall i'm just curious if i'm the only one who has encountered this or is it something that's maybe changed with how the various distro's have been handling ogg vorbis files? I haven't tested other media player's included in the various distro's mentioned above to see if they even handle embedded cover art with no problems, but it is kind of a frustrating issue that's holding me back on finally replacing my older Lubuntu 13.04 on this machine with a fresh install of Xubuntu 14.04 alongside Windows XP.

---

### Post by andrew.46 on 2014-04-19
There is an interesting, if somewhat dated, discussion of this problem here:

[https://wiki.xiph.org/VorbisComment#Playback_tests](https://wiki.xiph.org/VorbisComment#Playback_tests)

with a couple of test files. Certainly on my system audacious plays the first of these files with the cover-art displayed, as does MPlayer and vlc. I attach a screenshot of audacious in action. (This is audacious 3.3.4.)

---

### Post by mc4man on 2014-04-19
I don't see any issue here either, at least with art embedded with easytag.
I do have a file where the art was embedded as a video stream (dbpoweramp), in that case audacious has an issue with but a bit more drastic, won't play it at all.

---

### Post by Gilad_Pellaeon on 2014-04-21
Hmm i've embedded my cover art with mp3tag [http://www.mp3tag.de/en/](http://www.mp3tag.de/en/) - both in my windows install and through WINE in the past with no issues. The Audacious version's I had tested were 3.43 and up so I'm thinking it could be version related most likely or, less likely, something to do with the ogg vorbis librarie(s) that handle ogg vorbis files. Playback of the files is fine in any distro i've tried as mentioned in my first post. I've went and posted on the Audacious forums so maybe this will shed some light on the issue so to speak.

[http://redmine.audacious-media-player.org/boards/1/topics/1170](http://redmine.audacious-media-player.org/boards/1/topics/1170)

---

### Post by andrew.46 on 2014-04-21
Something wrong with your copy of audacious I suspect, I attach a screenshot of audacious playing your file + cover art...

---

### Post by Gilad_Pellaeon on 2014-04-22
> **andrew.46 said:**
> Something wrong with your copy of audacious I suspect, I attach a screenshot of audacious playing your file + cover art...

But that doesn't make sense when I tried all live USB distro's without installing them to the hard drive and then I tried the windows version of Audacious. I'm beginning to wonder if maybe it's something related to the library file(s) that handle ogg vorbis decoding? You just proved it's not audacious doing it as it's showing the cover art in KDE just fine.

---

### Post by andrew.46 on 2014-04-22
> **Gilad_Pellaeon said:**
>  You just proved it's not audacious doing it as it's showing the cover art in KDE just fine.

This is a Slackware installation mind you, I am between Ubuntu installations at the moment, but this should make no difference. Nice album art btw if perhaps a little racy :)

---

### Post by Gilad_Pellaeon on 2014-04-22
> **andrew.46 said:**
> This is a Slackware installation mind you, I am between Ubuntu installations at the moment, but this should make no difference. Nice album art btw if perhaps a little racy :)

I always liked it for like 3 or 4 files in my collection that was just old .MOD files outputted to ogg vorbis compression. Old musical favorites from my youth in the 90's! :D At any rate now just waiting to hear what the developer of Audacious has to say in the meantime as i'm running Xubuntu 14.04 on my system now and Audacious still won't show the cover art :rolleyes: but it plays my music just fine.

---

### Post by Gilad_Pellaeon on 2014-04-22
Well it turns out the 3.5 beta 1 release of Audacious does seem to fix my problem but alas for me it's been a real pain in the rear to compile the sources and get it running only to find out it still was missing a bunch of plugins and could only output to filewriter *facepalm*. So back to 3.43 for me I guess. Turns out that embedded cover art over 256kb in size is not being properly recognized in some instances - as mentioned on bug fixes since 3.43 on the website for audacious. Oh and of course wepupd8 ppa doesnt seem to have 3.5 beta 1 in a nice deb file to install (yet).

"Ogg Vorbis files with tags larger than 256 KB not recognized correctly"

---

### Post by Yellow Pasque on 2014-04-23
If you're going to build software, you need appropriate -dev packages. This command will get you pretty far (need to enable source repos first):
```
sudo apt-get build-dep audacious audacious-plugins
```

---

### Post by Gilad_Pellaeon on 2014-04-23
> **Temüjin said:**
> If you're going to build software, you need appropriate -dev packages. This command will get you pretty far (need to enable source repos first):
```
sudo apt-get build-dep audacious audacious-plugins
```

I ended up compiling the more painful way by finding out I needed dev packages for a few things as it complained of missing dev packages and then finally audacious and audacious-plugins compiled to the point the beta loaded anyways, just couldn't play anything.

---

### Post by Yellow Pasque on 2014-04-23
You probably needed libpulse-dev installed so you could output to something other than filewriter ;)

---

### Post by mc4man on 2014-04-23
If you can't get your compiled version working correctly then for 14.04 I have packages in a ppa ( 0.3.5 release.
If so i'd remove/uninstall your builds ect.,  inc. any other updated sources, if any
(0.3.5 wants newer versions of libquess1 & libmowgli-2, those are provided in ppa
 here - [https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

also available for limited time in a standalone testing ppa though that ppa will be moving to 0.3.6-alpha in the near future - 
[https://launchpad.net/~mc3man/+archive/audtests](https://launchpad.net/~mc3man/+archive/audtests)

---

### Post by andrew.46 on 2014-04-24
New version running nicely here after [a bit of a tussle]("http://www.linuxquestions.org/questions/slackware-14/lost-icons-audacious-3-5-a-4175502664/") :). Audacious remains my favourite gui music player and it is great to see the developers working away at it...

---

### Post by Gilad_Pellaeon on 2014-05-03
Well im happy to say after doing this to get H.264 video playback enabled in firefox (for youtube mostly) with the gstreamer0.10-ffmpeg package and it's dependencies

```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg

```

I was happily able to upgrade Audacious to 3.5 beta with the regular software updater included with Xubuntu 14.04 and now it's working great like a charm so far. Listening to my music and seeing my album art yay! :)

---

