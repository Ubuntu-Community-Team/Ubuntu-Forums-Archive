---
title: "[SOLVED] Can not &amp;quot;make install&amp;quot; mplayer(ubuntu6.06 gnome)"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by offline on 2007-09-20
```

sot@sot-desktop:~/Desktop/tar/MPlayer-1.0rc1$ make install
make -C loader
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/loader'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/loader'
make -C loader/dshow
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/loader/dshow'
make[1]: `libDS_Filter.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/loader/dshow'
make -C loader/dmo
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/loader/dmo'
make[1]: `libDMO_Filter.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/loader/dmo'
make -C libavformat LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libavformat'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libavformat'
make -C libavcodec LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libavcodec'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libavcodec'
make -C libavutil LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libavutil'
make -C libmpdemux
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libmpdemux'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libmpdemux'
make -C stream
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/stream'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/stream'
make -C libmpcodecs
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libmpcodecs'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libmpcodecs'
make -C libao2
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libao2'
make[1]: `libao2.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libao2'
make -C osdep
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/osdep'
make[1]: `libosdep.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/osdep'
make -C libswscale LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libswscale'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libswscale'
make -C input
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/input'
make[1]: `libinput.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/input'
make -C libvo
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libvo'
make[1]: `libvo.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libvo'
make -C libaf
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libaf'
make[1]: `libaf.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libaf'
make -C mp3lib
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/mp3lib'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/mp3lib'
make -C liba52
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/liba52'
make[1]: `liba52.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/liba52'
make -C libmpeg2
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libmpeg2'
make[1]: `libmpeg2.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libmpeg2'
make -C libfaad2
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libfaad2'
make[1]: `libfaad2.a' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libfaad2'
make -C libdha
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libdha'
make[1]: `libdha.so.1.0' is up to date.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libdha'
make -C vidix
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/vidix'
make -C drivers
make[2]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/vidix/drivers'make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/vidix/drivers'
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/vidix'
make -C libmpdvdkit2
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libmpdvdkit2'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libmpdvdkit2'
make -C libdha install
make[1]: Entering directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libdha'
mkdir -p /usr/local/lib
install -m 755  -p libdha.so.1.0  /usr/local/lib/libdha.so.1.0
install: cannot create regular file `/usr/local/lib/libdha.so.1.0': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/sot/Desktop/tar/MPlayer-1.0rc1/libdha'
make: *** [install] Error 2
sot@sot-desktop:~/Desktop/tar/MPlayer-1.0rc1$ mkdir /usr/local/lib/










```

What can I do?

---

### Post by RomeReactor on 2007-09-20
Hi. Try running it with sudo:
```
sudo make install
```

Any particular reason you need to compile it? why not get it from the repositories?
```
sudo apt-get install mplayer
```

---

### Post by offline on 2007-09-20
> **RomeReactor said:**
> Hi. Try running it with sudo:
```
sudo make install
```

Any particular reason you need to compile it? why not get it from the repositories?
```
sudo apt-get install mplayer
```

I have no internet conection at this pc.

By the way, when the above mentioned successful compilation happened is there a file that was created andwhere it may be? 

Additionally, after the unsuccessfull make install process is there any junk files that need to be get rid of and where?

Thanx.:confused:

---

### Post by RomeReactor on 2007-09-20
To find *most*--if not all--of the files created, enter:
```
locate mplayer
```
The executable files are in **/usr/bin/mplayer** and **/usr/bin/gmplayer**.
as for residual files, I'm not certain; probably only the source folder and files you just worked with.

---

### Post by Gremlinzzz on 2007-09-20
> **offline said:**
> I have no internet conection at this pc.

By the way, when the above mentioned successful compilation happened is there a file that was created andwhere it may be? 

Additionally, after the unsuccessfull make install process is there any junk files that need to be get rid of and where?

Thanx.:confused:

get smplayer its a deb package and installs mplayer
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)

---

