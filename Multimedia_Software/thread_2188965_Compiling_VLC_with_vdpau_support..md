---
title: "Compiling VLC with vdpau support."
date: 2013-11-20
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2013-11-20
Hi, 

I am trying to compile vlc 2.1 (or 2.2 from git) on raring with vdpau support. I basically follow this guide
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

The idea is  to compile vlc against a local version of ffmpeg instead of the system copy(which is avconv). Since vdpau support for VLC requires libvdpau >=0.6, I downloaded a tarball from [http://cgit.freedesktop.org/~aplattner/libvdpau/](http://cgit.freedesktop.org/~aplattner/libvdpau/)
untarred it in the directory vlc_build  and compile a local version as follows
```
cd vlc_build/libvdpau-0.6
./autogen.sh
./configure --prefix=$HOME/vlc_build/vlcdeps/usr
make
make install
```

It went through without error and I could see that the libvdpau files were installed in vlc_build/vlcdeps/usr/include and vlc_build/vlcdeps/usr/lib

I compiled vlc following Andrew's guide (CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include " \ LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \ PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig") Running ./configure --enable-vdpau returned error that libvdpau 0.6 or above was required and that only libvdpau 0.4 was found, so apparently it didn't see the local version. There was also another error that said libavcodecs >=54.36.0 was required. I have compiled the local version of ffmpeg from git, I don't know which version of libavcodecs it is, but I have the feeling that ./configure has simply ignored the local version.

Please help, thanks.

---

### Post by Yellow Pasque on 2013-11-20
I actually packaged libvdpau 0.6 (was intending to use it for someting else, but that's irrelevant). Feel free to use it if it helps: [https://launchpad.net/~dtl131/+archive/uvd](https://launchpad.net/~dtl131/+archive/uvd)

---

### Post by monkeybrain20122 on 2013-11-23
Bump!

---

### Post by Yellow Pasque on 2013-11-23
So did you use the vdpau package from my PPA or not? Results?

---

### Post by monkeybrain20122 on 2013-11-23
Hi,

I haven't tried your build yet. My problem is that I am not sure whether vlc is actually looking for the local libraries with those options. As I have indicated in my first post, it seemed to be using the system version of libavcodecs as well (so even if a system install of libvdpau from your ppa works, I would still get an error about outdated libavcodecs). I think my build of libvdpau probably works too, only if vlc build can find it.

Thanks.

---

### Post by mc4man on 2013-11-24
While i've no real use use for vdpau in vlc here (currently just using intel side of a 660m) I did give a quick try to building vlc with vdpau in a similar though not exact manner as Andrew's guide & there was no issue at all.
(I already have a static ffmpeg/x264 with the includes & libs installed to  /opt/ffmpeg-current so just linked to there in the configure.

So maybe you're not following that part of guide exactly or possibly, if you have libav -dev packages installed,  they're causing your issue. If so then I'd remove them
For libvdpau i'd use the ppa, then try again (not an issue here in 14.04 as libvdpau is @ 0.7+

(as a side note - while I am using intel,  I can get vdpau in mplayer & mpv thru libvdpau-va-gl1 & it works quite well, however in vlc  it's awful though I'd hope with nvidia it actually has some value..

---

### Post by monkeybrain20122 on 2013-11-24
Hi,

I think I did link to the local ffmpeg. I will give it a try by removing the libav-dev files. 

I have installed an arch build of VLC 2.1.1 from AUR on another partition. Even though vdpau option is present but has to disable it or video just stops. Not sure if it is a VLC problem or Arch build or other things. Will try to build it in Ubuntu and see if it works better.

Thanks.

---

### Post by monkeybrain20122 on 2013-12-13
It works! 

Since I was going to update to Saucy soon I didn't bother doing this in raring. I compiled vlc 2.1.2 (the latest stable) in Saucy and vdpau definitely works, though not as good as mplayer/mplayer2.

The libvdpau version in saucy is up to date, but to get libavcodecs >=54 so you need an up to date version of ffmpeg. You can compile it yourself,--but must enable shared,-- but there is a new ppa that features real ffmpeg [https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa) (Jon Severinsson's ppa is well known but it is too old for compiling vlc 2.1.2) It installs ffmpeg in /opt/ and you can install as well the package ffmpeg-set-alternatives which will then allow you to choose which ffmpeg to be the system default (command: sudo update-alternatives --config ffmpeg then pick the one, which will create a symlink to /usr/local and its target changes depending on the update-alternatives command)

Then install the dependencies (either sudo apt-get build-dep vlc or copy the list from andrew.46's guide linked in the first post but some of the packages listed may be outdated (libhal?) and no longer in the repo ) After installing the dependencies install the ffmeg-real-dev files from the ppa.This will remove the corresponding libav-dev files in the system. So if you intend to run sudo apt-get build-dep vlc to get the dependencies you should do this after, or apt-get build-dep would not run because the libav-dev files are uninstallable.

Download tarball for vlc 2.1.2 from videolan, untar, cd into it and run ./bootstrap. Before configuring run
```

CPPFLAGS="-I/opt/ffmpeg/include"
LDFLAGS="-L/opt/ffmpeg/lib"
PKG_CONFIG_PATH="/opt/ffmeg/lib/pkgconfig"
export CPPFLAGS LDFLAGS PKG_CONFIG_PATH


```

This is to instruct the build process to find the correct ffmpeg libraries (libavcodecs etc) from the ppa. I am not sure if it is necessary after setting the ppa's ffmpeg to be default. But I did it anyway.

Then just ./configure make and sudo make install (or sudo checkinstall)

Don't need to supply any option to enable things since vlc 1.5 or something, it picks up on its own which features can be enabled on your system.

Once vlc is installed successfully (in user/loca) run ```
sudo ldconfig
``` , since I haven't removed vlc2.0.8 before I compiled and it was in /usr. If you remove it first then you don't need to do this.. (I couldn't ./configuring vlc with prefix /usr  because I couldn't remove all vlc packages yet,--because of phonon-backend-vlc,--and that caused a conflict)

Finally I had problem with phonon-backend-vlc because the repo version doesn't work with vlc2.1.2 so I have to compile 0.7.1 from source and for that I needed a newer version of phonon (repo's version gave errors about unknown qt5 symbol or something, even though this uses qt4), which I got from [https://launchpad.net/~mati75/+archive/mint-lxde](https://launchpad.net/~mati75/+archive/mint-lxde)
Finally I removed all packages associated with vlc2.08 since phonon-backend-vlc didn't depend on them any more. I only keep vlc-data because it contains icons and stuffs like that.

Now everything is working. :) As a bonus I can open some .flv files that I wasn't able to in  Ubuntu or Debian because these distros compile their mediaplayers with  avconv, instead of ffmpeg and avconv for some reasons cannot play these files.

---

