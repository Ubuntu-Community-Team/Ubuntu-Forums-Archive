---
title: "Compiling Fuppes on Ubuntu 9.04 (Jaunty)"
date: 2009-05-12
forum: Multimedia Software
---

### Post by rizman on 2009-05-12
Hi all,

This is my first post here. I switched to Linux (Ubuntu 9.04) about a week ago and thus am pretty new to linux.

One thing I absolutely wanted to get to work was streaming my media to the Xbox 360. Finally, after multiple attempts at uShare (which worked, but I didn't get a folder structure to display. 1000's of MP3's in one list is not much fun)

Then I tried Fuppes but couldn't get it to compile because of all the dependencies required. Finally, I found in google a link to a forum entry on Fuppes's main page. Sadly, the forum is currently closed down. Luckily for me, google had the page cached.

So for future references, I thought it would be nice to have this guide on a more secure place where others can find it more easily then through google's cache until the other forums re-open.

So here it is. Thanks goes to **nullack **for posting this solution. 

First, get all the required packages
```

sudo apt-get install build-essential subversion autoconf automake gettext libtool libpcre3-dev libxml2-dev libsqlite3-dev libfaad-dev libmad0-dev libflac-dev libmagick++-dev libvorbis-dev libtwolame-dev libmpcdec-dev uuid-dev libavformat-dev libavutil-dev libavcodec-dev libmpeg4ip-dev libmp4v2-dev libtag1-dev libexpat1-dev

```Then, get the sources, configure, and make
```

svn co [https://**fuppes**.svn.sourceforge.net/svnroot/**fuppes**/trunk]("https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk") **fuppes**
cd **fuppes**/
autoreconf -vfi
./configure --prefix=/usr
make
sudo make install

```I finally got it compiling. The version I retrieved from the svn repo was 636.

Finally, you will need to configure fuppes to talk to the XBOX 360. Look in google, there are lots of threads out there who tell you how to configure the fuppes.cfg and vfolders.cfg files.

I just wanted to post the apt-get command as I coudln't find it elsewhere for Jaunty.

Hope this is helpful.

---

### Post by linuxvacuum on 2009-05-12
Thank you so much rizman! I tried compiling it months ago but there was always one more dependency required. And now it's installed!

---

### Post by littlegreiger on 2009-05-13
Anyone know any way to get this to compile on 64 bit?

---

### Post by rizman on 2009-05-13
> **linuxvacuum said:**
> Thank you so much rizman! I tried compiling it months ago but there was always one more dependency required. And now it's installed!

You're welcome. 
I had the very same problem. I almost gave up on it. And this was one very important point for me to stick with ubuntu after having switched from XP. Luckily, the original post was still cached in google :-)

@littlegreiger: Sorry, I don't have a 64bit machine. And anyway, as I said, I'm pretty new to Linux, so I wouldn't be of any help here anyway. Unfortunately, I don't recall seeing anything about compiling fuppes on Jaunty 64bit while googling around to get this thing to compile. But don't despear, Jaunty is quite new. Certainly someone will get a working compile done one day.

---

### Post by littlegreiger on 2009-05-13
thanks rizman, I'm sure I'll eventually find something

---

### Post by twisted_steel on 2009-05-14
> **littlegreiger said:**
> Anyone know any way to get this to compile on 64 bit?

I just compiled this on 64-bit Jaunty.  The only thing I did differently from the above steps was enable mp3 decoding and transcoding support:

```
./configure --enable-lame --enable-twolame --enable-mad --prefix=/usr
```

I'm not sure if I needed twolame or not, but it can't hurt.  I did need some extra dependencies installed: libmad0, libmad0-dev, libmp3lame0, libmp3lame-dev, libtwolame0, libtwolame-dev.  I haven't actually tried the software yet - just compiled it.

---

### Post by littlegreiger on 2009-05-16
Well I got it compiled, unfortunately I can't get video transcoding to work.
I did compile it with the option and do have ffmpeg installed, but the only way I could it to compile was to use the ffmpeg out of the repos, not the newest one from source.

---

### Post by kob0724 on 2009-05-16
Nice job man. That's pretty good stuff for a newby. Do you have previous experience with autotools or something?

---

### Post by pwoodhouse2000 on 2009-05-18
so I'm a complete newcomer, although I was a bit of a unix-head in a previous life. First - thanks to the initial poster - I lost many hours of sleep trying to get fuppes to compile, and there was always one more library. It's up and running now on my 9.04 64bit server, and my Yamaha receiver can actually see the data...but I can't for the life of me get taglib enabled. I've tried ./configure --enable-taglib

anyone out there done this?

---

### Post by il-luzhin on 2009-05-20
Can anyone suggests why I may have broken dependencies?

```

luzhin@kerenin:~$ sudo apt-get install build-essential subversion autoconf automake gettext libtool libpcre3-dev libxml2-dev libsqlite3-dev libfaad-dev libmad0-dev libflac-dev libmagick++-dev libvorbis-dev libtwolame-dev libmpcdec-dev uuid-dev libavformat-dev libavutil-dev libavcodec-dev libmpeg4ip-dev libmp4v2-dev libtag1-dev libexpat1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
subversion is already the newest version.
autoconf is already the newest version.
automake is already the newest version.
gettext is already the newest version.
libtool is already the newest version.
libpcre3-dev is already the newest version.
libxml2-dev is already the newest version.
libsqlite3-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libavutil-dev: Depends: libavutil49 (= 3:0.svn20090303-1ubuntu6) but it is not going to be installed
E: Broken packages
luzhin@kerenin:~$

```

Thanks

---

### Post by SDNick484 on 2009-05-21
> **pwoodhouse2000 said:**
> so I'm a complete newcomer, although I was a bit of a unix-head in a previous life. First - thanks to the initial poster - I lost many hours of sleep trying to get fuppes to compile, and there was always one more library. It's up and running now on my 9.04 64bit server, and my Yamaha receiver can actually see the data...but I can't for the life of me get taglib enabled. I've tried ./configure --enable-taglib

anyone out there done this?

You need to enable two-lame (--enable-twolame). FYI --enable-taglib isn't an option (check with ./configure --help), but it wasn't really clear two-lame would do it either, so don't feel bad about asking.

To get all features enabled I added "libsimage-dev libfaad-dev libexiv2-dev" to the list of things to install (also included twisted_steels suggested packages).  I configured with the following line:
./configure --enable-lame --enable-twolame --enable-mad --enable-faad --prefix=/us

This is on an x86_64 Jaunty box.  There's a launcher script I've used in the past on Fedora and Gentoo [here]("http://www.gentoo-wiki.info/Fuppes"), should work fine in Ubuntu.

---

### Post by twisted_steel on 2009-05-21
I should add that my build did end up working for transcoding FLAC files to mp3 for my Xbox 360.  The hard parts were figuring out the configs and not realizing that the web interface doesn't report correct information for compiled-in options.

---

### Post by twisted_steel on 2009-05-21
> **il-luzhin said:**
> Can anyone suggests why I may have broken dependencies?

...

Thanks

I'm not sure.  Did you try the fix broken packages option in Synaptic (under the Edit menu)?

---

### Post by PorchSong on 2009-05-25
> **il-luzhin said:**
> Can anyone suggests why I may have broken dependencies?

```

luzhin@kerenin:~$ sudo apt-get install build-essential subversion autoconf automake gettext libtool libpcre3-dev libxml2-dev libsqlite3-dev libfaad-dev libmad0-dev libflac-dev libmagick++-dev libvorbis-dev libtwolame-dev libmpcdec-dev uuid-dev libavformat-dev libavutil-dev libavcodec-dev libmpeg4ip-dev libmp4v2-dev libtag1-dev libexpat1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
subversion is already the newest version.
autoconf is already the newest version.
automake is already the newest version.
gettext is already the newest version.
libtool is already the newest version.
libpcre3-dev is already the newest version.
libxml2-dev is already the newest version.
libsqlite3-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libavutil-dev: Depends: libavutil49 (= 3:0.svn20090303-1ubuntu6) but it is not going to be installed
E: Broken packages
luzhin@kerenin:~$

```

Thanks

Well, I had exactly the same problem but was able to solve it after messing with it for a very long time.  I believe my problem was caused after following the directions on the thread "Install and use the latest FFmpeg and x264".  Somehow this breaks the fuppes install.  Also I was getting segmentation faults as well.

Here was my solution:


1.  If you did go through the process of 'Install and use the latest FFmpeg and x264' then go back to thread and use the purge command and then delete the ffmpeg and x264 folders.

2.  Install libavutil49 -- $sudo apt-get install libavutil49

This will give you the notice that you are about to remove a lot of other programs.  On my system it removed 23 other programs (DVD::RIP, and others).  Fuppes is very important to me, so I let them go.  If you want a list of what you are about to lose, then use '$sudo apt-get -s install libavutil49' to simulate.

Now, go back to my thread:

[http://ubuntuforums.org/showthread.php?t=984325]("http://ubuntuforums.org/showthread.php?t=984325")

And follow the instructions.  I tried other peoples ./configure with the  "prefix" rule and was getting segmentation faults, but when I followed the guide above, exactly, it worked and all is good again.

Anyway, give it a go and let us know.

---

### Post by strips on 2009-05-25
I have compiled SVN fuppes and enabled all options in ./configure without errors in compile. I can even see the flac libs beeing used in the compile output. but "i" in console says flac: disabled.

I have tried several fuppes.cfg files around but the same result, I can play MP3 files but not FLAC. The config seems to have enabled transcoding on FLAC.

Does anyone have a working config file for Playstation3 and FLAC transcoding?

Regards
Stian

---

### Post by rob4 on 2009-05-29
Hi All, 

Did a Fresh install of Jaunty
Followed [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) for ffmpeg 

Then followed this thread. I got the following error on make:

ffmpeg/ffmpeg.h:1400: warning: ‘AVFormatContext* av_alloc_format_context()’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:787)
make[1]: *** [libtranscoder_ffmpeg_la-transcoder_ffmpeg.lo] Error 1
make[1]: Leaving directory `/home/rob/fuppes/src/plugins'
make: *** [all-recursive] Error 1

Any help is greatly appreciated!

Rob

---

### Post by arc2v on 2009-05-30
Just wanted to say thanks for this.  I followed it almost exactly and it seems to be working on my test server (laptop) right now.

I think I manually added some other dependencies, but I'm not sure if they were necessary.

Still trying to get image resizing to work for jpgs, but for music, I'm happy.

Every once in a while I get an audio dropout on the Xbox, to which it never recovers.  But a quick back and restart usually works for the song.  Might be a wireless ethernet thing.  Lose the wrong packet at the wrong time and the client goes wonky.

But again, thanks for writing this up -- I couldn't have gotten this far without it.

---

### Post by PorchSong on 2009-06-01
> **rob4 said:**
> Hi All, 

Did a Fresh install of Jaunty
Followed [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) for ffmpeg 

Then followed this thread. I got the following error on make:

ffmpeg/ffmpeg.h:1400: warning: ‘AVFormatContext* av_alloc_format_context()’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:787)
make[1]: *** [libtranscoder_ffmpeg_la-transcoder_ffmpeg.lo] Error 1
make[1]: Leaving directory `/home/rob/fuppes/src/plugins'
make: *** [all-recursive] Error 1

Any help is greatly appreciated!

Rob

Go back to that thread and PURGE the install and delete the folders.  That thread breaks the fuppes install.  Purge it then install fuppes then go back and install it again.

I ran into exact problem.  That was how I solved it.

---

### Post by twisted_steel on 2009-06-03
> **strips said:**
> I have compiled SVN fuppes and enabled all options in ./configure without errors in compile. I can even see the flac libs beeing used in the compile output. but "i" in console says flac: disabled.

I have tried several fuppes.cfg files around but the same result, I can play MP3 files but not FLAC. The config seems to have enabled transcoding on FLAC.

Does anyone have a working config file for Playstation3 and FLAC transcoding?

Regards
Stian

I don't have a PS3, but do have FLAC -> MP3 transcoding working on my 360.  Interestingly enough, if I look at the info (via 'i') in the console, it also tells me FLAC is disabled.  I've attached my configs in case they can be of any use to you.  I had to add in ".txt" at the end of the filenames to actually get the forum software to let me attach them.

---

### Post by strips on 2009-06-08
> **twisted_steel said:**
> I don't have a PS3, but do have FLAC -> MP3 transcoding working on my 360.  Interestingly enough, if I look at the info (via 'i') in the console, it also tells me FLAC is disabled.  I've attached my configs in case they can be of any use to you.  I had to add in ".txt" at the end of the filenames to actually get the forum software to let me attach them.

Thanks, but I got the same results. I believe FLAC is not working properly even though I get the following when starting fuppes.

== lib/Plugins/Plugin.cpp (145) :: Mon Jun  8 22:44:12 2009 ==
registered audio decoder plugin "FLAC"

---

### Post by linuxvacuum on 2009-07-27
Yes rizman, thanks to your dependencies I got it compiled! I found an old deb for version 576. A fuppes repository would be nice.

---

### Post by jback2 on 2009-08-31
Sorry, I have a problem. I don't have autoreconf in my Jaunty. And I cannot find a package with this name. Do you have an idea?

---

### Post by meganox on 2009-08-31
I can't install the packages libavcodec-dev and libavutil-dev:

```
The following packages have unmet dependencies.
  libavcodec-dev: Depends: libavcodec52 (= 3:0.svn20090303-1ubuntu6) but it is not going to be installed
  libavutil-dev: Depends: libavutil49 (= 3:0.svn20090303-1ubuntu6) but it is not going to be installed

```

installing these dependencies would remove ffmpeg and some other packages which depend on it.  I'm using the Jaunty repos version of ffmpeg.

Any ideas?

---

### Post by meganox on 2009-08-31
> **jback2 said:**
> Sorry, I have a problem. I don't have autoreconf in my Jaunty. And I cannot find a package with this name. Do you have an idea?

```
$ sudo apt-get install build-essential autoconf automake gettext libtool
```

---

### Post by Rocketeer on 2009-09-05
> **il-luzhin said:**
> Can anyone suggests why I may have broken dependencies?

```

luzhin@kerenin:~$ sudo apt-get install build-essential subversion autoconf automake gettext libtool libpcre3-dev libxml2-dev libsqlite3-dev libfaad-dev libmad0-dev libflac-dev libmagick++-dev libvorbis-dev libtwolame-dev libmpcdec-dev uuid-dev libavformat-dev libavutil-dev libavcodec-dev libmpeg4ip-dev libmp4v2-dev libtag1-dev libexpat1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
subversion is already the newest version.
autoconf is already the newest version.
automake is already the newest version.
gettext is already the newest version.
libtool is already the newest version.
libpcre3-dev is already the newest version.
libxml2-dev is already the newest version.
libsqlite3-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libavutil-dev: Depends: libavutil49 (= 3:0.svn20090303-1ubuntu6) but it is not going to be installed
E: Broken packages
luzhin@kerenin:~$

```

Thanks

Actually I have the same problem (libavutil49), but I will not install it while getting a lot of other packages removed. Is there an other solution, as it seems fuppes is the best DLNA service out there for Ubuntu.

---

### Post by Rocketeer on 2009-09-05
(deleted - missinformation)

---

### Post by Rocketeer on 2009-09-05
Okay, I got it compiling even without the libavutil49! It seems to be some (for me) complex bug in the current ffmpeg build:
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/312898](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/312898)

However, you can install libavutil-**unstripped**-49 to make it work. 

```
sudo apt-get install libavutil-unstripped-49
```

After that, just follow the guide and it should work out fine.

---

### Post by enyoj on 2009-09-08
Rocketeer, can you further explain how you got this working please? I encounter the exact same problem.

I installed the unstripped version, but what do I do next? The apt-get install command in the OP doesn't work since it depends on the unstripped version. I read the bug report you reffered to, but I can't seem to figure out a workaround. It says this bug will be fixed in Ubuntu Karmic, but what to do till then?

---

### Post by kogger on 2009-09-12
I'm having a slightly different problem. The configure command seems to work fine, but here's my output for the autreconf -vfi and make commands:

autoreconf -vfi:
```
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.ac: not using Gettext
autoreconf2.50: running: aclocal --force -I m4
autoreconf2.50: configure.ac: tracing
autoreconf2.50: running: libtoolize --copy --force
You should update your `aclocal.m4' by running aclocal.
autoreconf2.50: running: /usr/bin/autoconf --force
autoreconf2.50: running: /usr/bin/autoheader --force
autoreconf2.50: running: automake --add-missing --copy --force-missing
autoreconf2.50: Leaving directory `.'
```

And make:
```
Making all in m4
make[1]: Entering directory `/home/damien/desktop/fuppes/m4'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/damien/desktop/fuppes/m4'
Making all in src
make[1]: Entering directory `/home/damien/desktop/fuppes/src'
if test -e "../version.sh"; then \
		../version.sh; \
	fi
make  all-am
make[2]: Entering directory `/home/damien/desktop/fuppes/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I.  -I/usr/include/uuid   -I/usr/include/libxml2   -I/usr/local/include   -DFUPPES_DATADIR=\"/usr/share/fuppes\" -DFUPPES_PLUGINDIR=\"/usr/lib/fuppes\"    -g -O2 -Wall -Wextra -MT UPnPAction.lo -MD -MP -MF .deps/UPnPAction.Tpo -c -o UPnPAction.lo `test -f 'lib/UPnPActions/UPnPAction.cpp' || echo './'`lib/UPnPActions/UPnPAction.cpp
../libtool: line 783: X--tag=CXX: command not found
../libtool: line 816: libtool: ignoring unknown tag : command not found
../libtool: line 783: X--mode=compile: command not found
../libtool: line 933: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 934: *** Future versions of Libtool will require -mode=MODE be specified.: command not found
../libtool: line 1077: Xg++: command not found
../libtool: line 1077: X-DHAVE_CONFIG_H: command not found
../libtool: line 1077: X-I.: command not found
../libtool: line 1077: X-I/usr/include/uuid: No such file or directory
../libtool: line 1077: X-I/usr/include/libxml2: No such file or directory
../libtool: line 1077: X-I/usr/local/include: No such file or directory
../libtool: line 1077: X-DFUPPES_DATADIR="/usr/share/fuppes": No such file or directory
../libtool: line 1077: X-DFUPPES_PLUGINDIR="/usr/lib/fuppes": No such file or directory
../libtool: line 1077: X-g: command not found
../libtool: line 1077: X-O2: command not found
../libtool: line 1077: X-Wall: command not found
../libtool: line 1077: X-Wextra: command not found
../libtool: line 1077: X-MT: command not found
../libtool: line 1077: XUPnPAction.lo: command not found
../libtool: line 1077: X-MD: command not found
../libtool: line 1077: X-MP: command not found
../libtool: line 1077: X-MF: command not found
../libtool: line 1077: X.deps/UPnPAction.Tpo: No such file or directory
../libtool: line 1077: X-c: command not found
../libtool: line 1125: XUPnPAction.lo: command not found
../libtool: line 1130: libtool: compile: cannot determine name of library object from `': command not found
make[2]: *** [UPnPAction.lo] Error 1
make[2]: Leaving directory `/home/damien/desktop/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/damien/desktop/fuppes/src'
make: *** [all-recursive] Error 1
```

I'm pretty sure I have all the dependencies, so why can't it find the required commands?

---

### Post by meganox on 2009-09-22
It says "You should update your `aclocal.m4' by running aclocal." directly after "autoreconf2.50: running: libtoolize --copy --force"

Since your make errors are all related to libtool, I suggest you do as it says.

---

### Post by Sp00nMan on 2009-09-24
I've installed all the libs and am running a make on jaunty 64-bit.. It crashes out with this error (using latest SVN)

lib/SharedConfig.cpp:41:24: error: ../version.h: No such file or directory
lib/SharedConfig.cpp:150:3: warning: #warning todo: system checks (e.g. XP firewall)
lib/SharedConfig.cpp:605:2: warning: #warning todo
lib/SharedConfig.cpp: In member function âstd::string CSharedConfig::GetAppVersion()â:
lib/SharedConfig.cpp:240: error: âFUPPES_VERSIONâ was not declared in this scope
make[2]: *** [SharedConfig.lo] Error 1
make[2]: Leaving directory `/home/tom/fuppes-0.640/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/tom/fuppes-0.640/src'
make: *** [all-recursive] Error 1

Guess I need to manually create a version.h?

EDIT: Guess I should have done that before post.  I created this file in the root folder and the compile completed

&#9492;&#9472;(14:14:%)&#9472;&#9472; more version.h                               
#define FUPPES_VERSION "0.SVN-549"

---

### Post by wweiland on 2009-09-24
[I]Sp00nMan,  I'm receiving the same error even after adding the version.h.  Were you able to complete the compile?

libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I/usr/include/uuid -I/usr/include/libxml2 -DFUPPES_DATADIR=\"/usr/share/fuppes\" -DFUPPES_PLUGINDIR=\"/usr/lib/fuppes\" -g -O2 -Wall -Wextra -DDEFAULT_HTTP_PORT=yes -MT SharedConfig.lo -MD -MP -MF .deps/SharedConfig.Tpo -c lib/SharedConfig.cpp  -fPIC -DPIC -o .libs/SharedConfig.o
lib/SharedConfig.cpp:150:3: warning: #warning todo: system checks (e.g. XP firewall)
lib/SharedConfig.cpp:612:2: warning: #warning todo
lib/SharedConfig.cpp: In constructor âCSharedConfig::CSharedConfig()â:
lib/SharedConfig.cpp:88: error: âyesâ was not declared in this scope
make[2]: *** [SharedConfig.lo] Error 1
make[2]: Leaving directory `/root/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/fuppes/src'
make: *** [all-recursive] Error 1


EDIT: Nevermind, it didn't like the --with-httpd-port option.

Compiled with ./configure --enable-lame --enable-mad --enable-twolame --prefix=/usr
[/I]

---

### Post by Rocketeer on 2009-09-26
> **enyoj said:**
> Rocketeer, can you further explain how you got this working please? I encounter the exact same problem.

I installed the unstripped version, but what do I do next? The apt-get install command in the OP doesn't work since it depends on the unstripped version. I read the bug report you reffered to, but I can't seem to figure out a workaround. It says this bug will be fixed in Ubuntu Karmic, but what to do till then?


Actually it was not working properly and I recieved a new server, so I started from scratch with a fresh Jaunty 64bit server install.
compiled like a charm. now i am just starting playing around.

---

### Post by kogger on 2009-10-13
> **meganox said:**
> It says "You should update your `aclocal.m4' by running aclocal." directly after "autoreconf2.50: running: libtoolize --copy --force"

Since your make errors are all related to libtool, I suggest you do as it says.

I did. It didn't work.

---

### Post by subkowlex on 2009-10-21
Hello everybody, after a night sitting in front of the screen I could comile and launch fuppes, but everytime I try to watch a video on my xbox 360, I get this:

> [NULL @ 0x901b9c0]Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from '/home/alexej/Videos/Test.avi':
  Duration: 00:42:41.12, start: 0.000000, bitrate: 1269 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Output #0, asf, to '/tmp/fuppes/0.wmv':
    Stream #0.0: Video: wmv2, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 1800 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: wmav1, 48000 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[asf @ 0x900fbf0]Aspect ratio mismatch between encoder and muxer layer
Could not write header for output file #0 (incorrect codec parameters ?)Does anybody have an idea where I can pimp a conf file to avoid this?

Thanks a lot for your replies.

Alex.

---

### Post by Shhnap on 2009-11-05
Just quickly, the version.h file in fuppes is autogenerated using version.sh. Just type in:

```
./version.sh
```

And you will be given a valid version.h file.

---

### Post by horse21 on 2009-11-10
I'm having some troubles with taglib as well. When I configure fuppes it says it is disabled, and when it says 'check optional stuff' it says:
checking for taglib-config... no

Yet the command taglib-config does exist. 

There is a --enable-taglib option for config (I type '--enable-tag' then hit tab, and it puts --enable-taglib). I have libtag1-dev installed. The other option under 'audio metadata extraction plugins' is disabled as well and I'm trying to enable it. I'm not sure about the dependencies of that option.

I thought that I had taglib saying enabled earlier (before I installed some more dependencies), I'm not sure why it changed. I haven't attempted it to see if it's just reporting incorrectly yet.

Anyone have an idea?

---

### Post by horse21 on 2009-11-11
Alright, I used the 
--prefix=/usr/
and it's showing properly as enabled now.

Thanks Shhnap!

---

