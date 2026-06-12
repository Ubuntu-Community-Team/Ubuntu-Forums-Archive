---
title: "Lubuntu. VLC crash with audio visualization"
date: 2015-03-14
forum: Multimedia Software
---

### Post by ruslan5 on 2015-03-14
I've compiled VLC from git.
When I do Audio->Visualization->Spectrum, VLC crashes with Segmentation fault (core dumped).
VLC installed from Lubuntu Software Center works well.
Lubuntu 14.04.
Any ideas how to fixed it?
Thanks in advance.

---

### Post by mc4man on 2015-03-14
Could be a host of reasons
1. You got a git where it's broken
2. Your config/build is lacking
3. Maybe you left some elements of the packaged vlc installed, it should be completely removed prior to building your own.

I've got a git master from yesterday, it's fine in this regard. I can't tell you the exact git head because I get the source from alternate means & I build it in a personal ppa with changes I want. (uses ffmpeg-shared, fdkaac enabled, an add. .desktop & binary for proper audio cd autoplay, ect.

Maybe try the latest git or use a slightly older git source to check.
Or for the moment remove your build, add this ppa, install vlc & see how it works. 
[https://launchpad.net/~videolan/+archive/ubuntu/master-daily](https://launchpad.net/~videolan/+archive/ubuntu/master-daily)
(- you can always remove the ppa vlc & disable the ppa afterwards. To completely remove the ubuntu repo or ppa vlc just go this, it will remove All vlc source packages - 
```
sudo apt-get purge vlc-data
```

---

### Post by andrew.46 on 2015-03-14
I compiled vlc-git 5 minutes ago:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 3.0.0-git Vetinari (revision b8c639d)
VLC version 3.0.0-git Vetinari (b8c639d)
Compiled by andrew on corinth (Mar 15 2015 08:29:31)

```

and both the ordinary spectrum visualisation and also one I had not seen before called '3d spectrum' worked flawlessly. I followed this guide:

Compile vlc-git under the latest Ubuntu release...
[http://www.andrews-corner.org/ubuntu/vlc.html](http://www.andrews-corner.org/ubuntu/vlc.html)

which also seems to have been updated today :). Can I ask why you need the development version of vlc rather than the recently released version?

---

