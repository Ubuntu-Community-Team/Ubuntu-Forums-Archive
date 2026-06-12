---
title: "DVDStyler 1.8.3  build Maverick"
date: 2011-04-02
forum: Multimedia Software
---

### Post by fmdex2011 on 2011-04-02
Good news, dvdstyler 1.8.3 was released today 4/2/2011

I downloaded DVDStyler-1.8.3.tar.bz2 and wxsvg-1.0.8-1.tar.bz2 from sourceforge.net and I am going to attempt to compile them on ubuntu 10.10 amd64

This should also work on ubuntu 10.10 i386 as well if you want to try it along with me or give me pointers when I smack into the inevitable wall

The dependencies listed in the dvdstyler package are:

    cdrtools >= 2.01 ([http://cdrecord.berlios.de/private/cdrecord.html](http://cdrecord.berlios.de/private/cdrecord.html))
    dvdauthor >= 0.6.14 ([http://dvdauthor.sourceforge.net](http://dvdauthor.sourceforge.net))
    dvd+rw-tools >= 7.1 ([http://fy.chalmers.se/~appro/linux/DVD+RW/tools/](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/))
    ffmpeg >= 0.4.9 20080823, libavformat >= 52.21.0 ([http://ffmpeg.mplayerhq.hu](http://ffmpeg.mplayerhq.hu))
    gettext >= 0.17 ([http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/))
    libexif12 >= 0.6.16 ([http://libexif.sourceforge.net](http://libexif.sourceforge.net))
    wxGTK >= 2.8.7 ([http://www.wxwidgets.org/downloads/](http://www.wxwidgets.org/downloads/))
    wxSVG >= 1.0.8 ([http://wxsvg.sourceforge.net](http://wxsvg.sourceforge.net))
    xine-ui >= 0.99.1 ([http://xinehq.de/](http://xinehq.de/))

(looks the same as version 1.8.2 although the change log states dvdauthor is now 0.7.0)

The dependencies in the wxsvg package are:

    wxGTK >= 2.6.3 ([http://www.wxwidgets.org](http://www.wxwidgets.org))
    ffmpeg >= 0.4.9_p20070616 ([http://ffmpeg.mplayerhq.hu](http://ffmpeg.mplayerhq.hu))
    libtool >= 1.5.26 ([http://www.gnu.org/software/libtool/](http://www.gnu.org/software/libtool/))

I'll start with the wxsvg package first, in the synaptic package manager I have checked and installed:

python-wxgtk2.6 ver 2.6.3.2.2-5ubuntu1
ffmpeg ver 4:0.6-2ubuntu6
libtool ver 2.2.6b-2ubuntu1
libltdl7 ver 2.2.6b-2ubuntu1
libltdl-dev ver 2.2.6b-2ubuntu1

Now to compile, I have extracted wxsvg-1.0.8-1.tar.bz2 to an empty folder called xmit

Open terminal and install checkinstall, you will see why later on

type: cd xmit
to get into the xmit folder

Type: cd wxsvg-1.0.8-1
to get into the extracted folder

Type: ./configure
check for errors when its done

Type: make
check for errors when its done

Type: sudo checkinstall
this creates a .deb file that is easy to remove or install later on, or you can just type: sudo make install, either way wxsvg 1.0.8 will be installed, you just won't see it using sudo make install

Everything worked so far, to be continued....

---

### Post by fmdex2011 on 2011-04-03
The next dvdstyler dependencies can be found in the ubuntu software center or the synaptic package manager

    dvd+rw-tools >= 7.1 ([http://fy.chalmers.se/~appro/linux/DVD+RW/tools/](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/))
    libavformat >= 52.21.0 ([http://ffmpeg.mplayerhq.hu](http://ffmpeg.mplayerhq.hu))
    gettext >= 0.17 ([http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/))
    libexif12 >= 0.6.16 ([http://libexif.sourceforge.net](http://libexif.sourceforge.net))
    xine-ui >= 0.99.1 ([http://xinehq.de/](http://xinehq.de/))

In the synaptic package manager I have checked and installed:

dvd+rw-tools ver 7.1-6
libburn4 ver 0.8.0.pl00-2
libavformat52 ver 4:0.6-2ubuntu6
libavformat-dev ver 4:0.6-2ubuntu6
gettext ver 0.18.1.1-1ubuntu2
liblocale-gettext-perl ver 1.05-6
gettext-base ver 0.18.1.1-1ubuntu2
po-debconf ver 1.0.16
libgtksourceview2.0-common ver 2.10.5-0ubuntu1
autotools-dev ver 20100122.1
libexif-dev ver 0.6.19-1
libexif12 ver 0.6.19-1
xine-ui ver 0.99.6-1
x11proto-xinerama-dev ver 1.2-2
libxine1-ffmpeg ver 1.1.18.1-4ubuntu4
libxine1-x ver 1.1.18.1-4ubuntu4
libxine1-bin ver 1.1.18.1-4ubuntu4
libxine1-misc-plugins ver 1.1.18.1-4ubuntu4
libxine1 ver 1.1.18.1-4ubuntu4
libxinerama1 ver 2:1.1-3
libxinerama-dev ver 2:1.1-3
libxine1-console ver 1.1.18.1-4ubuntu4
libvcdinfo0 ver 0.7.23-4ubuntu2

The dvdstyler dependency:

    dvdauthor >= 0.6.14 ([http://dvdauthor.sourceforge.net](http://dvdauthor.sourceforge.net))

can also be found in the ubuntu software center or the synaptic package manager as:

dvdauthor ver 0.6.18-1build1

However the dvdstyler 1.8.3 change log calls out dvdauthor ver 0.7.0, so I will compile that version instead, to be continued....

---

### Post by fmdex2011 on 2011-04-05
I downloaded dvdauthor-0.7.0.tar.gz from sourceforge.net and extracted it to an empty folder called xmit

There are no dependencies for this package, so it should be a nice easy compile
Before you start, you have to rename the extracted folder from dvdauthor to dvdauthor-0.7.0
checkinstall needs the version number to create the .deb file at the end

Open terminal and type: cd xmit
to get into the xmit folder

Type: cd dvdauthor-0.7.0
to get into the extracted folder

Type: ./configure
check for errors when its done

Type: make
check for errors when its done

Type: sudo checkinstall
no errors?  we're done!

On to the next dependency,  wxGTK >= 2.8.7 ([http://www.wxwidgets.org/downloads/](http://www.wxwidgets.org/downloads/))

I downloaded wxWidgets-2.9.1.tar.bz2, but I found version 2.8.11 is already on my system

In the synaptic package manager I have checked and installed:

python-wxgtk2.8 ver 2.8.11.0-0ubuntu4
python-wxtools ver 2.8.11.0-0ubuntu4
python-wxversion ver 2.8.11.0-0ubuntu4
libwxbase2.8-dev ver 2.8.11.0-0ubuntu4
libwxbase2.8-0 ver 2.8.11.0-0ubuntu4
wx-common ver 2.8.11.0-0ubuntu4
wx2.8-headers ver 2.8.11.0-0ubuntu4
libwxgtk2.8-dev ver 2.8.11.0-0ubuntu4
libwxgtk2.8-0 ver 2.8.11.0-0ubuntu4

The last dependency listed in the dvdstyler 1.8.3 package is:

    cdrtools >= 2.01 ([http://cdrecord.berlios.de/private/cdrecord.html](http://cdrecord.berlios.de/private/cdrecord.html))

I downloaded cdrtools-3.00.tar.bz2, extracted it to an empty folder called xmit, and started reading the contents

Not to long later I had a flashback to the Top Gun movie where Goose and Maverick are caught in a flat spin about to crash

This is not good Maverick, this is not good

Needless to say, I have had trouble compiling cdrtools before, but it can be done

One way to do it is using a script from here:  [http://muaythaimaster74.blogspot.com/2010/05/ubuntu-cdrtools-script.html](http://muaythaimaster74.blogspot.com/2010/05/ubuntu-cdrtools-script.html)
I have read through it several times and it should work, but I have not tried it myself

Another way is from a :ppa on launchpad.net here:  [https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

To install cdrtools 3.00, open a terminal and type:

sudo add-apt-repository ppa:brandonsnider/cdrtools

Then type:  sudo apt-get update

Go to the synaptic package manager, then check and install:

cdrecord ver 10:3.00-0ubuntu1~maverick~cdrtoolsppa1
cdda2wav ver 10:3.00-0ubuntu1~maverick~cdrtoolsppa1
mkisofs ver 10:3.00-0ubuntu1~maverick~cdrtoolsppa1

Thats it!  Now I can move on to compile dvdstyler 1.8.3  right?

to be continued....

---

### Post by schily on 2011-04-06
In contrary to most other software, there is no problem to compile cdrtools.

Just call "make" as usual.....

---

### Post by fmdex2011 on 2011-04-28
Well, its been a while, and as some of you may have guessed, I have ran into some problems with the final compile.

There were changes with ffmpeg and wxwidgets that set me back a bit, but I am still working on it as time permits.

Does anyone know if there is a Git repository for dvdstyler ?

Should I start one ?

Anyone have 2 cents to spare ? ( LOL )

to be continued....

---

### Post by mocha on 2011-04-30
I'm trying to get 1.8.3 to compile also but I can't get past the configure script step.  It's having a problem with avutil.h which was not used for compiling wxsvg for some reason, but it's strange because I have 1.8.2 on my system which I compiled as well with wxsvg 1.0.7 and it also did not use avutil.h but the dvdstyler configure script didn't complain about that...

This is in my wxsvg 1.0.7 config.log:

```
fatal error: ffmpeg/avutil.h: No such file or directory
```

yet dvdstyler 1.8.2 configure says that wxsvg with ffmpeg was found..

The same thing is definitely not happening with dvdstyler 1.8.3 and wxsvg 1.0.8

---

### Post by fmdex2011 on 2011-04-30
Hi mocha,

I have had similar problems with ffmpeg and wxsvg 1.0.8

I am going to remove ffmpeg (purge) and reinstall it using the [HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095") tutorial by FakeOutdoorsman

The Ubuntu repositories seem to leave out some parts of ffmpeg

Also the group at ffmpeg have split or moved to another group called Libav ?

If you have a previuos version of DvDStyler currently on your system, that may cause problems as well

DvDStyler 1.8.4b is now available too

to be continued....

---

### Post by karel_novotny on 2011-05-06
Any luck? If so, would you share the newly created deb?

Thanks!

---

### Post by mocha on 2011-05-07
I haven't had any luck.  There is a thread on the dvdstyler sourceforge forum about this issue.  For some reason wxsvg refuses to compile with one of the header files for ffmpeg even if it exists, then dvdstyler's config script bombs out when it sees that wxsvg does not have ffmpeg support.

---

