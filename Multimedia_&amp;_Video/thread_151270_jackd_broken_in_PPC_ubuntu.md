---
title: "jackd broken in PPC ubuntu"
date: 2006-03-27
forum: Multimedia &amp; Video
---

### Post by stmiller on 2006-03-27
Jack [doesn't work in PPC]("http://ubuntuforums.org/showthread.php?t=80931"). Who is the maintainer so I can notify them ASAP? W/o jack, the software can't run....

---

### Post by dolson on 2006-03-27
dana@polly:~$ apt-cache show jackd
Package: jackd
Priority: optional
Section: universe/sound
Installed-Size: 352
Maintainer: Robert Jordens <jordens@debian.org>
Architecture: i386
Source: jack-audio-connection-kit
Version: 0.100.0-4
Depends: libc6 (>= 2.3.2.ds1-11), libc6 (>= 2.3.4-1), libcap1, libjack0.100.0-0 (= 0.100.0-4), libreadline5, libsndfile1
Suggests: qjackctl, jack-tools, meterbridge, libjackasyn0
Filename: pool/universe/j/jack-audio-connection-kit/jackd_0.100.0-4_i386.deb
Size: 97568
MD5sum: e526f0bb1e7466d8b2d1c9db0c6583cc
Description: JACK Audio Connection Kit (server and example clients)
 Low-latency sound server. JACK allows the connection of multiple applications
 to an audio device, as well as allowing them to share audio between
 themselves.
 .
 See <http://jackit.sourceforge.net/> for more info.
 .
 This package contains the daemon jackd as well as some example clients.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

