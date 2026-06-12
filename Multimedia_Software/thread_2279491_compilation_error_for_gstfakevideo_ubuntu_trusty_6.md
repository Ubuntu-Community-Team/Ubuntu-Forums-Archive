---
title: "compilation error for gstfakevideo ubuntu trusty 64-bit"
date: 2015-05-23
forum: Multimedia Software
---

### Post by jurgen-manycolored on 2015-05-23
The idea is to install gstfakevideo and use /dev/video0 for it while moving the webcam device to /dev/video1, which supposedly allows Skype to run correctly.

However, (version 3):

Compile error during make install step - essentially fatal error. Any ideas as to how I can get around this (no libgstfakevideo.so found running make install)?

richard@richard-P5QL-PRO:~$ cd gstfakevideo-read-onlyrichard@richard-P5QL-PRO:~/gstfakevideo-read-only$ sudo make[sudo] password for richard: 
gcc -O2 -Wall -m32  `pkg-config gstreamer-0.10 --cflags` -ldl `pkg-config gstreamer-0.10 --libs` -shared -fpic gst.c gstfakevideo.c -o libgstfakevideo.so
In file included from /usr/include/gstreamer-0.10/gst/gst.h:75:0,
                 from gst.c:25:
/usr/include/gstreamer-0.10/gst/gstutils.h: In function &#8216;GST_READ_DOUBLE_LE&#8217;:
/usr/include/gstreamer-0.10/gst/gstutils.h:755:3: warning: left shift count >= width of type [enabled by default]
   u.i = GST_READ_UINT64_LE (data);
   ^
/usr/include/gstreamer-0.10/gst/gstutils.h:755:3: warning: left shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h:755:3: warning: left shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h:755:3: warning: left shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h: In function &#8216;GST_READ_DOUBLE_BE&#8217;:
/usr/include/gstreamer-0.10/gst/gstutils.h:783:3: warning: left shift count >= width of type [enabled by default]
   u.i = GST_READ_UINT64_BE (data);
   ^
/usr/include/gstreamer-0.10/gst/gstutils.h:783:3: warning: left shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h:783:3: warning: left shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h:783:3: warning: left shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h: In function &#8216;GST_WRITE_DOUBLE_LE&#8217;:
/usr/include/gstreamer-0.10/gst/gstutils.h:865:3: wlibgstfakevideo.soarning: right shift count >= width of type [enabled by default]
   GST_WRITE_UINT64_LE (data, u.i);
   ^
/usr/include/gstreamer-0.10/gst/gstutils.h:865:3: warning: right shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h:865:3: warning: right shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h:865:3: warning: right shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h: In function &#8216;GST_WRITE_DOUBLE_BE&#8217;:
/usr/include/gstreamer-0.10/gst/gstutils.h:892:3: warning: right shift count >= width of type [enabled by default]
   GST_WRITE_UINT64_BE (data, u.i);
   ^
/usr/include/gstreamer-0.10/gst/gstutils.h:892:3: warning: right shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h:892:3: warning: right shift count >= width of type [enabled by default]
/usr/include/gstreamer-0.10/gst/gstutils.h:892:3: warning: right shift count >= width of type [enabled by default]
gst.c: In function &#8216;shim_ioctl&#8217;:
gst.c:270:8: error: &#8216;VIDIOCKEY&#8217; undeclared (first use in this function)
   case VIDIOCKEY:
        ^
gst.c:270:8: note: each undeclared identifier is reported only once for each function it appears in
gst.c:286:8: error: &#8216;VIDIOCGUNIT&#8217; undeclared (first use in this function)
   case VIDIOCGUNIT:
        ^
gst.c:288:8: error: &#8216;VIDIOCGCAPTURE&#8217; undeclared (first use in this function)
   case VIDIOCGCAPTURE:
        ^
gst.c:290:8: error: &#8216;VIDIOCSCAPTURE&#8217; undeclared (first use in this function)
   case VIDIOCSCAPTURE:
        ^
gst.c:292:8: error: &#8216;VIDIOCSPLAYMODE&#8217; undeclared (first use in this function)
   case VIDIOCSPLAYMODE:
        ^
gst.c:294:8: error: &#8216;VIDIOCSWRITEMODE&#8217; undeclared (first use in this function)
   case VIDIOCSWRITEMODE:
        ^
gst.c:296:8: error: &#8216;VIDIOCGPLAYINFO&#8217; undeclared (first use in this function)
   case VIDIOCGPLAYINFO:
        ^
gst.c:298:8: error: &#8216;VIDIOCSMICROCODE&#8217; undeclared (first use in this function)
   case VIDIOCSMICROCODE:
        ^
gst.c: In function &#8216;cb_handoff&#8217;:
gst.c:85:10: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result [-Wunused-result]
     write(videopipe[1],GST_BUFFER_DATA(buffer),GST_BUFFER_SIZE(buffer));
          ^
/usr/include/bits/fcntl2.h: In function &#8216;open&#8217;:
gstfakevideo.c:164:7: warning: ignoring return value of &#8216;pipe&#8217;, declared with attribute warn_unused_result [-Wunused-result]
   pipe(videopipe);
       ^
make: *** [libgstfakevideo.so] Error 1
richard@richard-P5QL-PRO:~/gstfakevideo-read-only$ sudo make install
cp libgstfakevideo.so /usr/local/lib
cp: cannot stat &#8216;libgstfakevideo.so&#8217;: No such file or directory
make: *** [install] Error 1
richard@richard-P5QL-PRO:~/gstfakevideo-read-only$ 

I have gcc-multilib, libc6-dev-i386 and libc6-i386 installed. I also have -m32 in CFLAGS in the makefile. These were recommended for fatal compile errors in the make step.  But no references found for libgstfakevideo.so not found.  It looks like it tried to be created in the make step but couldn't for reasons unknown to me (or maybe anybody).
The file libgstfakevideo.so was definitely not in the directory, as I checked in case the compiler was lying to me.
Here is output from the install (with errors corrected as he went along) for Ubuntu by someone for 10:10 Ubuntu. My preliminary steps before the compilation were the same as his:

Sunday, August 15, 2010
installing gstfakevideo on ubuntu
/etc/init.d/udev reload

apt-get install libgstreamer0.10-dev pkg-config
svn checkout [http://gstfakevideo.googlecode.com/svn/trunk/](http://gstfakevideo.googlecode.com/svn/trunk/) gstfakevideo
cd gstfakevideo
make
make install
Create a new file called skype.sh and add these lines:
#!/bin/sh
qcset /dev/video1 compat=dblbuf
gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace

[http://www.kuhrti.de/index.php/linux/webcam-linux-and-skype-it-works/](http://www.kuhrti.de/index.php/linux/webcam-linux-and-skype-it-works/)


sudo apt-get install libgstreamer0.10-dev pkg-config
[sudo] password for xxxx:
Reading package lists... Done
Building dependency tree
Reading state information... Done
pkg-config is already the newest version.
The following extra packages will be installed:
libglib2.0-dev libxml2-dev
Suggested packages:
libglib2.0-doc python-subunit gstreamer0.10-doc
The following NEW packages will be installed:
libglib2.0-dev libgstreamer0.10-dev libxml2-dev
0 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 2,759kB of archives.
After this operation, 10.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libglib2.0-dev 2.24.1-0ubuntu1 [1,123kB]
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libglib2.0-dev 2.24.1-0ubuntu1 [1,123kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libxml2-dev 2.7.6.dfsg-1ubuntu1 [751kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libgstreamer0.10-dev 0.10.28-1 [886kB]
Fetched 2,759kB in 53s (51.5kB/s)
Selecting previously deselected package libglib2.0-dev.
(Reading database ... 216720 files and directories currently installed.)
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.24.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libxml2-dev.
Unpacking libxml2-dev (from .../libxml2-dev_2.7.6.dfsg-1ubuntu1_i386.deb) ...
Selecting previously deselected package libgstreamer0.10-dev.
Unpacking libgstreamer0.10-dev (from .../libgstreamer0.10-dev_0.10.28-1_i386.deb) ...
Processing triggers for man-db ...
Setting up libglib2.0-dev (2.24.1-0ubuntu1) ...
Setting up libxml2-dev (2.7.6.dfsg-1ubuntu1) ...
Setting up libgstreamer0.10-dev (0.10.28-1) ...

svn checkout [http://gstfakevideo.googlecode.com/svn/trunk/](http://gstfakevideo.googlecode.com/svn/trunk/) gstfakevideo
The program 'svn' is currently not installed. You can install it by typing:
sudo apt-get install subversion

sudo apt-get install subversion
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
libapr1 libaprutil1 libsvn1
Suggested packages:
subversion-tools db4.8-util
The following NEW packages will be installed:
libapr1 libaprutil1 libsvn1 subversion
0 upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
Need to get 1,411kB of archives.
After this operation, 6,836kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libapr1 1.3.8-1build1 [116kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libaprutil1 1.3.9+dfsg-3build1 [85.4kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libsvn1 1.6.6dfsg-2ubuntu1 [838kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main subversion 1.6.6dfsg-2ubuntu1 [372kB]
Fetched 1,411kB in 18s (74.3kB/s)
Selecting previously deselected package libapr1.
(Reading database ... 217131 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.3.8-1build1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.3.9+dfsg-3build1_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.6.6dfsg-2ubuntu1_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.6.6dfsg-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libapr1 (1.3.8-1build1) ...

Setting up libaprutil1 (1.3.9+dfsg-3build1) ...

Setting up libsvn1 (1.6.6dfsg-2ubuntu1) ...

Setting up subversion (1.6.6dfsg-2ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


svn checkout [http://gstfakevideo.googlecode.com/svn/trunk/](http://gstfakevideo.googlecode.com/svn/trunk/) gstfakevideo

A gstfakevideo/README-AMD64
A gstfakevideo/gstfakevideo
A gstfakevideo/gstfakevideo.c
A gstfakevideo/README
A gstfakevideo/Makefile
A gstfakevideo/gst.c
Checked out revision 3.

cd gstfakevideo
xxx@xxx:~/gstfakevideo$


make
gcc -O2 -Wall -m32 `pkg-config gstreamer-0.10 --cflags` -ldl `pkg-config gstreamer-0.10 --libs` -shared -fpic gst.c gstfakevideo.c -o libgstfakevideo.so
gst.c: In function &#8216;cb_handoff&#8217;:
gst.c:85: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
gstfakevideo.c: In function &#8216;open&#8217;:
gstfakevideo.c:164: warning: ignoring return value of &#8216;pipe&#8217;, declared with attribute warn_unused_result

make install
cp libgstfakevideo.so /usr/local/lib
cp: cannot create regular file `/usr/local/lib/libgstfakevideo.so': Permission denied
make: *** [install] Error 1

after sudo
cp libgstfakevideo.so /usr/local/lib
chmod 0755 /usr/local/lib/libgstfakevideo.so
cp gstfakevideo /usr/local/bin
chmod 0755 /usr/local/bin/gstfakevideo

As you see, he doesn't have the same problem I had.

Here is the README file for gstfakevideo:

Compile and install:

    make && make install

    AMD64 users may need to add "-m32" to CFLAGS in Makefile

Configuration:

    Default configuration can be changed either in source or
    in gstfakevideo script.

    To change the install path, have a look inside the Makefile.

Start:
    Be sure that your skype is reachable over your PATH variable.
    Then just type:

    $ gstfakevideo [gst-launch syntax video pipe definition]

Some examples:
    Avatar image streaming:
    gstfakevideo filesrc location=avatar.jpg ! jpegdec ! \
            videoscale ! ffmpegcolorspace 

    v4l source (i.e. webcam on /dev/video1) with vergotv effect:
    (if your cam use /dev/video0, simply: mv /dev/video0 /dev/video1)

    gstfakevideo v4lsrc device=/dev/video1 ! videoscale ! ffmpegcolorspace ! \
            vertigotv ! ffmpegcolorspace ! autovideosink

    gstfakevideo videotestsrc is-live=true
    

BUGS:
    at present, gstfakevideo simulates only /dev/video0
    properly, so if you have other video device configure it to use
    device file other than /dev/video0

which is the reason why sudo mv /dev/video0 /dev/video1 would be a command in my script to start skype.

There is a second readme, README-AMD64, but it was done on open SUSE, which uses RPMs, and wasn't very helpful.  It did say there was a problem compiling, but I don't know if the solution can be translated into .deb.

Here it is, just for the record:

Compilation of skype_dsp_hijacker on AMD64
by Danyel Ceccaldi, <danyel.ceccaldi@gmx.de>
(original version: [http://juljas.net/linux/skype/amd64.html](http://juljas.net/linux/skype/amd64.html))
-----------------------------------------------------

I want to submit informations back to you, as I tried to compile the library on
opensuse10, on an AMD64 / x86_64 platform.  I encountered the following
problem:

  $ make
  gcc -O2 -Wall -ldl -shared -fpic skype_dsp_hijacker.c -o libskype_dsp_hijacker.so
  
  $ file libskype_dsp_hijacker.so
  libskype_dsp_hijacker.so: ELF 64-bit LSB shared object, AMD x86-64, version 1
  (SYSV), not stripped

  $ ./skype_dsp_hijacker skype
  ERROR: ld.so: object './libskype_dsp_hijacker.so' from LD_PRELOAD cannot be
  preloaded: ignored.

Reason:
on this environment, the default architecture to build is 64-Bit, but skype is
32-bit.

Simply adding CFLAGS=-m32 will not help, as the build environment is not
prepared.

Solution:
assure the following rpm's are installed:
glibc-devel-32bit
glibc-locale-32bit
glibc-32bit

# cd /lib
# ln -s /lib/libdl.so.2 libdl.so
# ln -s /lib/libc.so.6 libc.so
# rpm -i suse/x86_64/glibc-devel-32bit-2.3.5-40.x86_64.rpm

$ gcc -m32 -ldl -shared -fpic skype_dsp_hijacker.c -o libskype_dsp_hijacker.so

$ file libskype_dsp_hijacker.so
libskype_dsp_hijacker.so: ELF 32-bit LSB shared object, Intel 80386, version 1
(SYSV), not stripped


(some hints indicated using also -L/lib, but it seems not necessary on
opensuse10 or not necessary at all)

---

### Post by mc4man on 2015-05-23
you do realize that is code written for 32 bit *8 years ago*. Seems a bit of a stretch to get it to compile & work in a 2014 64 bit install/libs, ect.

---

### Post by jurgen-manycolored on 2015-05-23
Not helpful.  This is the LATEST version and was compiled for 64-bit AMD ubuntu by someone else, given that it was an older version.  Pray tell me, what do you expect me to use?? I'm looking for solutions, not sarcastic comments.

For someone who WANTS to help, here is some additional information, in case it may be helpful:

richard@richard-P5QL-PRO:~$ dpkg -l | grep libv4l-dev
ii  libv4l-dev:amd64                                      1.0.1-1                                             amd64        Collection of video4linux support libraries (development files)
richard@richard-P5QL-PRO:~$ locate videodev.h
/usr/include/libv4l1-videodev.h
/usr/include/linux/videodev.h



[https://code.google.com/p/gstfakevideo/source/browse/#svn%2Ftrunk](https://code.google.com/p/gstfakevideo/source/browse/#svn%2Ftrunk)

---

### Post by jurgen-manycolored on 2015-05-23
It might be that a filename in Debian or Ubuntu has been changed in the intervening time between the last version of gstfakevideo which does not allow the compilation to complete, but I have no idea what that might be.  Everything I have found related to getting webcams working on Skype in Ubuntu point to trying gstfakevideo as a solution for a nonworking webcam in Skype without any reference to file changes vis-a-vis compilation, so I have nothing to go on unless someone knows the answer.

---

### Post by Vladlenin5000 on 2015-05-24
Please use code tags when posting such results (Go advanced, pres "#" and paste inside). It's an awful lot of text that detracts many users from reading and contributing.

Regarding your issue, I have to agree with mc4man. Even if it was later compiled for 64-bit it was a long long time ago and many changes happened in Ubuntu since. BTW, the comment wasn't sarcastic, it was factual and to the point.

Now, instead of looking for a "solution" (compiling) for what you think is a "solution" (gstfakevideo) (it might have been a long long time ago, but even then it was nothing but a "dirty" workaround), **why don't you explain what your problem really is**? Also post info regarding the hardware (webcam), Skype version, etc. Perhaps there's a proper (updated) solution...

PS - The use of such "tone" in this forum isn't conducive to a solution.

---

### Post by jurgen-manycolored on 2015-05-24
22I have been following the Ubuntu wiki on webcams. This was a suggested fix if the others didn't work.  This issue has been around since 2007 for persons using both 32- and 64-bit distributions, and Google code does not seem to have addressed the issue.  As far as being old code, my friend compiled it yesterday on Debian Jessie; he compiles his own kernel, using the latest kernel from Linux.  He refuses to have any 32-bit packages on his system, so he effectively compiled the code on a new 64-bit distribution.  I have tried numerous fixes to get the camera working (and a second one), and I have posted the problem addressing the camera on Ubuntu community without any successful answers offered.  Now trying to use this workaround, which by the way, is the latest version (3), I need to be able to compile it to see if in fact it works. As far as the amount of text in my first post is concerned, I thought it was helpful to give the full compiler output; but if that is a hinderance, I will refrain from doing so unless asked.

As far as any updated solution for my problem, I have been unable thus far to find any new information on getting my logitech 9000 to work in Skype 4.3 and Ubuntu trusty.

---

### Post by Vladlenin5000 on 2015-05-24
The problem isn't the amount of text, it's the formating: [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by Vladlenin5000 on 2015-05-24
Logitech Quickcam Pro 9000 is and always has been 'buggy' in Linux but the problems apparently are now restricted to Skype. 
I can't help you with that.

In all similar situations I always ask: How valuable is your time? Mine certainly worth a lot more than the $10 (or $15 or $20 or $50 or $75 or even $100!!) it would cost a new, fully supported, webcam.

---

### Post by mc4man on 2015-05-24
If your friend built the .so on Jessie then get a copy & attach to a post here (either append a .txt to it or place in a folder & compress folder to .tar.gz
Would be interesting to see the ldd on it & take a look inside.
(-if he is using wheezy then don't bother

---

### Post by Yellow Pasque on 2015-05-25
Why can't you just symlink video1 to video0?

Maybe you'll get some ideas here?: [https://bbs.archlinux.org/viewtopic.php?id=73459](https://bbs.archlinux.org/viewtopic.php?id=73459)
(The LD_PRELOAD commands will be a bit different because Arch uses /usr/lib64

---

