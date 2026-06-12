---
title: "Ubuntu 8.10 (Intrepid Ibex) Complete Multimedia Codec package installation"
date: 2008-11-04
forum: Multimedia Software
---

### Post by FunkyRider on 2008-11-04
Create a new file named "intrepidgo.sh"

Paste lines between dashes into the file:

---------------------------------------------------
#!/bin/sh

cp /etc/apt/sources.list /etc/apt/sources.list.intrepid_backup
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free" >> /etc/apt/sources.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

apt-get -y update

apt-get -y install totem-xine libxine1-ffmpeg libxine1-gnome libxine1-plugins libxine1
apt-get -y install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly libgstreamer0.10-0
apt-get -y install mplayer mencoder ffmpeg

apt-get -y install libdvdcss2
apt-get -y install w32codecs
---------------------------------------------------

Save it

In command console, execute:

$ sudo sh ./intrepidgo.sh

You will have complete media codec package for your newly installed Intrepid that will play any media format you throw at it. MPlayer is the best choice because it handles more file format then Totem, also it uses less CPU resource to decode the HDTV formats.

Any comments and suggestions please don't hesitate to reply! ):P

---

### Post by basith7 on 2009-01-09
to create and execute the file above may i do it in offline?
thanx reply to my email: [email]annahl.bee@gmail.com[/email]:D

---

### Post by halovivek on 2009-01-09
> **FunkyRider said:**
> Create a new file named "intrepidgo.sh"
Any comments and suggestions please don't hesitate to reply! ):P
Today i will try and tell you.

---

### Post by zeezon1990 on 2009-01-09
How about just installing Ubuntu Tweak and push buttons?

I think it's easy, but your solution is better. It means that I don't need X-windows.

:D

---

