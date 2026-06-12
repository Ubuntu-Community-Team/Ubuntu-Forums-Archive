---
title: "Struggling to find a way to use my ipod with Ubuntu"
date: 2012-07-19
forum: Multimedia Software
---

### Post by Potsoil on 2012-07-19
I'm currently trying to find a way to use my Ipod classic with Ubuntu..I'm using Ubuntu 12.04. I've tried using Rhythmbox Music Player, Banshee and Gtkpod Ipod Manager (all latest versions I think) to sync my ipod. All appear to sync successfully, with the music library appearing when you click on the device in each of the programs (Banshee appeared to duplicate every song, which Gtkpod then removed), but the music library never shows up on the Ipod. I've also tried using Wine (1.4) and several versions of Itunes, but all either failed to detect the device or kept freezing. I know there's a lot about this on the internet but as there doesn't seem to be any clear solution and most of the posts I found were from 2010, I thought I'd ask if anyone has any advice as I'm at a bit of a loose end..

---

### Post by ron999 on 2012-07-19
> **Potsoil said:**
> ... Gtkpod Ipod Manager (all latest versions I think) to sync my ipod...
Hi
**gtkpod** in 12.04 repository is broken. :(
Solution is to compile gtkpod from git. :D

It's not difficult to do this.
Takes about 20 minutes.
I've still got the commands if you're interested. ;)

---

### Post by Potsoil on 2012-07-19
> **ron999 said:**
> Hi
**gtkpod** in 12.04 repository is broken. :(
Solution is to compile gtkpod from git. :D

It's not difficult to do this.
Takes about 20 minutes.
I've still got the commands if you're interested. ;)

I'm not completely sure what that means but if it might work that'd be great!

---

### Post by ron999 on 2012-07-19
This is the method I used to compile and install gtkpod from git with Xubuntu-12.04
Takes approx 20 minutes.
Just two _single_ commands to copy and paste into terminal.

1 Preparation:-

```
sudo apt-get update && \
sudo apt-get -y remove gtkpod gtkpod-* && \
sudo apt-get -y build-dep gtkpod && \
sudo apt-get -y install checkinstall git \
gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```


2 Download, compile and install:-

```
cd ~/ && \
git clone --depth 1 git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod && \
cd gtkpod && ./autogen.sh && make && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname gtkpod \
--pkgversion "2.1.3+git$(date +%Y%m%d)" \
--backup=no --default --deldoc=yes --fstrans=no && \
sudo ldconfig
```

When it's finished...
The **.deb** file on 'Desktop' is yours to keep.
The **gtkpod** folder in 'Home' can be deleted.

The gtpod git shortlog is here ---> [http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/gtkpod;a=shortlog]("http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/gtkpod;a=shortlog")

---

### Post by Potsoil on 2012-07-19
> **ron999 said:**
> This is the method I used to compile and install gtkpod from git with Xubuntu-12.04
Takes approx 20 minutes.
Just two _single_ commands to copy and paste into terminal.

1 Preparation:-

```
sudo apt-get update && \
sudo apt-get -y remove gtkpod gtkpod-* && \
sudo apt-get -y build-dep gtkpod && \
sudo apt-get -y install checkinstall git \
gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```
2 Download, compile and install:-

```
cd ~/ && \
git clone --depth 1 git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod && \
cd gtkpod && ./autogen.sh && make && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname gtkpod \
--pkgversion "2.1.3+git$(date +%Y%m%d)" \
--backup=no --default --deldoc=yes --fstrans=no && \
sudo ldconfig
```When it's finished...
The **.deb** file on 'Desktop' is yours to keep.
The **gtkpod** folder in 'Home' can be deleted.

The gtpod git shortlog is here ---> [http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/gtkpod;a=shortlog](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/gtkpod;a=shortlog)

Sorry to be naive about this...but after it's installed do I just run the program and my ipod should sync? Or do I need to do something with the .deb file?

---

### Post by ron999 on 2012-07-19
> **Potsoil said:**
> ... Or do I need to do something with the .deb file?
The .deb file is only saved for if you need to re-install gtkpod again later.

---

### Post by djtarki on 2012-07-29
> **ron999 said:**
> This is the method I used to compile and install gtkpod from git with Xubuntu-12.04
Takes approx 20 minutes.
Just two _single_ commands to copy and paste into terminal.

1 Preparation:-

```
sudo apt-get update && \
sudo apt-get -y remove gtkpod gtkpod-* && \
sudo apt-get -y build-dep gtkpod && \
sudo apt-get -y install checkinstall git \
gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```2 Download, compile and install:-

```
cd ~/ && \
git clone --depth 1 git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod && \
cd gtkpod && ./autogen.sh && make && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname gtkpod \
--pkgversion "2.1.3+git$(date +%Y%m%d)" \
--backup=no --default --deldoc=yes --fstrans=no && \
sudo ldconfig
```When it's finished...
The **.deb** file on 'Desktop' is yours to keep.
The **gtkpod** folder in 'Home' can be deleted.

The gtpod git shortlog is here ---> [http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/gtkpod;a=shortlog](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/gtkpod;a=shortlog)


Sadly, I always get 

```
checking for faad... no
configure: WARNING: "Cannot find faad. Conversion from m4a to mp3 not possible"
checking if sjcd plugin is disabled... ./configure: line 19284: syntax error near unexpected token `vorbisenc,,{'
./configure: line 19284: `                        AM_GST_ELEMENT_CHECK(vorbisenc,,{ $as_echo "$as_me:${as_lineno-$LINENO}: WARNING: The 'vorbisenc' element was not found. This will cause encoding to Ogg Vorbis to fail." >&5'

```I am using Ubuntu 12.04 64, any idea please?

Thank you.

Best regards

[COLOR=Green]**SOLVED!: after installing the following packages:  libfaad-ocaml-dev, libfaad-dev, libgstreamer0.10-dev**[/COLOR], libgstreamer-plugins-base0.10-dev and faad (others might be needed depending on what is already installed on your distribution)

---

### Post by ron999 on 2012-07-30
> **djtarki said:**
> Sadly, I always get 

```
checking for faad... no
configure: WARNING: "Cannot find faad. Conversion from m4a to mp3 not possible"
checking if sjcd plugin is disabled... ./configure: line 19284: syntax error near unexpected token `vorbisenc,,{'
./configure: line 19284: `                        AM_GST_ELEMENT_CHECK(vorbisenc,,{ $as_echo "$as_me:${as_lineno-$LINENO}: WARNING: The 'vorbisenc' element was not found. This will cause encoding to Ogg Vorbis to fail." >&5'

```I am using Ubuntu 12.04 64, any idea please?

Thank you.

Best regards

[COLOR=Green]**SOLVED!: after installing the following packages:  libfaad-ocaml-dev, libfaad-dev, libgstreamer0.10-dev**[/COLOR], libgstreamer-plugins-base0.10-dev and faad (others might be needed depending on what is already installed on your distribution)

Thanks for the feedback. :)

---

### Post by keishia.tee on 2012-08-06
Hi, thanks for the thread. I've followed all the steps but I'm still having problems.

I'm trying to transfer my music *from* my ipod classic to Ubuntu 12.04. I can move files *to* the ipod using Banshee no problem, but I'm having problems with gtkpod. 

I can see the track info on my ipod, but if I try and drag anything to my music library it crashes. Sometimes it will stay open if I only move one track, but mostly it crashes straight away. Most of the time it will transfer one track, even if it does crash. Any ideas?? 

Also, it displays this message every time I open gtkpod:

```
iTunesDB '/media/IPOD/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/IPOD/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using SHA1 checksums. This may take a long time.

```

Mostly it does find a matching checksum (or whatever it is it's doing!) but not always... Is this normal?

Thanks for your input!

---

### Post by kai12 on 2012-10-06
Hey hey, 

I'm having gtkpod trouble in kubuntu 12.04, 
so I followed the above procedure and compiled from the git sources.

But something apparently went wrong, upon startup, gtkpod reports messages like:

Could not load Photo Editor Plugin
This usually means that your installation is corrupted. The error message leading to this was:
Unable to find plugin module /usr/local/lib/gtkpod/libphoto_editor.so

in a long series of pop-up windows. 
Afterwards, the only entry in the "Music" menu is "Quit".

I checked the output in the terminal window where I build gtkpod for "error" and "failed" and found a bunch of messages reading

ln: failed to create symbolic link `../libfiletype_flac.so': File exists

which sounds just like the reason for the above -- but what exactly went wrong and how I can fix this I don't know.

Can anybody help me out here?
kai

---

### Post by motorcity909 on 2012-10-06
This may not be the solution you are looking for but I hope you don't mind me contributing.

I had a lot of trouble using my iPod when I first moved to Ubuntu over three years ago.  Between them Banshee and Rhythmbox wiped all my covers or wiped all my songs.  This was three years ago so they may be better now.

Since then I've been using Virtualbox with Windows XP and iTunes.

This is the only thing I have to go to XP for.  I absolutely hate iTunes but use it solely to manage my iPod.

Cheers
Dave

---

### Post by kai12 on 2012-10-09
Thanks Dave, this might work for many. 

I didn't have any trouble with gtkpod and my iPod nano in the past though (the "past" being a 10.04 ubuntu system). It even played nice with occasionally getting a file or two from iTunes at a friends place.

And I just don't own a windows license.  So VirtualBox/VMware won't do...

kai

---

### Post by ron999 on 2012-10-11
> **kai12 said:**
> Hey hey, 

I'm having gtkpod trouble in kubuntu 12.04, 
so I followed the above procedure and compiled from the git sources.

But something apparently went wrong
Hi
I've just compiled gtkpod from git again.
It's working OK.
Version is 2.1.3-2067905
System is Xubuntu-12.04

---

### Post by awulll on 2012-10-17
Sorry for the newbie question.
I follow all the instructions but when I type gtkpod in terminal I get:

bash: /usr/bin/gtkpod: Arquivo ou diretório não encontrado

I need use any diferent path to run?

---

### Post by awulll on 2012-10-17
It was in other directory, I found it, thanks!

---

### Post by PDA1 on 2012-11-21
I tried to install Gtkpod using using the 2 aforementioned commands. 

What do I do next? 

Please be exact as I have no idea really how to do those "make" "install" etc commands or other fancy sort of stuff.

---

### Post by noSelf on 2013-01-30
Thanks so much for the easy scripts! i'd been wanting to update GTKPod for over a year (when i was still on 10.10). After upgrading to 12.04.1 (64-bit) i was dismayed to read of teh troubles with the version in the Ubuntu repos. This is a great relief, there are few software programs that annoy me as much as iTunes.

---

### Post by smorgado on 2013-03-01
I compiled and installed gtkpod from git but I think some libraries
get missplaced, when I run /usr/local/bin/gtkpod does not find
libgtkpod.so.1

---

### Post by toodh on 2013-03-23
Hi 

I followed your steps, but had lots of tweaking to do, maybe because it's a Kubuntu-based distro in 64bit. After 3 hrs I think I have nearly made it, but can't figure out my last problem. Below you find the terminal output before the script / your command sequence aborts. It seem that .libs/libgtkpod.lai cannot be found, and indeed if I check the folder ~/gtkpod/libgtkpod/.libs, the only the files libgtkpod.so and .a are there, but not .lai. Any suggestions would be very welcome,  I am quite frustrated after 3hrs of work...

```

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@Moria ]
1 -  Summary: [ Package created with checkinstall 1.6.2 ]
2 -  Name:    [ gtkpod ]
3 -  Version: [ 2.1.3+git20130323 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ gtkpod ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ gtkpod ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in libgtkpod
make[1]: Entering directory `/home/isildur/gtkpod/libgtkpod'
make[2]: Entering directory `/home/isildur/gtkpod/libgtkpod'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libgtkpod.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libgtkpod.so.1.1.0 /usr/local/lib/libgtkpod.so.1.1.0
libtool: install: (cd /usr/local/lib && { ln -s -f libgtkpod.so.1.1.0 libgtkpod.so.1 || { rm -f libgtkpod.so.1 && ln -s libgtkpod.so.1.1.0 libgtkpod.so.1; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libgtkpod.so.1.1.0 libgtkpod.so || { rm -f libgtkpod.so && ln -s libgtkpod.so.1.1.0 libgtkpod.so; }; })
libtool: install: /usr/bin/install -c .libs/libgtkpod.lai /usr/local/lib/libgtkpod.la
/usr/bin/install: cannot stat `.libs/libgtkpod.lai': No such file or directory
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/isildur/gtkpod/libgtkpod'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/isildur/gtkpod/libgtkpod'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```


Thanks,

Daniel

---

### Post by ron999 on 2013-03-23
Hi
I've just compiled gtkpod from git again.
It's working OK.
Version is 2.1.3-665fe09
System is Xubuntu-12.04 (32-bit)

```
*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@xubuntu ]
1 -  Summary: [ Package created with checkinstall 1.6.2 ]
2 -  Name:    [ gtkpod ]
3 -  Version: [ 2.1.3+git20130323 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gtkpod ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ gtkpod ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in libgtkpod
make[1]: Entering directory `/home/ron/gtkpod/libgtkpod'
make[2]: Entering directory `/home/ron/gtkpod/libgtkpod'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libgtkpod.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libgtkpod.so.1.1.0 /usr/local/lib/libgtkpod.so.1.1.0
libtool: install: (cd /usr/local/lib && { ln -s -f libgtkpod.so.1.1.0 libgtkpod.so.1 || { rm -f libgtkpod.so.1 && ln -s libgtkpod.so.1.1.0 libgtkpod.so.1; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libgtkpod.so.1.1.0 libgtkpod.so || { rm -f libgtkpod.so && ln -s libgtkpod.so.1.1.0 libgtkpod.so; }; })
libtool: install: /usr/bin/install -c .libs/libgtkpod.lai /usr/local/lib/libgtkpod.la
libtool: install: /usr/bin/install -c .libs/libgtkpod.a /usr/local/lib/libgtkpod.a
libtool: install: chmod 644 /usr/local/lib/libgtkpod.a
libtool: install: ranlib /usr/local/lib/libgtkpod.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib
```

---

### Post by toodh on 2013-03-23
Thanks for the quick answer!

I managed with a lot of fiddling to get it working. I believe the problems arose because I am running a 64bit linux. Indeed, if you compare our output, the only difference is in my
7 -  Architecture: [ amd64 ]
versus your
7 -  Architecture: [ i386 ]

As a consequence, many required libraries resided in a different folder than what the installation procedure expected: the installation said it could not find them in /usr/lib/i36-linux-gnu because they were in /usr/lib/x86_64-linux-gnu. So I renamend and relinked, then performed the installation, and afterwards undid the renaming and relinking. I don't know why this worked, so I can't recommend it, but since it worked for me, somebody might find this useful.

---

### Post by PDA1 on 2014-01-13
I'm desperately trying to get this to work (install gtkpod).

I paste both of the aforementioned code groups into Terminal and execute them one at a time. 

In step 2- (*2 Download, compile and install:-*) am I supposed to do something after Step 2 ends? That is- "compile" "install"? If so, would you please give the commands I'm to use and where they're to be executed?

Thanks.

There is no .deb file on my Desktop

---

### Post by Juvr on 2014-04-16
First off:

> **PDA1 said:**
> I'm desperately trying to get this to work (install gtkpod).

I paste both of the aforementioned code groups into Terminal and execute them one at a time. 

In step 2- (*2 Download, compile and install:-*) am I supposed to do something after Step 2 ends? That is- "compile" "install"? If so, would you please give the commands I'm to use and where they're to be executed?

Thanks.

There is no .deb file on my Desktop

What does the last line say when the installation is done? If it says something like

configure: error: *** No package 'libgpod-1.0' found

you basically just have to install that package and then do the whole thing again.


Now, I've run in to some problems too. I was missing a couple of packages so naturally the installation stopped and asked for them.
After installing everything it asked for it now stops at the same place in the process and says:

configure: error: The curl library could not be found. Explicity disable support by rerunning with --without-curl

I have both the packages curl and curlftpfs insalled, and I've been trying to figure out where --without-curl is supposed to be inserted but can't seem to get it right.
Anyone have any suggestion?

Cheers!

---

### Post by PDA1 on 2014-04-16
My opinion is simple- give up. I did.

Instead I use GtkPod by way of Ubuntu 10.04 in Virtual Box.

Here's how I did it- 

[http://ubuntuforums.org/showthread.php?t=2199542](http://ubuntuforums.org/showthread.php?t=2199542)

GtkPod is a fantastic program but whoever is developing it should see that other versions of Ubuntu can use it and not leave it to be configured by someone whose an expert computer operator to get it to run.

---

### Post by Kamron on 2014-04-16
Rhytmbox worked perfectly for me when I had my iPod back in the day...

---

### Post by PDA1 on 2014-04-17
> **Kamron said:**
> Rhytmbox worked perfectly for me when I had my iPod back in the day...

Past tense- *"worked*"

I've tried them all (see my link above) and have exhausted too many hours *in hope against hope* that I could get anything to work other than iTunes (which I will not use anymore).

Very, very few people are going to expend their time in trying to get a program to work after about 2 hours. If it doesn't work "out of the box" (as they say) or with a few minor, easy changes then it's not worth using. And the idiot(s) that have the fancy web sites that answer questions (supposed questions) about, "does Linux offer a program like iTunes?", then they promptly blab about the various junk programs that'll run an iPod....even though they never, ever tried themselves to see if they work. 
Here's an example- [http://askubuntu.com/questions/90197/what-software-is-available-for-ipod-synchronization](http://askubuntu.com/questions/90197/what-software-is-available-for-ipod-synchronization)

And forget about putting video onto an iPod Classic unless you know how to convert it using FFMPEG to mp4 or m4v and if the video is over 15 minutes in length then you *really* have to know what  you're doing. Don't expect any help from the grouches on the FFMPEG mailing list either. The only one that knows how to solve those sort of problems is "FakeOutdoorsman" here on the Ubuntu forum. He knows his stuff and is very helpful.

GtkPod is great...it really is. But the guy that's writing the program never fixes it for newer versions of Ubuntu and yet continues its development.

I have no loyalties to any program- I just need something to easily work with my iPod (which I now use in Virtual Box running Ubuntu 10.04.

---

### Post by Yellow Pasque on 2014-04-17
The question you link to is over two years old and refers to a long EOL release, so I'm not sure why you're calling people idiots/liars...
Furthermore, the programs in question all use the libgpod library, so if none of them work, it's probably an issue with that (or one of its supporting libraries like libimobiledevice).

> And forget about putting video onto an iPod Classic unless you know how to convert it using FFMPEG to mp4 or m4v and if the video is over 15 minutes in length then you really have to know what you're doing. Don't expect any help from the grouches on the FFMPEG mailing list either.
Handbrake has presets for those devices, but I'm guessing you tried that?

---

### Post by PDA1 on 2014-04-17
> **Temüjin said:**
> The question you link to is over two years old and refers to a long EOL release, so I'm not sure why you're calling people idiots/liars...
Furthermore, the programs in question all use the libgpod library, so if none of them work, it's probably an issue with that (or one of its supporting libraries like libimobiledevice).




Handbrake has presets for those devices, but I'm guessing you tried that?

Oh, I wasn't calling them liars....just idiots. 

Each version of Handbrake has presets that are dependent on a specific version of FFMPEG. If you don't have them right then you'll only get an unuseable transcode.

---

### Post by Yellow Pasque on 2014-04-17
The first thing I would do is try a live version of Ubuntu Trusty, as it has the later versions of libgpod and libimobiledevice. If that doesn't work, then my next guess would be that it's an issue with libhashab.so:
[http://ubuntuforums.org/showthread.php?t=2030727](http://ubuntuforums.org/showthread.php?t=2030727)

---

### Post by PDA1 on 2014-04-17
> **Temüjin said:**
> The first thing I would do is try a live version of Ubuntu Trusty, as it has the later versions of libgpod and libimobiledevice. If that doesn't work, then my next guess would be that it's an issue with libhashab.so:
[http://ubuntuforums.org/showthread.php?t=2030727](http://ubuntuforums.org/showthread.php?t=2030727)


Thanks for the ideas but I've chased too many solutions like that to end up where I am now.

---

### Post by Yellow Pasque on 2014-04-17
@Juvr: I would recommend starting a new thread...
BTW, you need -dev packages (e.g. libcurl4-gnutls-dev) when configure complains about something missing.

---

