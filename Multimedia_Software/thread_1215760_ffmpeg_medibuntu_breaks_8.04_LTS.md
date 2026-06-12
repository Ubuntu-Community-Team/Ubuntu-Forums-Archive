---
title: "ffmpeg medibuntu breaks 8.04 LTS"
date: 2009-07-17
forum: Multimedia Software
---

### Post by tomjoad on 2009-07-17
I tried to get ffmpeg to work, but have now given up.
(The problem was that avi2flv didn't fix the sound)

However, I now have dependency problems that affects regular 8.04LTS,
php5-ffmpeg (which grabs movie attributes can't be installed),


sources.list WAS prev.
#
[FONT="Courier New"]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #”Illegal” multimedia,
[/FONT]#
now medibuntu-row commented out.
[FONT="Courier New"]apt-get update[/FONT]

upon apt-get install php5-ffmpeg I get:
[B]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-ffmpeg: Depends: libavcodec1d (>= 0.cvs20070307) but it is not going to be installed
               Depends: libavformat1d (>= 0.cvs20070307) but it is not going to be installed
E: Broken packages[/B]


dpkg -l | grep cvs tells:
ii  binutils                          2.18.1~cvs20080103-0ubuntu1
rc  ffmpeg                            3:0.cvs20070307-5ubuntu7.3+medibuntu1
rc  libavcodec1d                      3:0.cvs20070307-5ubuntu7.3            ffmpeg codec library
rc  libavformat1d                     3:0.cvs20070307-5ubuntu7.3            ffmpeg file format library
rc  libavutil1d                       3:0.cvs20070307-5ubuntu7.3            ffmpeg utility library
ii  libedit2                          2.9.cvs.20050518-4                    BSD editline and history libraries
rc  libswscale1d                      3:0.cvs20070307-5ubuntu7.3            ffmpeg video scaling library
ii  libtidy-0.99-0                    20080116cvs-2                 
 
(nothing broken, all ii or rc)

thankful for any help a_s I can't trust regular LTS apt-get upgrade currently..._

---

### Post by tomjoad on 2009-07-17
Untouched LTS (other machine) says;

apt-get install php5-ffmpeg
T[B]he following extra packages will be installed:
  libavcodec1d libavformat1d libavutil1d libdc1394-13 libgsm1 libogg0
  libraw1394-8 libtheora0 libvorbis0a libvorbisenc2[/B]

..

[FONT="Courier New"]dpkg -l | grep cvs =>
i  binutils                          2.18.1~cvs20080103-0ubuntu1
ii  libavcodec1d                      3:0.cvs20070307-5ubuntu7.3   ffmpeg codec library
ii  libavformat1d                     3:0.cvs20070307-5ubuntu7.3   ffmpeg file format library
ii  libavutil1d                       3:0.cvs20070307-5ubuntu7.3   ffmpeg utility library
ii  libedit2                          2.9.cvs.20050518-4           BSD editline and history libraries
ii  libtidy-0.99-0                    20080116cvs-2                HTML syntax checker and reformatter - librar
[/FONT]

---

### Post by tomjoad on 2009-07-17
Silly me...
medibuntu was still around in
/etc/apt/sources.list.d/

all nice after apt-get update

:-)

---

