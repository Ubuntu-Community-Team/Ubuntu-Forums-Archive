---
title: "samrog131 disapear"
date: 2015-08-05
forum: Multimedia Software
---

### Post by janove75 on 2015-08-05
When you try an update on your ubuntu system 14.04, you may read:

```
W: Impossible de récupérer http://ppa.launchpad.net/samrog131/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found
```
```
W: Impossible de récupérer http://ppa.launchpad.net/samrog131/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
```
```
E: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
```

I tried to understand why.
I found the answer: Sam Rog have removed the PPA.

So two options:
1/ find an archive of PPA and adapt it by yourself
2/ take out samrog131 in your sources.list.d directory

---

### Post by barakli on 2015-08-07
Same problem. It looks PPA deleted. I used to use samrog ppa for ffmpeg. I found the alternative: [https://www.ffmpeg.org/download.html](https://www.ffmpeg.org/download.html)
Under the "Linux Packages" you can see the PPA link: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by monkeybrain20122 on 2015-08-07
> **barakli said:**
> Same problem. It looks PPA deleted. I used to use samrog ppa for ffmpeg. I found the alternative: [https://www.ffmpeg.org/download.html](https://www.ffmpeg.org/download.html)
Under the "Linux Packages" you can see the PPA link: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

I think mc3man's ffmpeg for Trusty is a static build. If you use ffmpeg as a standalone software it is fine. But I use it to compile other things so I need a shared version so in 14.04 it is either samorg or compile ffmpeg myself. But anyway the last version of ffmpeg from samorg would be up to date for quite some times to come. Most distros don't upgrade ffmpeg too often (or at all, like Ubuntu lts when it provided ffmpeg) anyway.

---

### Post by mc4man on 2015-08-11
> **monkeybrain20122 said:**
> I think mc3man's ffmpeg for Trusty is a static build. If you use ffmpeg as a standalone software it is fine. But I use it to compile other things so I need a shared version so in 14.04 it is either samorg or compile ffmpeg myself. But anyway the last version of ffmpeg from samorg would be up to date for quite some times to come. Most distros don't upgrade ffmpeg too often (or at all, like Ubuntu lts when it provided ffmpeg) anyway.

Yes the ffmpeg build in the multimedia ppa is for use of the ffmpeg binaries only, it's also not suitable  to be used to build sources against.

For the general user replacing libav shared libs with those from a recent ffmpeg in 14.04 has no value & could cause issues. It's only useful when sources are rebuilt against the ffmpeg libs.

ffmpeg shared for 14.04 is available [here]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6"), sources that could benefit from using ffmpeg libs are supplied, otherwise libav is bumped to libav11 & sources rebuilt against that are supplied.
(the ffmpeg in multimedia ppa will be the higher version as there will be no ABI/API concerns

Starting in 15.10 & completed in 16.04 FFmpeg will return as the default & sources will be built from it, life for users will be much simpler.

---

### Post by monkeybrain20122 on 2015-08-11
> **mc4man said:**
> 

ffmpeg shared for 14.04 is available [here]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6"), sources that could benefit from using ffmpeg libs are supplied, otherwise libav is bumped to libav11 & sources rebuilt against that are supplied. 

Thanks. Is ffmpeg installed in /opt or /usr? just wondering. I am maintaining a fallback 14.04 install so probably will switch to the ppa this weekend. But if it is install in a different location may have to change a few things in environmental variables and probably rebuild something..

> Starting in 15.10 & completed in 16.04 FFmpeg will return as the default & sources will be built from it, life for users will be much simpler.
It will probably be quite out of date and with missing non free extras going by past experience. So it will be great if you still provide a ppa for it. :)

---

### Post by monkeybrain20122 on 2015-08-11
There is a ppa which restores the ffmpeg part of samrog's for Trusty [https://launchpad.net/~adrozdoff/+archive/ubuntu/ffmpeg-opti]("https://launchpad.net/%7Eadrozdoff/+archive/ubuntu/ffmpeg-opti")

---

### Post by mc4man on 2015-08-11
> **monkeybrain20122 said:**
> Thanks. Is ffmpeg installed in /opt or /usr? :)
It installs completely to /usr
Only sources that have been built off of it specifically will use it's shared libs, otherwise apps will use libav11's shared or the default libav9 shared. 
The 2(3) sets of shared libs coexist peacefully, however only one set of -dev packages can be installed at a time.
See screen, 3 libavcodec's are installed here currently  based on packages using them.

---

### Post by mc4man on 2015-08-11
Also here FFmpeg is supplied via the multimedia ppa, not using the one produced via the shared build. The advantage there is it can kept being updated from git master without concern for breakage of other apps. If something newer can be used I've the option of adding to that build statically. Currently dcadec & libvpx2 (1.4) are statically linked.

---

