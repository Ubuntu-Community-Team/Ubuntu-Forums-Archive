---
title: "Kubuntu - Amarok and general music codecs problem"
date: 2010-12-14
forum: Multimedia Software
---

### Post by tpprynn on 2010-12-14
I've spoken to people on the KDE forum about this but am a bit stumped. They advised me to change the phonon backend of Amarok from xine to phonon-backend-gstreamer or phonon-backend-vlc. The latter doesn't seem to be in the repositaries though someone on the KDE forum said otherwise. When I change to gstreamer, Amarok says it cannot play mp3 files.

Apparently Kubuntu 10.04's Amarok is a bit old too but I can't see how to update it - does this involve adding a ppa or something?

I've added two other database-type players, Exaile and Rhythmbox, both designed of course for other desktop environments, but they both give gripes about codecs too or won't play. The xine backend causes jumps in playback mentioned in another post.

I have installed the Kubuntu restricted extras, and I even added w32codecs and nonfreecodecs at one point, now removed (--purged).

I don't fancy moving to 10.10 as I like the 3 years of not messing about upgrading/reinstalling. I would ideally update just Amarok and KDE itself.

Any ideas here? Thanks.

---

### Post by Yellow Pasque on 2010-12-14
If you're going to use Lucid and gstreamer, do yourself a favor and add this PPA to your sources: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)
Make sure you install the "good, bad, and ugly" gstreamer packages as well as the fluendo mp3 package.

---

### Post by mc4man on 2010-12-14
In addition to the above suggestion, an excellent ppa  for any lucid multimedia user., I guess you could look at this ppa for an updated amarok in lucid

[https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

I have a kubuntu 10.10 I fool around on, in that case the xine backend works fine (libxine1-ffmpeg installed), the gstreamer backend also works when the plugins are installed (not sure if it will use the ffmpeg one, but I'd install anyway and the ppa Temüjin linked is the way to go for gstreamer plugins

---

