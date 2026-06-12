---
title: "FFmpeg built from SVN source and package dependencies."
date: 2009-07-14
forum: Multimedia Software
---

### Post by Krazen on 2009-07-14
Hello.

I have compiled ffmpeg myself on my system because I need to have full control over its configuration. FFmpeg is working just fine, but I have problem with installing some packages from repositories.

Many packages (especially those related to multimedia) depend on ffmpeg, libavformat, libavcodec etc. I have that all already compiled in my system and installing, for example, libavformat52 package from repositories makes my ffmpeg crash.

Is there any way to install all those packages depending on ffmpeg and stuff, such as gstreamer0.10-ffmpeg on my machine? I tried:

```
dpkg -i --force-depends package_name.deb
```

but packages installed that way are not working properly.

I guess making ffmpeg and its libraries that are already compiled and installed fill those dependencies would be proper way of solving my problem but I have no idea how to do that.

---

### Post by FakeOutdoorsman on 2009-07-14
It is trickier using apt based systems to compile and satisify dependencies that some other package managers, but it definately isn't impossible.  By default, self compiled software should by default install to */usr/local*, while the package manager should install to */usr*.  This separation usually allows you to have your compiled software and satisify the package manager's dependencies.  I, admittedly with some bias, recommend this guide:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

It uses checkinstall to integrate nicely with the package manager.  You may be interested in trying a distro that is more friendly for compiling.  Both Arch Linux and Slackware are worth trying out and have a "ports-like" system.  From the Arch Linux Wiki:

> [ What is a ports-like system?](http://wiki.archlinux.org/index.php/ABS#What_is_a_ports-like_system.3F)

'Ports' is a system used by *BSD, which allows source packages to be downloaded, unpacked, patched, compiled and installed. A 'port' is merely a small directory on the user's computer, named after the corresponding software to be installed, which contains a few files with instructions for downloading and installing an application from source, typically by navigating to the directory, or port, and doing 'make' and 'make install'. The system will then download, compile and install the desired software. 

---

### Post by igorzwx on 2009-07-14
When they are going to fix the bug with frame rate (X11grab)?

---

### Post by mc4man on 2009-07-14
Another thing you could consider  if sticking with jaunty is to build a current or recent ffmpeg as a debian package set to /usr as shared libraries.
It will then integrate nicely with apps that depend on ffmpeg liraries and you'll have unstripped libraries with matching -dev's (which isn't  possible to do from the repo.

There will be no issue installing jaunty packages and then ones that use the ffmpeg libraries will use the new ones.
If they require a lesser version # then that will also install cleanly

Ex. the gstreamer-ffmpeg plugin uses the same ver. # of libavcodec but a lesser libavutil (49 vs. 50 ) Both can co exist so gstreamer-ffmpeg will install and run properly (or you can build it off of the new libav*'s, same method 

Fairly easy to do using a good debian.diff, just need to decide on configure options, whether to include amr and if so, the older ones or the curreny 'open' ones. (source dependant on that
Also whether to include vdpau or not, dirac, ect.

I do this for hardy, but simple on jaunty, just did a set on the live cd

Screen shows ffmpeg install, gtreamer-ffmpeg  installs fine, as do other ffmpeg lib dependant apps (note that the libs are listed without saying 'un-stripped' but the are the full un-stripped versions

Default conf. options from this .diff minus the opensource amr's, easy to add, the options can be tuned as you need

> ubuntu@ubuntu:~$ ffmpeg
FFmpeg version SVN-r19424, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g --libdir='${prefix}/lib' --shlibdir='${prefix}/lib' --bindir='${prefix}/bin' --incdir='${prefix}/include/ffmpeg' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir='${prefix}/share/man' --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --enable-libopenjpeg --enable-version3 --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jul 14 2009 18:53:38, gcc: 4.3.3
 

---

### Post by igorzwx on 2009-07-14
It seems that you get 2fps with x11grab on any box.

A friend send me this message:

it's ffmpeg doing a bad job, nothing to do with PC power.
  
 see this, [http://www.mail-archive.com/ffmpeg-issues@live.polito.it/msg02014.html](http://www.mail-archive.com/ffmpeg-issues@live.polito.it/msg02014.html)
  
 so, there is nothing we can do, but wait for a fix....

---

### Post by Krazen on 2009-07-27
**mc4man** when I try to do that I get only "ffmpeg" package marked as installed in Synaptic.

You said:

> Fairly easy to do using a good debian.diff

Could you please explain this to me, I'm not familiar with diff and I guess it's important here.

Thanks in advance.

---

### Post by mc4man on 2009-07-27
If building and installing a current ffmpeg as a package set with shared libs is what you need I'll certainly give you enough info to get started.
To some extent you'll need to figure some things out and modify to suit your needs. (I'm still doing that myself

A few suggestions first

Post what release of ubuntu your using, the assumption would be jaunty i386

Post your built ffmpeg configure and how installed

(( your problems seem to indicate you configured ffmpeg with --enable-shared

If your reason for building and installing a svn ffmpeg is confined to the use of ffmpeg itself and the jaunty unstripped ffmpeg libs are good for your use of apps that use them then....

Use FakeOutdoorsman guide - you can add to the configure if desired, just don't add --enable-shared

If you need shared ffmpeg libs configured differently and or more current than the repo's unstripped ones than building and installing as I mentioned is the best way (as I see it


If so let me know, Though I think if you remove what you've done, follow the guide, and use the repo's unstripped libs you may be fine.

While I'm on the jaunty live cd I'm posting a screen that show ffmpeg built with same method that created the ones in above screen.
The above one used debian-multimedia's july 20 source and diff, with minor changes to some of the debian files

Below is using the same diff (it's still  good because ffmpeg hasn't changed much in a week
I made a few additional changes so the packages reflected a new source, the ffmpeg folder is the checked out source, the ...tar.gz is the source repacked after applying the diff and various edits, wmapro patch, but before the build
(this way if i made a mistake or need an adjustment I can delete everything but the ..tar.gz, re-extract and not have to start from scratch

in this case I enabled the opensource amr 
> 
ubuntu@ubuntu:~$ ffmpeg
FFmpeg version SVN-r19521, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --libdir='${prefix}/lib' --shlibdir='${prefix}/lib' --bindir='${prefix}/bin' --incdir='${prefix}/include/ffmpeg' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir='${prefix}/share/man' --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --enable-libopenjpeg --enable-version3 --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jul 27 2009 18:24:12, gcc: 4.3.3

---

### Post by Krazen on 2009-07-28
I'm using Jaunty.

My configuration:

```
FFmpeg version SVN-r19314, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --libdir='${prefix}/lib' --shlibdir='${prefix}/lib' --bindir='${prefix}/bin' --incdir='${prefix}/include/ffmpeg' --mandir='${prefix}/share/man' --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-libamr-nb --enable-libamr-wb --enable-libamr-wb --enable-nonfree --enable-libvorbis --enable-libgsm --enable-zlib
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jul 28 2009 01:42:38, gcc: 4.3.3

```

I tried with --enable-shared as well and neither with nor without works.

Maybe the problem is the way I build my packet. In your screenshot there are libavformat etc. packets and for my only one packet (ffmpeg) is building. I do it the way FakeOutdoorsman shown in his guide:

```
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "5:0.svn`date +%Y%m%d`-12ubuntu3" --default
```

---

