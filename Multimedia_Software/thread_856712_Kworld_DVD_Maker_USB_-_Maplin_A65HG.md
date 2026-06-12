---
title: "Kworld DVD Maker USB - Maplin A65HG"
date: 2008-07-11
forum: Multimedia Software
---

### Post by Blastz on 2008-07-11
Hi,

I've got this USB device working on 8.04 Hardy, but it was a bit of a struggle.

I found a forum with instructions for a very similar card, but it wouldn't work because although the installation installs everything you need, the sample launch commands are wrong for this card.

The link is [http://levien.zonnetjes.net/?q=dvdmaker]("http://levien.zonnetjes.net/?q=dvdmaker")

(Install MPlayer first of course.)
His instructions are:
-----------------
Open a terminal, and go to a directory where you want to store the source-files for the drivers (if you don't have a dedicated source directory, your home-directory should be OK). Then do:

apt-get install linux-source linux-headers-generic mercurial
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)
cd v4l-dvb-kernel
make
sudo make install
--------------------
I changed the last three lines to  this when I got a &#8221;No such file or directory&#8221; error message

cd v4l-dvb-experimental/
make
sudo make install
-----------------

But the command I use to get it working is
mplayer -tv driver=v4l2:input=0:width=720:height=576:normid=0:forceaudio:alsa:adevice=hw.1,0 \-vf screenshot -vf pp=fd -zoom -fs tv://

The difference is the input 0 for AV 1 for S-Video
normid can be 0-3 for PAL-BG, PAL-DG, PAL-I and PAL-H
-fs for fullscreen (alt-F4 to close)

-vf pp=fd is the filter, I don't think it matters which one you use, this one works fine though

Stopping the script and restarting it with different settings sometimes the  settings are not picked up correctly. Just unplug and replug it in after mplayer has stopped.

I couldn't get it to work on a PAL-60 signal properly. The best was to use PAL-H but then the image is black and white.

---

### Post by last_moromete on 2008-08-22
Hi, I have the same device and I&#8221;ve tried to follow the steps described above, but I&#8221;m stuck at &#8221;cd v4l-dvb-kernel&#8221;. I get the message &#8221;No such file or directory&#8221;. Why? Should I install some packages first? Please help!

---

### Post by samsearcher on 2009-02-13
I have been able to make the Kwordd DVD Maker USB 2.0 work by compiling the drivers with help from this page.

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

after compiling the drivers edit /etc/modules and add this line
em28xx

after that I restarted and you can test using tvtime or mplayer. With mplayer try this.

mplayer -tv driver=v4l2:input=1:width=640:height=480:normid=0:adevice=/dev/dsp:audiorate=44100:immediatemode=0:forceaudio tv://

---

### Post by Blastz on 2009-05-03
I'm just trying to get this to work on 9.04, Jaunty and I had the same error message.

When I looked in my home directory there was a folder called v4l-dvb-experimental so I used that instead.

The line became:
cd v4l-dvb-experimental/
make
sudo make install

And now that I look at my instructions above, this looks like the correct way.

---

### Post by coolen on 2009-05-30
Thank you so much. This is working perfectly for me!

I just recorded the intro to Dilbert playing from my XBox using Cheese ^_^

---

### Post by gir861 on 2009-10-24
Hello,
I migrated to Ubuntu from Windows an I need to work with this gadget. I followed the steps from this topic, but I don't have image, just sound. Please help me...

---

### Post by Sirron on 2009-11-07
Windows 7 will allow you to install the driver from Windows Update as an Optional update. Vista probably will do so as well.

To view the device's video you'll want a tool such as VLC or mplayer. VLC might be the easiest to get working with the device.

---

