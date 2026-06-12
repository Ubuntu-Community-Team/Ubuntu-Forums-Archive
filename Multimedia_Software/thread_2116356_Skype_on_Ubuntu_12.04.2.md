---
title: "Skype on Ubuntu 12.04.2"
date: 2013-02-15
forum: Multimedia Software
---

### Post by mrquesty on 2013-02-15
Hi Everyone,

I've just installed a fresh Ubuntu 12.04.2 amd64 and try to install Skype, but all fails:

1. Original Skype from Skype.com says I have troubles with libqt-dbus.i386 (seems, it requires older lib)
2. Skype from launchpad or Ubuntu partner repo says I need skype-bin, but when I say to install skype-bin the following error rises:  skype-bin:i386 : Depends: libqt4-dbus:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqt4-network:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqt4-xml:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not going to be installed
                  Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Recommends: sni-qt:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Any ideas, how to fix it?

---

### Post by gifford on 2013-02-15
First you should fix the broken packages. If you have synaptic package manager installed, go to to edit and fix broken packages. After they have been fixed try installing Skype from the Ubuntu software center. All dependencies should be installed then.

---

### Post by mrquesty on 2013-02-16
> **gifford said:**
> First you should fix the broken packages. If you have synaptic package manager installed, go to to edit and fix broken packages. 

I don't use Synaptic PM, but the regular Ubuntu Software Center.
I fixed broken packages by means of: sudo apt-get update & sudo apt-get -f install. There are no mistakes, nor any packages to be installed/updated/etc.

I have all the libs required, see below:
dpkg -l | grep libqt4
ii  libqt4-dbus                                  4:4.8.1-0ubuntu4.4                               Qt 4 D-Bus module
ii  libqt4-declarative                           4:4.8.1-0ubuntu4.4                               Qt 4 Declarative module
ii  libqt4-network                               4:4.8.1-0ubuntu4.4                               Qt 4 network module
ii  libqt4-opengl                                4:4.8.1-0ubuntu4.4                               Qt 4 OpenGL module
ii  libqt4-script                                4:4.8.1-0ubuntu4.4                               Qt 4 script module
ii  libqt4-sql                                   4:4.8.1-0ubuntu4.4                               Qt 4 SQL module
ii  libqt4-sql-sqlite                            4:4.8.1-0ubuntu4.4                               Qt 4 SQLite 3 database driver
ii  libqt4-svg                                   4:4.8.1-0ubuntu4.4                               Qt 4 SVG module
ii  libqt4-xml                                   4:4.8.1-0ubuntu4.4                               Qt 4 XML module
ii  libqt4-xmlpatterns                           4:4.8.1-0ubuntu4.4                               Qt 4 XML patterns module


Maybe, I'm not 100% certain, it's all, because I have a dual boot configuration with Windows 8, and had to run boot-repair sequence, which made really lots of changes to kernel & supporting libs.

Any ideas, guys?

---

### Post by mrquesty on 2013-02-16
I just wanted to add, that I have Ubuntu 12.04.2 at office, but it was an upgrade from 12.04 -> 12.04.1, all is just fine, but this is a fresh install.

I tried to reinstall all dependencies once again and force dpkg to install Skype, but it doesn't start saying I don't have: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

It is present: find /usr/lib -name libQtDBus.so\*
/usr/lib/x86_64-linux-gnu/libQtDBus.so.4.8
/usr/lib/x86_64-linux-gnu/libQtDBus.so.4
/usr/lib/x86_64-linux-gnu/libQtDBus.so.4.8.1

---

### Post by fdrake on 2013-02-16
can you lease post 
```

less log /var/log/dpkg.log | tail -30| less

```
also try to fix the problem with libtq
```

sudo apt-get remove --purge libqt4*
sudo apt-get upgrade && sudo apt-get update && sudo apt-get install libqt4*
sudo apt-get install skype

```
make sure to post the output of the commands in case of errors

---

### Post by mrquesty on 2013-02-16
> **fdrake said:**
> can you lease post 
```

less log /var/log/dpkg.log | tail -30| less

```

Sure. I added more, because there were so many tests...

2013-02-16 10:04:23 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-02-16 10:04:23 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:04:23 status config-files skype:i386 4.1.0.20-1
2013-02-16 10:04:23 status config-files skype:i386 4.1.0.20-1
2013-02-16 10:04:23 trigproc desktop-file-utils 0.20-0ubuntu3 <none>
2013-02-16 10:04:23 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-02-16 10:04:23 status installed desktop-file-utils 0.20-0ubuntu3
2013-02-16 10:04:23 trigproc bamfdaemon 0.2.124.2-0ubuntu1 <none>
2013-02-16 10:04:23 status half-configured bamfdaemon 0.2.124.2-0ubuntu1
2013-02-16 10:04:23 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-02-16 10:04:23 trigproc gnome-menus 3.4.0-0ubuntu1 <none>
2013-02-16 10:04:23 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-02-16 10:04:23 status installed gnome-menus 3.4.0-0ubuntu1
2013-02-16 10:04:24 startup archives unpack
2013-02-16 10:04:25 install libstdc++6:i386 4.6.3-1ubuntu5 4.6.3-1ubuntu5
2013-02-16 10:04:25 status half-installed libstdc++6:i386 4.6.3-1ubuntu5
2013-02-16 10:04:25 status unpacked libstdc++6:i386 4.6.3-1ubuntu5
2013-02-16 10:04:25 status unpacked libstdc++6:i386 4.6.3-1ubuntu5
2013-02-16 10:04:25 install libdbus-1-3:i386 1.4.18-1ubuntu1.3 1.4.18-1ubuntu1.3
2013-02-16 10:04:25 status half-installed libdbus-1-3:i386 1.4.18-1ubuntu1.3
2013-02-16 10:04:26 status unpacked libdbus-1-3:i386 1.4.18-1ubuntu1.3
2013-02-16 10:04:26 status unpacked libdbus-1-3:i386 1.4.18-1ubuntu1.3
2013-02-16 10:04:26 install zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu4 1:1.2.3.4.dfsg-3ubuntu4
2013-02-16 10:04:26 status half-installed zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu4
2013-02-16 10:04:26 status unpacked zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu4
2013-02-16 10:04:26 status unpacked zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu4
2013-02-16 10:04:27 install libssl1.0.0:i386 1.0.1-4ubuntu5.5 1.0.1-4ubuntu5.5
2013-02-16 10:04:27 status half-installed libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-16 10:04:27 status unpacked libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-16 10:04:27 status unpacked libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-16 10:04:28 install libxau6:i386 1:1.0.6-4 1:1.0.6-4
2013-02-16 10:04:28 status half-installed libxau6:i386 1:1.0.6-4
2013-02-16 10:04:28 status unpacked libxau6:i386 1:1.0.6-4
2013-02-16 10:04:28 status unpacked libxau6:i386 1:1.0.6-4
2013-02-16 10:04:28 install libxdmcp6:i386 1:1.1.0-4 1:1.1.0-4
2013-02-16 10:04:28 status half-installed libxdmcp6:i386 1:1.1.0-4
2013-02-16 10:04:28 status unpacked libxdmcp6:i386 1:1.1.0-4
2013-02-16 10:04:29 status unpacked libxdmcp6:i386 1:1.1.0-4
2013-02-16 10:04:29 install libxcb1:i386 1.8.1-1ubuntu0.1 1.8.1-1ubuntu0.1
2013-02-16 10:04:29 status half-installed libxcb1:i386 1.8.1-1ubuntu0.1
2013-02-16 10:04:29 status unpacked libxcb1:i386 1.8.1-1ubuntu0.1
2013-02-16 10:04:29 status unpacked libxcb1:i386 1.8.1-1ubuntu0.1
2013-02-16 10:04:30 install libx11-6:i386 2:1.4.99.1-0ubuntu2 2:1.4.99.1-0ubuntu2
2013-02-16 10:04:30 status half-installed libx11-6:i386 2:1.4.99.1-0ubuntu2
2013-02-16 10:04:30 status unpacked libx11-6:i386 2:1.4.99.1-0ubuntu2
2013-02-16 10:04:30 status unpacked libx11-6:i386 2:1.4.99.1-0ubuntu2
2013-02-16 10:04:30 install libxext6:i386 2:1.3.0-3build1 2:1.3.0-3build1
2013-02-16 10:04:30 status half-installed libxext6:i386 2:1.3.0-3build1
2013-02-16 10:04:31 status unpacked libxext6:i386 2:1.3.0-3build1
2013-02-16 10:04:31 status unpacked libxext6:i386 2:1.3.0-3build1
2013-02-16 10:04:31 install libasyncns0:i386 <none> 0.8-4
2013-02-16 10:04:31 status half-installed libasyncns0:i386 0.8-4
2013-02-16 10:04:31 status unpacked libasyncns0:i386 0.8-4
2013-02-16 10:04:31 status unpacked libasyncns0:i386 0.8-4
2013-02-16 10:04:32 install libogg0:i386 <none> 1.2.2~dfsg-1ubuntu1
2013-02-16 10:04:32 status half-installed libogg0:i386 1.2.2~dfsg-1ubuntu1
2013-02-16 10:04:32 status unpacked libogg0:i386 1.2.2~dfsg-1ubuntu1
2013-02-16 10:04:32 status unpacked libogg0:i386 1.2.2~dfsg-1ubuntu1
2013-02-16 10:04:32 install libflac8:i386 <none> 1.2.1-6
2013-02-16 10:04:32 status half-installed libflac8:i386 1.2.1-6
2013-02-16 10:04:33 status unpacked libflac8:i386 1.2.1-6
2013-02-16 10:04:33 status unpacked libflac8:i386 1.2.1-6
2013-02-16 10:04:33 install libsamplerate0:i386 <none> 0.1.8-4
2013-02-16 10:04:33 status half-installed libsamplerate0:i386 0.1.8-4
2013-02-16 10:04:33 status unpacked libsamplerate0:i386 0.1.8-4
2013-02-16 10:04:34 status unpacked libsamplerate0:i386 0.1.8-4
2013-02-16 10:04:34 install libjack-jackd2-0:i386 <none> 1.9.8~dfsg.1-1ubuntu1
2013-02-16 10:04:34 status half-installed libjack-jackd2-0:i386 1.9.8~dfsg.1-1ubuntu1
2013-02-16 10:04:34 status unpacked libjack-jackd2-0:i386 1.9.8~dfsg.1-1ubuntu1
2013-02-16 10:04:34 status unpacked libjack-jackd2-0:i386 1.9.8~dfsg.1-1ubuntu1
2013-02-16 10:04:35 install libjson0:i386 <none> 0.9-1ubuntu1
2013-02-16 10:04:35 status half-installed libjson0:i386 0.9-1ubuntu1
2013-02-16 10:04:35 status unpacked libjson0:i386 0.9-1ubuntu1
2013-02-16 10:04:35 status unpacked libjson0:i386 0.9-1ubuntu1
2013-02-16 10:04:35 install libvorbis0a:i386 <none> 1.3.2-1ubuntu3
2013-02-16 10:04:35 status half-installed libvorbis0a:i386 1.3.2-1ubuntu3
2013-02-16 10:04:36 status unpacked libvorbis0a:i386 1.3.2-1ubuntu3
2013-02-16 10:04:36 status unpacked libvorbis0a:i386 1.3.2-1ubuntu3
2013-02-16 10:04:36 install libvorbisenc2:i386 <none> 1.3.2-1ubuntu3
2013-02-16 10:04:36 status half-installed libvorbisenc2:i386 1.3.2-1ubuntu3
2013-02-16 10:04:36 status unpacked libvorbisenc2:i386 1.3.2-1ubuntu3
2013-02-16 10:04:36 status unpacked libvorbisenc2:i386 1.3.2-1ubuntu3
2013-02-16 10:04:37 install libsndfile1:i386 <none> 1.0.25-4
2013-02-16 10:04:37 status half-installed libsndfile1:i386 1.0.25-4
2013-02-16 10:04:37 status unpacked libsndfile1:i386 1.0.25-4
2013-02-16 10:04:37 status unpacked libsndfile1:i386 1.0.25-4
2013-02-16 10:04:38 install libwrap0:i386 <none> 7.6.q-21
2013-02-16 10:04:38 status half-installed libwrap0:i386 7.6.q-21
2013-02-16 10:04:38 status triggers-pending man-db 2.6.1-2ubuntu1
2013-02-16 10:04:38 status half-installed libwrap0:i386 7.6.q-21
2013-02-16 10:04:38 status unpacked libwrap0:i386 7.6.q-21
2013-02-16 10:04:38 status unpacked libwrap0:i386 7.6.q-21
2013-02-16 10:04:39 install libpulse0:i386 <none> 1:1.1-0ubuntu15.2
2013-02-16 10:04:39 status half-installed libpulse0:i386 1:1.1-0ubuntu15.2
2013-02-16 10:04:39 status unpacked libpulse0:i386 1:1.1-0ubuntu15.2
2013-02-16 10:04:39 status unpacked libpulse0:i386 1:1.1-0ubuntu15.2
2013-02-16 10:04:40 install libspeexdsp1:i386 <none> 1.2~rc1-3ubuntu2
2013-02-16 10:04:40 status half-installed libspeexdsp1:i386 1.2~rc1-3ubuntu2
2013-02-16 10:04:40 status unpacked libspeexdsp1:i386 1.2~rc1-3ubuntu2
2013-02-16 10:04:40 status unpacked libspeexdsp1:i386 1.2~rc1-3ubuntu2
2013-02-16 10:04:40 install libxss1:i386 1:1.2.1-2 1:1.2.1-2
2013-02-16 10:04:40 status half-installed libxss1:i386 1:1.2.1-2
2013-02-16 10:04:41 status unpacked libxss1:i386 1:1.2.1-2
2013-02-16 10:04:41 status unpacked libxss1:i386 1:1.2.1-2
2013-02-16 10:04:41 install libxv1:i386 2:1.0.6-2build1 2:1.0.6-2build1
2013-02-16 10:04:41 status half-installed libxv1:i386 2:1.0.6-2build1
2013-02-16 10:04:41 status unpacked libxv1:i386 2:1.0.6-2build1
2013-02-16 10:04:41 status unpacked libxv1:i386 2:1.0.6-2build1
2013-02-16 10:04:42 install libasound2-plugins:i386 <none> 1.0.25-1ubuntu1
2013-02-16 10:04:42 status half-installed libasound2-plugins:i386 1.0.25-1ubuntu1
2013-02-16 10:04:42 status unpacked libasound2-plugins:i386 1.0.25-1ubuntu1
2013-02-16 10:04:42 status unpacked libasound2-plugins:i386 1.0.25-1ubuntu1
2013-02-16 10:04:42 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2013-02-16 10:04:42 status half-configured man-db 2.6.1-2ubuntu1
2013-02-16 10:04:43 status installed man-db 2.6.1-2ubuntu1
2013-02-16 10:04:43 startup packages configure
2013-02-16 10:04:43 configure libstdc++6:i386 4.6.3-1ubuntu5 <none>
2013-02-16 10:04:43 status unpacked libstdc++6:i386 4.6.3-1ubuntu5
2013-02-16 10:04:44 status half-configured libstdc++6:i386 4.6.3-1ubuntu5
2013-02-16 10:04:44 status installed libstdc++6:i386 4.6.3-1ubuntu5
2013-02-16 10:04:44 status triggers-pending libc-bin 2.15-0ubuntu10.3
2013-02-16 10:04:44 configure libdbus-1-3:i386 1.4.18-1ubuntu1.3 <none>
2013-02-16 10:04:44 status unpacked libdbus-1-3:i386 1.4.18-1ubuntu1.3
2013-02-16 10:04:44 status half-configured libdbus-1-3:i386 1.4.18-1ubuntu1.3
2013-02-16 10:04:44 status installed libdbus-1-3:i386 1.4.18-1ubuntu1.3
2013-02-16 10:04:44 configure zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu4 <none>
2013-02-16 10:04:44 status unpacked zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu4
2013-02-16 10:04:44 status half-configured zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu4
2013-02-16 10:04:44 status installed zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu4
2013-02-16 10:04:44 configure libssl1.0.0:i386 1.0.1-4ubuntu5.5 <none>
2013-02-16 10:04:44 status unpacked libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-16 10:04:45 status half-configured libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-16 10:04:45 status installed libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-16 10:04:45 configure libxau6:i386 1:1.0.6-4 <none>
2013-02-16 10:04:45 status unpacked libxau6:i386 1:1.0.6-4
2013-02-16 10:04:45 status half-configured libxau6:i386 1:1.0.6-4
2013-02-16 10:04:45 status installed libxau6:i386 1:1.0.6-4
2013-02-16 10:04:45 configure libxdmcp6:i386 1:1.1.0-4 <none>
2013-02-16 10:04:45 status unpacked libxdmcp6:i386 1:1.1.0-4
2013-02-16 10:04:45 status half-configured libxdmcp6:i386 1:1.1.0-4
2013-02-16 10:04:45 status installed libxdmcp6:i386 1:1.1.0-4
2013-02-16 10:04:46 configure libxcb1:i386 1.8.1-1ubuntu0.1 <none>
2013-02-16 10:04:46 status unpacked libxcb1:i386 1.8.1-1ubuntu0.1
2013-02-16 10:04:46 status half-configured libxcb1:i386 1.8.1-1ubuntu0.1
2013-02-16 10:04:46 status installed libxcb1:i386 1.8.1-1ubuntu0.1
2013-02-16 10:04:46 configure libx11-6:i386 2:1.4.99.1-0ubuntu2 <none>
2013-02-16 10:04:46 status unpacked libx11-6:i386 2:1.4.99.1-0ubuntu2
2013-02-16 10:04:46 status half-configured libx11-6:i386 2:1.4.99.1-0ubuntu2
2013-02-16 10:04:46 status installed libx11-6:i386 2:1.4.99.1-0ubuntu2
2013-02-16 10:04:46 configure libxext6:i386 2:1.3.0-3build1 <none>
2013-02-16 10:04:46 status unpacked libxext6:i386 2:1.3.0-3build1
2013-02-16 10:04:46 status half-configured libxext6:i386 2:1.3.0-3build1
2013-02-16 10:04:46 status installed libxext6:i386 2:1.3.0-3build1
2013-02-16 10:04:46 configure libasyncns0:i386 0.8-4 <none>
2013-02-16 10:04:46 status unpacked libasyncns0:i386 0.8-4
2013-02-16 10:04:47 status half-configured libasyncns0:i386 0.8-4
2013-02-16 10:04:47 status installed libasyncns0:i386 0.8-4
2013-02-16 10:04:47 configure libogg0:i386 1.2.2~dfsg-1ubuntu1 <none>
2013-02-16 10:04:47 status unpacked libogg0:i386 1.2.2~dfsg-1ubuntu1
2013-02-16 10:04:47 status half-configured libogg0:i386 1.2.2~dfsg-1ubuntu1
2013-02-16 10:04:47 status installed libogg0:i386 1.2.2~dfsg-1ubuntu1
2013-02-16 10:04:47 configure libflac8:i386 1.2.1-6 <none>
2013-02-16 10:04:47 status unpacked libflac8:i386 1.2.1-6
2013-02-16 10:04:47 status half-configured libflac8:i386 1.2.1-6
2013-02-16 10:04:47 status installed libflac8:i386 1.2.1-6
2013-02-16 10:04:48 configure libsamplerate0:i386 0.1.8-4 <none>
2013-02-16 10:04:48 status unpacked libsamplerate0:i386 0.1.8-4
2013-02-16 10:04:48 status half-configured libsamplerate0:i386 0.1.8-4
2013-02-16 10:04:48 status installed libsamplerate0:i386 0.1.8-4
2013-02-16 10:04:48 configure libjack-jackd2-0:i386 1.9.8~dfsg.1-1ubuntu1 <none>
2013-02-16 10:04:48 status unpacked libjack-jackd2-0:i386 1.9.8~dfsg.1-1ubuntu1
2013-02-16 10:04:48 status half-configured libjack-jackd2-0:i386 1.9.8~dfsg.1-1ubuntu1
2013-02-16 10:04:48 status installed libjack-jackd2-0:i386 1.9.8~dfsg.1-1ubuntu1
2013-02-16 10:04:48 configure libjson0:i386 0.9-1ubuntu1 <none>
2013-02-16 10:04:48 status unpacked libjson0:i386 0.9-1ubuntu1
2013-02-16 10:04:48 status half-configured libjson0:i386 0.9-1ubuntu1
2013-02-16 10:04:48 status installed libjson0:i386 0.9-1ubuntu1
2013-02-16 10:04:49 configure libvorbis0a:i386 1.3.2-1ubuntu3 <none>
2013-02-16 10:04:49 status unpacked libvorbis0a:i386 1.3.2-1ubuntu3
2013-02-16 10:04:49 status half-configured libvorbis0a:i386 1.3.2-1ubuntu3
2013-02-16 10:04:49 status installed libvorbis0a:i386 1.3.2-1ubuntu3
2013-02-16 10:04:49 configure libvorbisenc2:i386 1.3.2-1ubuntu3 <none>
2013-02-16 10:04:49 status unpacked libvorbisenc2:i386 1.3.2-1ubuntu3
2013-02-16 10:04:49 status half-configured libvorbisenc2:i386 1.3.2-1ubuntu3
2013-02-16 10:04:49 status installed libvorbisenc2:i386 1.3.2-1ubuntu3
2013-02-16 10:04:49 configure libsndfile1:i386 1.0.25-4 <none>
2013-02-16 10:04:49 status unpacked libsndfile1:i386 1.0.25-4
2013-02-16 10:04:49 status half-configured libsndfile1:i386 1.0.25-4
2013-02-16 10:04:49 status installed libsndfile1:i386 1.0.25-4
2013-02-16 10:04:50 configure libwrap0:i386 7.6.q-21 <none>
2013-02-16 10:04:50 status unpacked libwrap0:i386 7.6.q-21
2013-02-16 10:04:50 status half-configured libwrap0:i386 7.6.q-21
2013-02-16 10:04:50 status installed libwrap0:i386 7.6.q-21
2013-02-16 10:04:50 configure libpulse0:i386 1:1.1-0ubuntu15.2 <none>
2013-02-16 10:04:50 status unpacked libpulse0:i386 1:1.1-0ubuntu15.2
2013-02-16 10:04:50 status unpacked libpulse0:i386 1:1.1-0ubuntu15.2
2013-02-16 10:04:50 status half-configured libpulse0:i386 1:1.1-0ubuntu15.2
2013-02-16 10:04:50 status installed libpulse0:i386 1:1.1-0ubuntu15.2
2013-02-16 10:04:50 configure libspeexdsp1:i386 1.2~rc1-3ubuntu2 <none>
2013-02-16 10:04:50 status unpacked libspeexdsp1:i386 1.2~rc1-3ubuntu2
2013-02-16 10:04:50 status half-configured libspeexdsp1:i386 1.2~rc1-3ubuntu2
2013-02-16 10:04:50 status installed libspeexdsp1:i386 1.2~rc1-3ubuntu2
2013-02-16 10:04:51 configure libxss1:i386 1:1.2.1-2 <none>
2013-02-16 10:04:51 status unpacked libxss1:i386 1:1.2.1-2
2013-02-16 10:04:51 status half-configured libxss1:i386 1:1.2.1-2
2013-02-16 10:04:51 status installed libxss1:i386 1:1.2.1-2
2013-02-16 10:04:51 configure libxv1:i386 2:1.0.6-2build1 <none>
2013-02-16 10:04:51 status unpacked libxv1:i386 2:1.0.6-2build1
2013-02-16 10:04:51 status half-configured libxv1:i386 2:1.0.6-2build1
2013-02-16 10:04:51 status installed libxv1:i386 2:1.0.6-2build1
2013-02-16 10:04:51 configure libasound2-plugins:i386 1.0.25-1ubuntu1 <none>
2013-02-16 10:04:51 status unpacked libasound2-plugins:i386 1.0.25-1ubuntu1
2013-02-16 10:04:51 status half-configured libasound2-plugins:i386 1.0.25-1ubuntu1
2013-02-16 10:04:51 status installed libasound2-plugins:i386 1.0.25-1ubuntu1
2013-02-16 10:04:51 trigproc libc-bin 2.15-0ubuntu10.3 <none>
2013-02-16 10:04:51 status half-configured libc-bin 2.15-0ubuntu10.3
2013-02-16 10:04:52 status installed libc-bin 2.15-0ubuntu10.3
2013-02-16 10:05:03 startup archives install
2013-02-16 10:05:03 install skype:i386 4.1.0.20-1 4.1.0.20-1
2013-02-16 10:05:03 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:03 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-02-16 10:05:04 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:04 status triggers-pending bamfdaemon 0.2.124.2-0ubuntu1
2013-02-16 10:05:04 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:04 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-02-16 10:05:04 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:05 status unpacked skype:i386 4.1.0.20-1
2013-02-16 10:05:05 status unpacked skype:i386 4.1.0.20-1
2013-02-16 10:05:05 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-02-16 10:05:05 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-02-16 10:05:05 status installed desktop-file-utils 0.20-0ubuntu3
2013-02-16 10:05:05 trigproc bamfdaemon 0.2.124.2-0ubuntu1 0.2.124.2-0ubuntu1
2013-02-16 10:05:05 status half-configured bamfdaemon 0.2.124.2-0ubuntu1
2013-02-16 10:05:05 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-02-16 10:05:05 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-02-16 10:05:05 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-02-16 10:05:05 status installed gnome-menus 3.4.0-0ubuntu1
2013-02-16 10:05:18 startup archives install
2013-02-16 10:05:19 upgrade skype:i386 4.1.0.20-1 4.1.0.20-1
2013-02-16 10:05:19 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:19 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-02-16 10:05:19 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:19 status triggers-pending bamfdaemon 0.2.124.2-0ubuntu1
2013-02-16 10:05:19 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:19 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-02-16 10:05:19 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:20 status half-installed skype:i386 4.1.0.20-1
2013-02-16 10:05:20 status unpacked skype:i386 4.1.0.20-1
2013-02-16 10:05:20 status unpacked skype:i386 4.1.0.20-1
2013-02-16 10:05:20 configure skype:i386 4.1.0.20-1 4.1.0.20-1
2013-02-16 10:05:20 status unpacked skype:i386 4.1.0.20-1
2013-02-16 10:05:20 status unpacked skype:i386 4.1.0.20-1
2013-02-16 10:05:21 status half-configured skype:i386 4.1.0.20-1
2013-02-16 10:05:21 status triggers-awaited skype:i386 4.1.0.20-1
2013-02-16 10:05:21 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-02-16 10:05:21 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-02-16 10:05:21 status installed desktop-file-utils 0.20-0ubuntu3
2013-02-16 10:05:21 trigproc bamfdaemon 0.2.124.2-0ubuntu1 0.2.124.2-0ubuntu1
2013-02-16 10:05:21 status half-configured bamfdaemon 0.2.124.2-0ubuntu1
2013-02-16 10:05:21 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-02-16 10:05:21 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-02-16 10:05:21 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-02-16 10:05:21 status installed skype:i386 4.1.0.20-1
2013-02-16 10:05:21 status installed gnome-menus 3.4.0-0ubuntu1

---

### Post by mrquesty on 2013-02-16
Honestly, I'm almost lost with what could cause this, so trying to install 12.10 in an hour or two - can't leave w/o Skype (my work instrument)...

---

### Post by fdrake on 2013-02-16
> **mrquesty said:**
> Honestly, I'm almost lost with what could cause this, so trying to install 12.10 in an hour or two - can't leave w/o Skype (my work instrument)...

i don't think this is a big deal. Check my prev post and run my command in post # 5. That should do it.

--------------------------
quote
also try to fix the problem with libtq
```


sudo apt-get remove --purge libqt4*
sudo apt-get upgrade && sudo apt-get update && sudo apt-get install libqt4*
sudo apt-get install skype

```
make sure to post the output of the commands in case of errors

---

### Post by mrquesty on 2013-02-16
```


sudo apt-get remove --purge libqt4*
sudo apt-get upgrade && sudo apt-get update && sudo apt-get install libqt4*
sudo apt-get install skype

```

Purge was successful. The following error appeared during install of libqt4 -> The following packages have unmet dependencies:
 libqt3-mt-dev : Depends: libfontconfig1-dev but it is not going to be installed
                 Depends: libxft-dev but it is not going to be installed

I tried to install libxft-dev, but the following:
vladimiry@questy-ubu-ENVY:~$ sudo apt-get install libfontconfig1-dev libxft-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libfontconfig1-dev : Depends: libexpat1-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
vladimiry@questy-ubu-ENVY:~$ sudo apt-get install libfontconfig1-dev libxft-dev libexpat1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libexpat1-dev : Depends: libexpat1 (= 2.0.1-7.2ubuntu1.1) but 2.1.0-1ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
vladimiry@questy-ubu-ENVY:~$ sudo apt-get install libfontconfig1-dev libxft-dev libexpat1-dev libexpat1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libexpat1 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libexpat1-dev : Depends: libexpat1 (= 2.0.1-7.2ubuntu1.1) but 2.1.0-1ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by mrquesty on 2013-02-16
I did a fresh install of 12.10, and Skype installation went smoothly.
Thanks Everyone for cooperation and support.

---

