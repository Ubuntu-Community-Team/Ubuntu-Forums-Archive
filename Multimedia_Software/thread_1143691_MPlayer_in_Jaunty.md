---
title: "MPlayer in Jaunty"
date: 2009-04-30
forum: Multimedia Software
---

### Post by teonghan on 2009-04-30
Hi all,

Just upgrade my Intrepid to Jaunty last night. After upgrading, I played some movies using SMPlayer and it commented that MPlayer version is outdated. I tried updating and look for new version in MPlayer website and the version I have is the latest one. Though, my videos played without any problem, I tend to have latest version of updates for Ubuntu. Any idea? Do that new version I need is that from SVN?

Thanks in advance.

---

### Post by fornix on 2009-04-30
I had the exact same problem. Smplayer complained that mplayer is not the latest one and that I may experience some problems (especially subtitles)
Though movies do play properly.

---

### Post by teonghan on 2009-04-30
> **Ellen2 said:**
> There is some preparation required for installing the updated mplayer in Jaunty. You may like to check this how-to tutorial for this. Check it over here [http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

Thanks. Will try that later and see. As far as the tutorial is concerned, I think the possible solution is to compile the SVN version of MPlayer, I guess.

---

### Post by kpkeerthi on 2009-04-30
[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/~rvm/+archive/mplayer")

---

### Post by andrew.46 on 2009-04-30
Hi teonghan,

> **teonghan said:**
> Thanks. Will try that later and see. As far as the tutorial is concerned, I think the possible solution is to compile the SVN version of MPlayer, I guess.

As kpkeerthi has suggested an easier option than compiling the svn MPlayer yourself is to use the version of MPlayer that rvm has been good enough to provide in his PPA.

I suspect that when Karmic Koala is released the svn MPlayer guide that I have produced for so many years will not be rewritten as PPAs are really the way to go these days. 

All the best,

Andrew

---

### Post by teonghan on 2009-05-01
kpkeerthi and andrew.46,

Thanks for the feedback. As pointed out by andrew.46, installing latest mplayer is easier through launchpad PPA. Following the guide in [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer), I have already updated my mplayer to the latest SVN.

Thanks!

---

### Post by andrew.46 on 2009-05-01
Hi teonghan,

> **teonghan said:**
> As pointed out by andrew.46, installing latest mplayer is easier through launchpad PPA. Following the guide in [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer), I have already updated my mplayer to the latest SVN.

Good to hear! Mind you I will find it hard letting go of that MPlayer guide which I have been fine tuning for so long... But as I mentioned before the PPA seems to be the way for such software now.

Andrew

---

### Post by bofphile on 2009-05-01
Is there a launchpad PPA for mplayer compiled with ffmpeg-mt ?

Thanks.

---

