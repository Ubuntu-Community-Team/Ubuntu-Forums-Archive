---
title: "Medibuntu and libdvdcss: Building your own..."
date: 2013-05-17
forum: Multimedia Software
---

### Post by andrew.46 on 2013-05-17
The future of Medibuntu's Repository is a little uncertain so now might be a good time to consider building your own copy of libdvdcss. Building your own copy is pretty easy, simply paste the following *single command* into a Terminal window:

```

sudo apt-get -y install build-essential checkinstall && \
mkdir -pv $HOME/libdvdcss_build && cd $HOME/libdvdcss_build && \
sudo apt-get remove libdvdcss2 && \
wget http://download.videolan.org/pub/libdvdcss/1.2.13/libdvdcss-1.2.13.tar.bz2 && \
tar xvf libdvdcss-1.2.13.tar.bz2 && \
cd libdvdcss-1.2.13 && \
./configure && make && \
sudo checkinstall --pakdir "$HOME/libdvdcss_build" --backup=no --deldoc=yes \
                  --pkgname libdvdcss2 --pkgversion "1.2.13" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

Now you should be right to go with playing back encrypted DVDs :).

---

### Post by speartip on 2013-06-05
Hi Andrew,
I had dvd playback working via medibuntu, but decided to give this a go.
I deleted the libdvdcss already installed, then ran your command.
Everything seemed to work & I had libdvdcss 1.2.13 installed, but could get no dvd playback.
I reverted to the medibuntu repo again & everything worked fine.
What am I doing wrong, or are there any other commands I need to run?
Using 12.04 by the way, if that makes a difference.

---

### Post by mc4man on 2013-06-05
> **speartip said:**
> Hi Andrew,
I had dvd playback working via medibuntu, but decided to give this a go.
I deleted the libdvdcss already installed, then ran your command.
Everything seemed to work & I had libdvdcss 1.2.13 installed, but could get no dvd playback.
I reverted to the medibuntu repo again & everything worked fine.
What am I doing wrong, or are there any other commands I need to run?
Using 12.04 by the way, if that makes a difference.
Andrew's command set is missing this for after the build/install - 
sudo ldconfig

(whether the package name should be libdvdcss2 is also a question...

---

### Post by monkeybrain2012 on 2013-06-05
I have compiled libdvdcss by simply downloading the tarball from videolan, extract it and cd into and did
```

./configure --prefix=/usr
make
sudo checkinstall

```

I named the package libdvdcss2 (instead of libdvdcss) and it works. Basically it is the same as what Andrew did, except for the name (don't think it matters whether you install in /usr or /usr/local and run ldconfig afterwords)

---

### Post by andrew.46 on 2013-06-05
Work & life have me at the moment but I have made the changes suggested, hopefully this gets things running ok...

---

