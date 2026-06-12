---
title: "HOWTO: Enable TV out (S-Video) on the ATI Radeon 7000"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by momeni on 2008-03-18
Hello world.
This is not a question. This is a HOW-TO instruction guide for enabling TV out (S-video) on the [COLOR="Blue"]ATI Radeon 7000[/COLOR].

If you have an [COLOR="Blue"]ATI Radeon 7000[/COLOR] graphic card and want to enable TV out, you can follow this step by step guide.
1) Run following code:
```

cd ~
mkdir graphic

```

2) Download following files to the *graphic* folder.
[renderproto-0.9.3.tar.gz]("http://xorg.freedesktop.org/releases/individual/proto/renderproto-0.9.3.tar.gz")
[videoproto-2.2.2.tar.gz]("http://xorg.freedesktop.org/releases/individual/proto/videoproto-2.2.2.tar.gz")
[xextproto-7.0.2.tar.gz]("http://xorg.freedesktop.org/releases/individual/proto/xextproto-7.0.2.tar.gz")
[xf86driproto-2.0.3.tar.gz]("http://xorg.freedesktop.org/releases/individual/proto/xf86driproto-2.0.3.tar.gz")
[xf86-video-ati-6.8.0.tar.gz]("http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.8.0.tar.gz")

3) Install following packages: (You may find them from Ubuntu gutsy DVD or [http://packages.ubuntu.com](http://packages.ubuntu.com) or ......)
> 
xserver-xorg-dev_1.3.0.0.dfsg-12ubuntu8.3_i386.deb
x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb
x11proto-xf86misc-dev_0.9.2-4ubuntu1_all.deb
x11proto-gl-dev_1.4.8-1_all.deb
x11proto-core-dev_7.0.10-2_all.deb
x11proto-input-dev_1.4.2-1_all.deb
x11proto-kb-dev_1.0.3-2ubuntu1_all.deb
xtrans-dev_1.0.3-2_all.deb
mesa-common-dev_7.0.1-1ubuntu3_all.deb
atitvout_0.4-7_i386.deb
x11proto-fonts-dev_2.0.2-5ubuntu1_all.deb
x11proto-randr-dev_1.2.1-2_all.deb
libdrm-dev_2.3.0-4ubuntu1_i386.deb


4) After installing above packages go to graphic directory (the place that you download .tar.gz files) and run following codes in a terminal:
```

tar -xzvf renderproto-0.9.3.tar.gz
tar -xzvf videoproto-2.2.2.tar.gz
tar -xzvf xextproto-7.0.2.tar.gz
tar -xzvf xf86driproto-2.0.3.tar.gz
tar -xzvf xf86-video-ati-6.8.0.tar.gz

cd renderproto-0.9.3
./configure
sudo make install

cd ../videoproto-2.2.2
./configure
sudo make install

cd ../xextproto-7.0.2
./configure
sudo make install

cd ../xf86driproto-2.0.3
./configure
sudo make install

cd ../xf86-video-ati-6.8.0
export XORG_PREFIX="/usr"
export XORG_CONFIG="--prefix=$XORG_PREFIX --sysconfdir=/etc --localstatedir=/var"
./configure $XORG_CONFIG --with-xorg-module-dir=/usr/lib/xorg/modules
make
sudo make install

```

After end of this setup, you must reboot computer in order to changes take effect.
After rebooting:
Since now you can turn on TV by:
```

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

```
and turn off TV by:
```

xrandr --output S-video --off

```

OK :KS
If you want to play a video, the video will be played on your monitor but on the TV only a blank window will be displayed. (In cases else of video playing, TV and monitor will show same things without any problem) In order to watch the video in your TV you must turn off your VGA output (Monitor) first.
You can turn off your monitor by:
```

xrandr --output VGA-0 --off

```
and turn it on after video watching, simply by:
```

xrandr --output VGA-0 --mode 1280x768

```

**IMPORTANT NOTE:**
1) S-video output only may work in the 800x600 resolution.
2) In the command which I offer for turning VGA on again, the 1280x768 is my monitor resolution and you must replace it with your own. If you replace this resolution with a non-supported one (by your monitor) the VGA will not become enable! You can see your monitor's supported resolutions by:
```

xrandr --prop

```
Also if you use a non-supported resolution there, you can simply restart X server using _Ctrl+Alt+Backspace_. By restarting X server TV will become off and VGA will become on again.

Above configuration, works very well on my computer.
Let yourself free to quote any comment on this guide.

Have a lot of fun :)
Momeni

---

