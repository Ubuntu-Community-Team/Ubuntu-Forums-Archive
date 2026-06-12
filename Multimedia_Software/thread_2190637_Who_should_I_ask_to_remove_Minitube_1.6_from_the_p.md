---
title: "Who should I ask to remove Minitube 1.6 from the precise repos?"
date: 2013-11-28
forum: Multimedia Software
---

### Post by lads on 2013-11-28
Hello everyone,

I tried today MiniTube for the first on Ubuntu 12.04 and it simply doesn't work. There are loads of reviews on the Software Centre from 12.04 users saying exactly the same. [I contacted the developer]("http://flavio.tordini.org/forums/topic/how-to-play-videos#post-90539") and he simply told me to **buy** a newer version of MiniTube.

It seems to me that MiniTube 1.6 is a nothing more than a decoy for commercial software. I'm not against the distribution of commercial software through the Software Centre, but this sort of decoys are dispensable. Who should I contact or how should I proceed to request the removal of this package from the repos?

Thanks.

---

### Post by mc4man on 2013-11-28
The cost of "buying" it thru software-center is zero, as in free.

---

### Post by vasa1 on 2013-11-28
But [https://apps.ubuntu.com/cat/applications/minitube-ubuntu/](https://apps.ubuntu.com/cat/applications/minitube-ubuntu/) has it for US$ 3.99.

---

### Post by lads on 2013-11-28
> **mc4man said:**
> The cost of "buying" it thru software-center is zero, as in free.

In Ubuntu 12.04 it is US$ 3.99.

---

### Post by mc4man on 2013-11-28
> **lads said:**
> In Ubuntu 12.04 it is US$ 3.99.

Too bad, I  guess since I 'purchased' it in the past that it's free here on any install I have  or will have (based on sso 

At this point it's also not as good as before, changes in youtube aren't fixed as fast as previously when the code was open.
(I find smtube to be better in some regards, updated quicker, ect.

As far as requesting removal that could be done in a launchpad bug report, whether the old non working are removed you'd have to see.

---

### Post by monkeybrain20122 on 2013-11-28
Not sure if 1.6 is a decoy. Minitube from the repo almost never worked as far as I can remember because Google keeps changing Youtube formats. Minitube 1.6 is ancient since it hasn't been updated since Precise came out and Youtube has gone through so many changes I would be very surprised if it works!

 I used to always get the latest Linux binary from its website. I haven't used it since 11.04 or 11.10. It used to be a paid app for  Windows and Mac but free for Linux. I checked just now because of your  thread and saw there was a download link for Ubuntu (instead of just  Linux) but it had no package.

The source code ( minitube 2.1.3)is still free. 

[http://flavio.tordini.org/minitube/minitube-sources](http://flavio.tordini.org/minitube/minitube-sources)

It is easy to build.  Install the dependencies
```
sudo apt-get install build-essential qt4-dev-tools libphonon-dev

```

untar the minitube source tarball, cd into the minitube directory
then run

```

qmake-qt4
make

```

That's it. The binary is in minitube/build/target, just click on it to start.
If you want to install it in your system. Run after "make" (still in the directory minitube)

```

sudo make install

```
** Or **, if you have checkinstall installed.

```

sudo checkinstall 

```

I just compiled it and it worked in 13.04. In 12.04 there was some gstreamer bug or something, may not work without some further tweaks. Check out the minitube forum if it doesn't work.

---

### Post by lads on 2013-11-29
Thanks for the tip monkeybrain. I still think the package should be removed from the repos.

---

### Post by monkeybrain20122 on 2013-11-29
I agree. Software known to be broken should not be in the repo (not particularly against minitube, just a general point. Many multimedia software in Ubuntu's repo are out of date or broken especially for LTS just because of the feature freeze, I don't think minitube 1.6 is deliberately put there as a decoy). 

I noticed that the license for minitube-ubuntu (the up to date version that costs $3.99) in the USC is "proprietary". Has minitube gone non-free? So the source he provides is missing some functionalities (maybe downloading?) Anyway, I haven't used it for quite a while, I prefer smtube because I use Smplayer, and it works better too (Minitube was quite buggy and used a lot more cpu cycles on my system than anything based on mplayer because of vdpau).

---

