---
title: "ATI - Rage Theathre - Radeon 9250 (9200 SE) TV-OUT"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by Pawel on 2006-06-11
Welcome Everybody! :)


At first - sorry if my english will be not understand ;)

I wan't to slove my problem with ATI's card and also help other pople who may the same or similar problem with their ATI's card.

Short description:

HARDWARE: ATI Radeon 9250 (9200 SE), with 128 MB of RAM.
SOFT: UBUNTU of course (6.06).

The binary driver from ATI (fglrx) doesn't work (no accel, if tv is connected then picture on primary monitor (crt) like gamma correction is too high).

The open source driver work partially ("ati" - accel is ok, but tv-out doesn't work//no synchro. on TV).
And here is my question:

How to make open source driver to work with this card (that TV-OUT will be available) ?
From xorg log file:
> (II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
Especially the last line... - what is the "multimedia table" ?

My xorg.conf file is located here:
[http://schemacik.webpark.pl/ubu/xorg.conf](http://schemacik.webpark.pl/ubu/xorg.conf)

Does ubuuntu pre-compiled xorg open-source drivers requires add a path form gatos.sf.net ?
If yes - why it doesn't compile ? (i get an error like:
> usr/include/GL/glxint.h:95: error: syntax error before 'GLboolean' 
---------------
I try to ask for help and i try to make this topic name right as much as posibble to help find it in the future ;-)

If somebody have TV-out works fine with the open source driver - please - post your xorg.conf file.

Thank You!


Best regards
Pawel W.

---

### Post by danoyoto on 2006-06-11
please let know if you figure this out, I have the same card.  Currently running the default drivers installed.

---

### Post by ~A~ on 2006-06-13
I've been searching for a nice solution. The best i've found so far is using SWcursor instead of HWcursor with the fglrx driver from synaptic/apt-get.
For your Xorg.conf:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"fglrx"
	Option		"SWcursor"	"true"
	BusID		"PCI:1:0:0"
EndSection

```
It is also kind of interresting to know that the fglrx driver from synaptic for kernel 2.6.12-9 only worked if the linux-restricted modules were installed.

Arnout

---

### Post by elleP on 2006-06-15
Tnx!
I've been looking for a solution for this since 5.10!

Too bad that SWcursor leaves some holes in my display when I move my mouse. But at least I can watch movies on my tv again, something that has been holding me back from using linux full time.

---

### Post by Pawel on 2006-08-16
Hello everyone!

I just want to say that i got working TV-OUT on this card.

:) 

Few days ago i tried again to compile open source radeon driver with patch.  It's working now.
It automaticlly turns tv-out on when we switch to 800x600 resolution. Monitor picture goes then strange but when we watch TV - it isn't important. (Just turn off monitor). And it also automaticlly turns off tv-out when we back to e.g. 1024x768 resolution.


All infos are located on:
[http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html)
> # Most modern systems use the Xorg 7.0 as default.
# If so you will only need to patch and compile the ati driver. 
# Grab a driver release from [http://xorg.freedesktop.org/releases/individual/driver/](http://xorg.freedesktop.org/releases/individual/driver/) :
wget [http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.5.8.0.tar.bz2](http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.5.8.0.tar.bz2)

# Grab a matching patch from [http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html) :
wget [http://megahurts.dk/rune/stuff/xorg7-6.5.8.0-tv_output.patch.gz](http://megahurts.dk/rune/stuff/xorg7-6.5.8.0-tv_output.patch.gz)

# Extract, patch:

tar xjvf xf86-video-ati-6.5.8.0.tar.bz2
gunzip -c xorg7-6.5.8.0-tv_output.patch.gz | \
  patch -p1 -d xf86-video-ati-6.5.8.0

# Compile:
# make sure you have installed the xorg
# and x11 proto development packages for your distribution
export XORG_PREFIX="/usr" (XORG_PREFIX/bin is where Xorg is located)
export XORG_CONFIG="--prefix=$XORG_PREFIX --sysconfdir=/etc --localstatedir=/var"
./configure $XORG_CONFIG --with-xorg-module-dir=$XORG_PREFIX/lib/X11/modules
make

# Install:
make install

# Edit your /etc/X11/xorg.conf according to
# ./xf86-video-ati-6.5.8.0/src/README.out :
# * Set the resolution to 800x600
# * In the "Device" section, add:
    Option "MonitorLayout" "AUTO, NONE"
    Option "TVOutput"      "PAL"       (or "NTSC", etc.)

# Start X and rejoice.
Xorg
  

P.S. in my case i use:
> Option "MonitorLayout" "AUTO, AUTO"

P.S.2 Thanks for people who is making gatos project for great job.

Hope this helps.

It works fine on my computer and also computer belongs to my Brother.

If you have any question - just ask :) I 'll try to give some advice if i can.

Best Regards
Pawel

---

### Post by Darth Tux on 2006-08-26
I got my 9250 working with the latest 8.28.8 drivers. In earlier releases I had to used this [guide]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26"). 3D acceleration worked right off the bat with the new drivers and I added [ Option "AGPv3Mask" "0x00000002" ] to my xorg.conf under the "Device" section.I added that to stop random freezing and complete lock-ups I was experiencing in games. Hope this helps.

---

