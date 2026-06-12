---
title: "Idjc?"
date: 2008-06-05
forum: Multimedia Software
---

### Post by Kidfork on 2008-06-05
HELLO fellow Ubuntu/Kubuntu/Watever. IM havign a couple problems with the Internet DJ Console. Its actualy quiet simple. WHen i put all my information into the "SERVER" screen on SHOUTcast the button wont light up "SERVER CONNECT" which means i cant stream. How can i resolve this problem?

THank You

Kidfork-

---

### Post by StephenF on 2008-06-06
> **Kidfork said:**
> HELLO fellow Ubuntu/Kubuntu/Watever. IM havign a couple problems with the Internet DJ Console. Its actualy quiet simple. WHen i put all my information into the "SERVER" screen on SHOUTcast the button wont light up "SERVER CONNECT" which means i cant stream. How can i resolve this problem?
You could use a different IDJC package from the official one which won't likely offer mp3 streaming support until the mp3 software patent expires in four years time or you could compile your own from source. IDJC does not support Ogg/vorbis streams to Shoutcast servers.

---

### Post by Kidfork on 2008-06-15
Where can i find this "Source"

---

### Post by StephenF on 2008-06-16
> **Kidfork said:**
> Where can i find this "Source"

Since you asked...

[http://sourceforge.net/projects/idjc/](http://sourceforge.net/projects/idjc/)

---

### Post by StephenF on 2008-06-16
**A detailed IDJC install guide with all features enabled.**

Step 0) Uninstall any IDJC packages that you may currently have installed. 

Step 1) Open a terminal window. It's under Applications->Accessories in the top left corner of the screen.

Step 2) Install necessary dependencies (copy and paste the following into the console window):
```

sudo apt-get install libc6-dev libjack-dev jackd libvorbis-dev libsamplerate0-dev libsndfile1-dev python-gtk2-dev libmad0-dev libavcodec-dev libavformat-dev libmp3lame-dev flac vorbis-tools python-mutagen libspeex-dev
```
If you are using a 64 bit Ubuntu add **libc6-dev-i386** to the list.

Step 3) Grab a copy of IDJC:
```

wget http://web.bethere.co.uk/idjc/download/idjc-0.8.1.tar.gz

```

Step 4) Extract it:
```

tar xzvf idjc-0.8.1.tar.gz

```

Step 5) Compile and install:
```

cd idjc-0.8.1
./configure CFLAGS="-O2"
make
sudo make install

```

Step 6) Post configuration:
```

echo "/usr/bin/jackd -d alsa -r 44100 -p 2048" > ~/.jackdrc

```

And that's it! IDJC appears in the Applications->Internet menu.

---

### Post by JvdS45 on 2009-02-02
not working for me I got this message below
Traceback (most recent call last):
  File "/usr/local/lib/python2.5/site-packages/idjcgui.py", line 86, in <module>
    from ln_text import ln
  File "/usr/local/lib/python2.5/site-packages/idjc/ln_text.py", line 106, in <module>
    ln = _set()
  File "/usr/local/lib/python2.5/site-packages/idjc/ln_text.py", line 103, in _set
    return getattr(gns, lev)()
  File "/usr/local/lib/python2.5/site-packages/idjc/ln_text.py", line 57, in __init__
    self._load_text(cls)
  File "/usr/local/lib/python2.5/site-packages/idjc/ln_text.py", line 39, in _load_text
    mod = __import__(modulename)
ImportError: No module named nl_NL_text

so what to do now?

thanks if you can help me

---

### Post by StephenF on 2009-02-02
Start IDJC like this:

LANG="en_GB" idjc

---

### Post by JvdS45 on 2009-02-13
thank u thats working

so soon i can broadcast here :)

---

### Post by HnKDKS on 2009-04-30
Hello everyone!
I just clean install unbuntu 8.10 64 bits on this pc and tried to re-install IDJC.

I have been coming up with this error all the time, I can't figure out what the problem. Any help would do.

Thanks!

~$ idjc
Internet DJ Console Version 0.7.14
Copyright 2005-2009 Stephen Fairchild
Released under the GNU General Public License V3.0

Language translation: en_US
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: cannot set period size to 2048 frames for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
something bad happened and IDJC could not continue

Hardware is:
Asus M3N-HD HDMI (Nforce 750a)
AMD X2 5400+
4 Gig Ram
9800GTX 512 ram

---

### Post by HnKDKS on 2009-05-01
Fixed it with this code:

```
echo "/usr/bin/jackd -d alsa -r 44100 -p 1024" > ~/.jackdrc
```

For some odd reason it doesn't want to run at -p 2048 but only at 1024.

Anyway it works now.

:guitar:

---

### Post by happinesskills on 2009-05-02
Hi. I just upgraded to Jaunty & now IDJC won't start. doesn't even give Jack error (if jack's off)

Here's the output from terminal:
```
matt@matt-laptop:~$ idjc
Compromise language match found en_GB
Internet DJ Console Version 0.7.7
Copyright 2005-2008 Stephen Fairchild
Released under the GNU General Public License V3.0

Language translation: en_GB
/usr/lib/python2.5/site-packages/idjcgui.py:1565: DeprecationWarning: os.popen2 is deprecated.  Use the subprocess module.
  self.mixer_ctrl, self.mixer_rply = os.popen2([ libexecdir + "idjcmixer" ], 4096)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 2360, in <module>
    run_instance = MainWindow()
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 1731, in __init__
    self.mic_select = nice_mic_togglebutton()
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 225, in __init__
    gtk.ToggleButton.__init__(self, label, use_underline)
RuntimeError: more argument specifiers than keyword list entries (remaining format:'):GtkToggleButton.__init__')
matt@matt-laptop:~$ Mixer module has closed
```

---

### Post by bobince on 2009-05-02
Yeah, forget jaunty's idjc package: it's outdated, buggy and compiled without MP3 support (due to the surrounding legal quagmire). See StephenF's post on the previous page of this thread on compiling your own; it's not too tricky.

(Although I'd go with 0.7.13 rather than 14 until the listener numbers bug is fixed.)

---

### Post by rickyprose on 2009-08-17
Hi Guys,

I would like to use my eeepc with ubuntu 9.04 to made a webradio.
After the command ./configure CFLAGS="-02"
I have this error:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for JACK... configure: error: Package requirements (jack >= 0.98.0) were not met:

No package 'jack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables JACK_CFLAGS
and JACK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Someone can help me?
PS I already installed Jack

Thanks :guitar:

The Crazy

---

### Post by StephenF on 2009-08-18
> **rickyprose said:**
> Hi Guys,

I would like to use my eeepc with ubuntu 9.04 to made a webradio.
After the command ./configure CFLAGS="-02"
I have this error:

See post number 5 in this thread.

---

### Post by Hybodus on 2009-09-03
Has anyone managed to get the announce to work in xchat, I've got idjc installed and works brilliantly. Copied the idjc-announce.py to the .xchat2 folder and it does load when xchat starts.
 using the command /announce says idjc announce already started but nothing happens when I stream music. if I use /listening i get an announcement of the current playing track but would like it to announce each track as they play.

would be grateful for any ideas on how to get this working, ta

Nevermind, found out it only works when connected to a server, problem solved :)

Hybodus

---

### Post by draldo on 2009-10-05
Hey all,

   I followed the directions but ran into this : 


Making all in c
make[2]: Entering directory `/home/user/idjc-0.7.17/c'
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -std=gnu99 -O2    -I/usr/include/FLAC     -I/usr/include/ffmpeg   -I/usr/include/ffmpeg    -O2 -MT idjcmixer-idjcmixer.o -MD -MP -MF ".deps/idjcmixer-idjcmixer.Tpo" -c -o idjcmixer-idjcmixer.o `test -f 'idjcmixer.c' || echo './'`idjcmixer.c; \
	then mv -f ".deps/idjcmixer-idjcmixer.Tpo" ".deps/idjcmixer-idjcmixer.Po"; else rm -f ".deps/idjcmixer-idjcmixer.Tpo"; exit 1; fi
In file included from idjcmixer.c:46:
avcodecdecode.h:25:32: error: libavcodec/avcodec.h: No such file or directory
avcodecdecode.h:26:34: error: libavformat/avformat.h: No such file or directory
In file included from idjcmixer.c:46:
avcodecdecode.h:32: error: expected specifier-qualifier-list before &#8216;AVCodec&#8217;
make[2]: *** [idjcmixer-idjcmixer.o] Error 1
make[2]: Leaving directory `/home/user/idjc-0.7.17/c'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/idjc-0.7.17'
make: *** [all] Error 2


So basically it configured ok but can't find libavcodec and libavformat which presumably are not where idjc is looking for them. How would I go about fixing this? Or telling idjc to build with libavcodec and -format in the right places?

Any help is greatly appreciated.



SOLVED : I started looking at other options and although it might not be the desired one for now (let me know it what I did was wrong) what seemed to work was removing and replacing both libavcodec-dev and libavformat-dev with they equivalent libavcodec-unstripped-51 and libformat-unstripped-52 which seemed to take care of the problem.

I hope that may help others shoud they encounter the same.

---

### Post by bbabiuk on 2009-10-18
> **StephenF said:**
> **A detailed IDJC install guide with all features enabled.**

Step 0) Uninstall any IDJC packages that you may currently have installed. 

Step 1) Open a terminal window. It's under Applications->Accessories in the top left corner of the screen.

Step 2) Install necessary dependencies (copy and paste the following into the console window):
```

sudo apt-get install libc6-dev libjack-dev jackd libvorbis-dev libsamplerate0-dev libsndfile1-dev python-gtk2-dev libmad0-dev libavcodec-dev libavformat-dev libmp3lame-dev libmp4v2-dev flac vorbis-tools python-eyed3 libspeex-dev
```If you are using a 64 bit Ubuntu add **libc6-dev-i386** to the list.

Step 3) Grab a copy of IDJC:
```

wget http://web.bethere.co.uk/idjc/download/idjc-0.7.16.tar.gz

```Step 4) Extract it:
```

tar xzvf idjc-0.7.16.tar.gz

```Step 5) Compile and install:
```

cd idjc-0.7.16
./configure CFLAGS="-O2"
make
sudo make install

```Step 6) Post configuration:
```

echo "/usr/bin/jackd -d alsa -r 44100 -p 2048" > ~/.jackdrc

```And that's it! IDJC appears in the Applications->Internet menu.


Ok.. I followed this.. and it still complains about connecting to JACK.  I tried rerunning the last statement... even with sudo in front.  But it seems (and I'm guessing) that Pulseaudio and Jack dont play nice together.  Any ideas?

---

### Post by roquet on 2009-11-14
=D>=D>=D>Thank you very much.

---

### Post by jamorod on 2010-02-11
Hi there,

I would like to know which is the latest version available for Ubuntu?

I've tried the 8.1 version, but it doesn't want to work with Ubuntu, it keeps giving the LIBJACK error problem.

I tried downloading the version 7.14 from the link [http://web.bethere.co.uk/idjc/download/idjc-0.7.15_pre1.tar.gz](http://web.bethere.co.uk/idjc/download/idjc-0.7.15_pre1.tar.gz) but it is not available any longer. Where can I find it?

---

### Post by jamorod on 2010-02-11
It seems that I've found it... from here: [http://packages.ubuntu.com/karmic/x11/idjc](http://packages.ubuntu.com/karmic/x11/idjc) 

I hope this is the right one!

---

### Post by jamorod on 2010-02-11
Oh, no! This is for Karmic and I have Jaunty! Too late.. already installing, let's see what happens.

---

