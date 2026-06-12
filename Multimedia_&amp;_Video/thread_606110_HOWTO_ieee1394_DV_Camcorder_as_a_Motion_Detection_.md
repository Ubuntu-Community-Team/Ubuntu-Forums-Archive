---
title: "HOWTO: ieee1394 DV Camcorder as a Motion Detection Camera"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by RemmyLee on 2007-11-07
Now as many of you know, Video4Linux still has its drawbacks. For instance, it is currently unable to use most DV camcorders as a V4L device, however, there are ways around this. The following will set up you DV camcorder as a motion detection system. 

> 
**NOTES: **

This assumes that you already have your DV camera working in linux and you're able to access it via Kino or dvgrab. 

This also assumes that you have none of the prerequisites installed.

This has been tested with Gutsy only. YMMV

**Software Used:**
vloopback
dvgrab
dv2vloopback
motion

**Step 1. Download/Configure/Install vloopback**
```
svn co http://www.lavrsen.dk/svn/vloopback/trunk/ vloopback
cd vloopback
make
sudo make install
sudo modprobe videodev
sudo modprobe vloopback pipes=2

```

**Step 2. Download/Install Dependencies**
```

sudo apt-get install linux-headers-`uname -r` gcc libgd2-xpm libgd2-xpm-dev

```

**Step 3. Downlaod/Install dvgrab and motion**
```

sudo apt-get install dvgrab motion

```

**Step 4. Download/Make dv2vloopback**
```

wget http://internap.dl.sourceforge.net/sourceforge/dv2vloopback/dv2vloopback0.02.tar.gz
tar xvzf dv2vloopback0.02.tar.gz
cd dv2vloopback
make

```

**Step 5. Putting it all together.**
Run dv2vloopback as follows:
```

./dv2vloopback /dev/video0 **width**x**height**x24 10

```

What this line means:
run dv2vloopback and write images grabbed with dvgrab to the pipe on the V4L device located at /dev/video1 with a width of x and height of x and a color space of 24bits (RGB) at 10 frames per second.

Width and Height should be values supported by your camera. Common values are: 180x120 320x240 352x240 640x480 720x480

Notice that even though we specify 10 frames per second, dv2vloop is not currently able to acheive that framerate as it uses the hard drive for temporarily storing intermediate images.

**Step 6. motion**
before running motion, you will need to configure it via its conf file:
```
sudo gedit (or sudo nano) /etc/motion/motion.conf
```

Change the device setting to video1:
```

videodevice /dev/video1

```

Specify the location you would like to save your images:
```

# Target base directory for pictures and films (you may need
# to change this (or change its permissions) depending on
# which system user runs motion).
target_dir /home/user/Pictures (for example)

```
You can play around with other options if you like, but for simplistic capturing, this should be all you need.

Check that your camera is on and run motion. Do to the limitations of dv2vloopback, you may only get between 1-2 frames per second.

---

