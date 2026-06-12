---
title: "[SOLVED] Convert OGG to WMA"
date: 2008-10-27
forum: Multimedia Software
---

### Post by Dr Small on 2008-10-27
I know there must be some way to do this, as Windows can do it. I need to find a way to convert an OGG vorbis (audio file) to a WMA (for my sister). I have tried SoundConverter on GNOME, and it does not convert to WMA.

I have also tried mplayer, but couldn't figure it out, although it should be able to do it. I've done a dozen searches and the results are always "convert WMA to OGG", which is opposite of what I need to do.

Any suggestions?
Will mplayer or ffmpeg do it, and if so, how?

---

### Post by FakeOutdoorsman on 2008-10-27
I'm not familiar with WMA, but ffmpeg will be able to do this. This will create a WMA file but with an mp3 audio stream.  I'm not sure if that is a proper combination, but it's what ffmpeg does by default:
```
ffmpeg -i Sputnik.ogg -ac 2 -ab 128k sputnik.wma
```
This next command will use ffmpeg's wmav2 codec.  I would expect this one to work in Windows:
```
ffmpeg -i Sputnik.ogg -acodec wmav2 -ac 2 -ab 128k sputnik2.wma
```
ac 2 = two audio channels / stereo
ab 128k = 128k audio bitrate
acodec wmav2 = tell ffmpeg to use the wmav2 audio codec instead of guessing.  You can see other available codecs, such as wmav1, with "ffmpeg -formats".

---

### Post by Dr Small on 2008-10-27
No matter what I try with ffmpeg, I get a "Segmentation fault" on the last line.

---

### Post by FakeOutdoorsman on 2008-10-27
Can you post the complete ffmpeg output?  What version of Ubuntu and ffmpeg are you using?

---

### Post by Dr Small on 2008-10-27
I tried it on my sister's computer (the first command) and it worked. Apparently she doesn't have the wmav2 codec (even though it is listed when I run the option '-formats'). At first I was trying this on my computer (ArchLinux) and apparently I have an older version of ffmpeg or something. (Sis's computer is Feisty Fawn).

Dr Small

---

### Post by FakeOutdoorsman on 2008-10-27
Although wmav2 may be listed, it may not be able to encode:
```
DEA    wmav2           Windows Media Audio 2
```
D = decode available
E = encoding available
A = audio codec

I tested the command in both Hardy using ffmpeg from the universe repo (ubuntu-updates) and in Arch using a hacked up PKGBUILD:
```

# Contributor: niQo <niqooo(AT)gmailDOTcom>

pkgname=ffmpeg-svn
pkgver=15712
pkgrel=1
pkgdesc="Complete and free Internet live audio and video broadcasting solution for Linux/Unix"
arch=(i686 x86_64)
url="http://ffmpeg.mplayerhq.hu/"
license=('LGPL')
depends=('lame' 'libvorbis' 'faad2' 'faac' 'xvidcore' 'zlib' 'x264-git' 'libtheora')
makedepends=('subversion')
#provides=('ffmpeg')
provides=("ffmpeg=`date +%Y%m%d`")
conflicts=('ffmpeg')
source=()
md5sums=()

_svntrunk=svn://svn.mplayerhq.hu/ffmpeg/trunk
_svnmod=ffmpeg

build() {
  cd "$srcdir"

  if [ -d $_svnmod/.svn ]; then
    (cd $_svnmod && svn up -r $pkgver)
  else
    svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
  fi

  msg "SVN checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$_svnmod-build"
  mkdir "$_svnmod-build"
  cd "$_svnmod-build"

  "$srcdir/$_svnmod/configure" \
  --prefix=/usr \
  --enable-gpl \
  --enable-libmp3lame \
  --enable-libvorbis \
  --enable-libfaac \
  --enable-libfaad \
  --enable-libxvid \
  --enable-libx264 \
  --enable-libtheora \
  --enable-postproc \
  --enable-pthreads \
  --disable-debug \
  --disable-ipv6 \
  --disable-ffplay \
  --disable-ffserver \
  --disable-vhook \
  || return 1

  make -j 2 || return 1
 #make doc/ff{mpeg,play,server}.1 || return 1

  make DESTDIR="$pkgdir" install || return 1
 #make DESTDIR="$pkgdir" install-man || return 1
}

# vim:set ts=2 sw=2 et:

```

---

### Post by Sef on 2008-10-27
>  (Sis's computer is Feisty Fawn).

Fiesty Fawn is no longer supported.  It would be best to [upgrade]("http://ubuntuforums.org/showthread.php?t=849915") her computer.   Probably best would be [Hardy Heron]("http://ubuntuforums.org/showthread.php?t=849915") as it has long term support.

---

### Post by Dr Small on 2008-10-27
> **FakeOutdoorsman said:**
> Although wmav2 may be listed, it may not be able to encode:
```
DEA    wmav2           Windows Media Audio 2
```

I tested the command in both Hardy using ffmpeg from the universe repo (ubuntu-updates) and in Arch using a hacked up PKGBUILD:

You were right, the wmav2 codec does not have the encode option for her computer. I'll be installing ffmpeg from that PKGBUILD, just as soon as I get x264-git installed from the AUR.

> **Sef said:**
> Fiesty Fawn is no longer supported.  It would be best to [upgrade]("http://ubuntuforums.org/showthread.php?t=849915") her computer.   Probably best would be [Hardy Heron]("http://ubuntuforums.org/showthread.php?t=849915") as it has long term support.
Yes, I know. I told her just today that I should install Hardy on her system and she told me, "Don't touch my system!"... She panics every time I install Ubuntu on it. :D

---

### Post by FakeOutdoorsman on 2008-10-27
> **Dr Small said:**
> You were right, the wmav2 codec does not have the encode option for her computer. I'll be installing ffmpeg from that PKGBUILD, just as soon as I get x264-git installed from the AUR.
Mines just an edited version of [ffmpeg-svn 13107-1]("http://aur.archlinux.org/packages.php?ID=5553").

---

### Post by Dr Small on 2008-10-27
Finally got it compiled, and it worked just like it's supposed to. Thanks for the explanations and the PKBUILD! Now I can convert ogg's to wma for my Sis :)

Dr Small

---

