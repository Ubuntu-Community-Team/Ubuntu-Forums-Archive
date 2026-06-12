---
title: "Installing faust on Ubuntu Studio 19 removed a bunch of programs"
date: 2019-10-03
forum: Multimedia Software
---

### Post by digital-larry on 2019-10-03
Some of which I was using.  I went and complained about it on the Faust mailing list but then I realize they don't supply a deb package.

```

Package: faust
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 6159
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2.14.4~repack2-1
Depends: libc6 (>= 2.27), libgcc1 (>= 1:3.0), libllvm8 (>= 1:8~svn298832-1~), libstdc++6 (>= 5.2), faust-common (>= 2.14.4~repack2-1), faust-common (<< 2.14.4~repack2+1~)
Recommends: clang, python, ruby, libc6-dev | libc-dev, g++, make, libjack-dev, libgtk2.0-dev
Suggests: kate
Description: functional programming language for realtime audio applications
 Faust is a functional programming language specifically designed for realtime
 audio applications and plugins. The syntax of the language is block diagram
 oriented. The faust compiler translate signal processing specifications into
 optimized C++ code for signal processing applications.
 .
 The generated code can be wrapped into an 'architecture file' in order to
 create for example a standalone jack/gtk application. Several architecture
 file are provided and additional ones are fairly easy to add.
Original-Maintainer: Debian Multimedia Maintainers <debian-multimedia@lists.debian.org>
Homepage: https://faust.grame.fr/


```

These are the packages that got removed.

```

larry@ub-studio:~$ less /var/log/dpkg.log | grep remove | grep 10-03
2019-10-03 10:56:11 startup packages remove
2019-10-03 10:56:11 remove aeolus:amd64 0.9.5-1build1 <none>
2019-10-03 10:56:12 remove ardour-video-timeline:all 1:5.12.0-3 <none>
2019-10-03 10:56:12 remove csladspa:amd64 1:6.11.1-1 <none>
2019-10-03 10:56:13 remove dssi-host-jack:amd64 1.1.1~dfsg0-1build2 <none>
2019-10-03 10:56:14 remove foo-yc20:amd64 1.3.0-6build2 <none>
2019-10-03 10:56:14 remove ghostess:amd64 20120105-1build2 <none>
2019-10-03 10:56:15 remove gmidimonitor:amd64 3.6+dfsg0-3 <none>
2019-10-03 10:56:15 remove jack-capture:amd64 0.9.73-3 <none>
2019-10-03 10:56:16 remove jack-mixer:amd64 10-1build2 <none>
2019-10-03 10:56:17 remove jack-tools:amd64 20131226-1build4 <none>
2019-10-03 10:56:18 remove jconvolver:amd64 0.9.3-2 <none>
2019-10-03 10:56:18 remove libcsound64-6.0:amd64 1:6.12.2~dfsg-3 <none>
2019-10-03 10:56:19 remove meterbridge:amd64 0.9.2-13 <none>
2019-10-03 10:56:19 remove qmidinet:amd64 0.5.0-1 <none>
2019-10-03 10:56:20 remove recordmydesktop:amd64 0.3.8.1+svn602-1ubuntu5 <none>
2019-10-03 10:56:21 remove simplescreenrecorder:amd64 0.3.11-1build1 <none>
2019-10-03 10:56:22 remove sooperlooper:amd64 1.7.3~dfsg0-3build2 <none>
2019-10-03 10:56:22 remove xjadeo:amd64 0.8.7-2build1 <none>
2019-10-03 10:56:23 remove zita-at1:amd64 0.6.0-1.1 <none>
2019-10-03 10:56:23 remove zita-lrx:amd64 0.1.0-3 <none>
2019-10-03 10:56:24 remove zita-mu1:amd64 0.2.2-3 <none>
2019-10-03 10:56:25 remove zita-rev1:amd64 0.2.1-5.1 <none>
larry@ub-studio:~$ 

```

---

