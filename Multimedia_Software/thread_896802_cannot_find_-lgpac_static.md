---
title: "cannot find -lgpac_static"
date: 2008-08-21
forum: Multimedia Software
---

### Post by pindari on 2008-08-21
I am compiling from the x264 files as follows:

clean install - Ubuntu 8.04 LTS Server Edition

# cd ~
# apt-get install build-essential subversion
# apt-get install checkinstall
# apt-get install sysvconfig
# apt-get install git-core
# apt-get install gpac
# wget [http://www.tortall.net/projects/yasm/releases/yasm-0.7.1.tar.gz](http://www.tortall.net/projects/yasm/releases/yasm-0.7.1.tar.gz)
# tar xzvf yasm-0.7.1.tar.gz
# cd yasm-0.7.1
# ./configure
# make
# checkinstall
# cd ~
# git clone git://git.videolan.org/x264.git
# cd ~/x264
# ./configure --enable-pthread --enable-mp4-output --enable-shared

/-- eveything is good so far, but then make fails --/

# make
....
/usr/bin/ld: cannot find -lgpac_static
collect2: ld returned 1 exit status
make: *** [libx264.so.60] Error 1

... and no sign of lgpac_static anywhere on the disk.

Any help or thoughts appreciated.

---

### Post by forger on 2008-08-21
perhaps you need: [apt://libgpac-dev]("apt://libgpac-dev")
it contains the files:
> /usr/lib/libgpac.so
/usr/lib/libgpac_static.a


Also, read here: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

If it still doesn't detect it, then do:
```

sudo apt-get install --reinstall libgpac-dev
ranlib /usr/lib/libgpac_static.a
sudo ldconfig -v

```

---

### Post by reader4 on 2009-04-28
Worked for me in 9.04.

---

### Post by kingtiger01 on 2009-08-28
thanks, was doing the same. it was obvious but it didnt dawn on me... till after i read it :D

---

