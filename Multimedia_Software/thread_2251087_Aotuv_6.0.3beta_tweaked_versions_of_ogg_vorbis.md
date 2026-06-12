---
title: "Aotuv 6.0.3beta tweaked versions of ogg vorbis"
date: 2014-11-01
forum: Multimedia Software
---

### Post by plazman30 on 2014-11-01
I am trying very hard to build the 6.0.3beta aotuv tweaked version of the ogg-vorbis souce that I got from here:

[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)

I searched through a dozen web sites, and was unable to find anything useful for the 14.04 version of Ubuntu.

I finally found this thread and read through it:

[http://ubuntuforums.org/showthread.php?t=1137670](http://ubuntuforums.org/showthread.php?t=1137670)

Using this thread I used the following commands to compile and install aotuv

```
CFLAGS=-fno-strict-aliasing sh ./configure --prefix=/usr
make 
sudo make install
```

These commands, according to the thread, are supposed to replace the installed binaries with the new ones that get compiled.  Problem is, I try to encode a FLAC file, and it's still using the old encoder.

Any help greatly appreciated.

---

### Post by mc4man on 2014-11-01
Whether  there is much to be gained here not up on anymore..
Your problem is that the thread is old & that source is also dated in where it installs to.

So while the method of building shared to /usr would work back then, (not the best approach), now  the libs should  go elsewhere.
So in a nutshell you've installed to where oggenc doesn't use.

Can be checked simply - 
> ldd /usr/bin/oggenc
linux-vdso.so.1 =>  (0x00007fff8574f000)
	libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f030b455000)
	libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f030b228000)
	libFLAC.so.8 => /usr/lib/x86_64-linux-gnu/libFLAC.so.8 (0x00007f030aff6000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f030acf0000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f030aae7000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f030a720000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f030b94e000)

Your source installed to /usr/lib & by itself of no value there.

there are many ways to skin this cat if inclined -  1 simple way to produce an enabled oggenc
cd to your recent source & run a sudo make uninstall
delete the source folder, ect.

starting fresh - 
```
sudo apt-get  build-dep libvorbis vorbis-tools

```
```
sudo apt-get install checkinstall

```

Then 1 single copy & paste
```
cd 
mkdir -p ogg_build && cd ogg_build && \
wget http://www.geocities.jp/aoyoume/aotuv/source_code/libvorbis-aotuv_b6.03_2014.tar.bz2 && \
tar -xvjf libvorbis-aotuv_b6.03_2014.tar.bz2 && \
cd aotuv-b6.03_20110424-20140429 && chmod +x configure && \
./configure --disable-shared && make && \
sudo checkinstall --pkgname=aotuv-vorbis  --backup=no --default \
--deldoc=yes --fstrans=no --pkgversion=6.03 && \
cd .. && \
apt-get source vorbis-tools && \
cd vorbis-tools-1.4.0 && ./configure && make && \
sudo checkinstall --backup=no --deldoc=yes  --deldesc=yes --delspec=yes \
--default --fstrans=no  --pkgversion 1.4.0+aotuv-b6.3


```

---

### Post by plazman30 on 2014-11-02
Thanks!  I'll give that a try!

---

### Post by andrew.46 on 2014-11-04
> **mc4man said:**
> Whether  there is much to be gained here not up on anymore..

A little difficult to interpret Aoyumi's message:

```

   # The latest aoTuV beta6.03 was unified with Xiph.Org's libvorbis1.3.4. 
The part related to sound quality is not changed from previous version. 

```

but my interpretation is that he has simply altered his work to fit the latest release of libvorbis (1.3.4) with no additional work on ogg sound quality, thus still a worthwhile patch. I am going to have a closer look this weekend but it might be useful for some to look at the simple patch I made against libvorbis 1.3.4, attached to this post. (I usually run this patch against the original source, using an original build script...).

---

### Post by andrew.46 on 2014-11-04
OK so the weekend came a little early and the patch works fine. Created a file:

```

andrew@ilium~/media/luckynight$ **[COLOR="#FF0000"]oggenc -q 8 luckynight.wav [/COLOR]**
Opening with wav module: WAV file reader
Encoding "luckynight.wav" to 
         "luckynight.ogg" 
at quality 8.00
	[ 98.9%] [ 0m00s remaining] \ 

Done encoding file "luckynight.ogg"

	File length:  1m 00.0s
	Elapsed time: 0m 01.4s
	Rate:         43.2773
	Average bitrate: 259.5 kb/s

```

and when tested it is badged appropriately:

```

andrew@ilium~/media/luckynight$ **[COLOR="#FF0000"]mediainfo luckynight.ogg [/COLOR]**
General
Complete name                            : luckynight.ogg
Format                                   : OGG
File size                                : 1.87 MiB
Duration                                 : 1mn 0s
Overall bit rate mode                    : Variable
Overall bit rate                         : 260 Kbps

Audio
ID                                       : 1470759980 (0x57AA042C)
Format                                   : Vorbis
Format settings, Floor                   : 1
Duration                                 : 1mn 0s
Bit rate mode                            : Variable
Bit rate                                 : 256 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 1.85 MiB (98%)
**[COLOR="#FF0000"]Writing library                          : aoTuV 20110424 (UTC 2011-04-24)[/COLOR]**


andrew@ilium~/media/luckynight$ 

```

Note the date which indicates that only the *formatting* of the patch has changed since 2011 not the *content* --> aoTuV Beta6.03 [beta6.02 >> beta6.03] (2011/04/25)...

---

### Post by mc4man on 2014-11-04
> **andrew.46 said:**
> A little difficult to interpret Aoyumi's message:

```

   # The latest aoTuV beta6.03 was unified with Xiph.Org's libvorbis1.3.4. 
The part related to sound quality is not changed from previous version. 

```

but my interpretation is that he has simply altered his work to fit the latest release of libvorbis (1.3.4) with no additional work on ogg sound quality, thus still a worthwhile patch. I am going to have a closer look this weekend but it might be useful for some to look at the simple patch I made against libvorbis 1.3.4, attached to this post. (I usually run this patch against the original source, using an original build script...).
That seems to be a decent view, never really quite got those comments myself.
Thanks for the patch, will add to 1.3.4
(- I don't use vorbis much so really have no view on value..., did notice it creates about a 7% larger file on same encodes

---

### Post by andrew.46 on 2014-11-04
The subversive in me has always preferred ogg vorbis in part because the rest of the world went with mp3 :)

---

