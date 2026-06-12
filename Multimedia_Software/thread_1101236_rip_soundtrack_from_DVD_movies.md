---
title: "rip soundtrack from DVD movies?"
date: 2009-03-20
forum: Multimedia Software
---

### Post by ucalagon on 2009-03-20
In the bad ole daze of Creaky Gates, I used to have an app which would rip music tracks and sound effects from DVD movies and PC games.  Does such a prog exist for ubuntu 8.10, please?
All help very welcome - Thanks in advance
David in Norfolk UK

---

### Post by MaindotC on 2009-03-20
The program is simply called dvd::rip - it's in the repos.

---

### Post by ucalagon on 2009-03-20
Thanks strAlan - how's Morrisville, daughter's in Westport.  Got this on install...
E: linux-restricted-modules-2.6.27-14-generic: subprocess post-installation script returned error exit status 1
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
Any thoughts?   David

---

### Post by jocheem67 on 2009-03-20
This tends to be a tricky matter nowadays...

I've been investigating this extensively, 'cause I've got some music-dvd's that I wanted to rip to ogg.

Are you new to linux? The standard is using mplayer, but that's cli stuff...
There are threads around the forum, with the proper commands...

My method is different, as mplayer hasn't been that 'friendly' lately.

I use vobcopy:

> vobcopy -l

This creates one big vob file from the dvd

Next I load the vob into avidemux ( repo-stuff )

Here you can choose to only rip/copy the audio to ms-wav 

The resulting wav can be processed with audacity and cut and converted to whatever format.

---

### Post by MaindotC on 2009-03-20
Morrisville sucks - spring + fall semester + internship and I'm outta here!  Hopefully on to be some god Unix admin somewhere - maybe SUNYIT (they have a posting for Unix admin)

I'm assuming you tried using sudo apt-get install dvdrip?  If so, check the dependencies to see if it needs linux-restricted-modules.  Should be in their documentation.

---

### Post by meho_r on 2009-03-20
> **ucalagon said:**
> Thanks strAlan - how's Morrisville, daughter's in Westport.  Got this on install...
E: linux-restricted-modules-2.6.27-14-generic: subprocess post-installation script returned error exit status 1
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
Any thoughts?   David

Bah, postinstall errors are more and more present in newer versions of Ubuntu (found them in Debian too, so it's probably problem with Debian). However, just to avoid annoyance of getting error message every time you install/uninstall/update things, do the following:

1. you'll find postinst script here: /var/lib/dpkg/info Look for the one with .postinst extension (i.e. in your case it'll be: **linux-restricted-modules-2.6.27-14-generic.postinst** or something similar

2. open it with a text editor and add "exit 0" (without quotes) just few lines down from the beginning of file, immediately after "set -e"


3. sudo apt-get install -f

---

### Post by jocheem67 on 2009-03-20
:D

With my method, if interested, it's opening avidemux ---- look at the menu on the left ----- 'video copy' ------- 'audio' make it 'wav pcm' ----- go to the topmenu ----- 'audio' 'save'...

It's pretty foolproof;)

BTW encoding the audio directly to for example vorbis should also be possible, but I never tried it, 'cause audacity did that for me later in the process.

---

### Post by andrew.46 on 2009-03-20
Hi jocheem,

> **jocheem67 said:**
> BTW encoding the audio directly to for example vorbis should also be possible, but I never tried it, 'cause audacity did that for me later in the process.

The newest Transcode will do this:

```

andrew@skamandros~$ transcode --version
transcode v1.1.1 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team

```

although I will admit that several processes are set off by a single commandline:

```

transcode -x dvd -i /dev/dvd -T 1,3,1 -a 0 -y null,ogg \
-b 192 -E 44100,16,2 -o $HOME/Desktop/james_brown.ogg

```

I have just finished using the commandline above which imports track 1, chapter 3, 1st audio stream of the Blues Brothers (the James Brown cameo) and exports it in ogg format, seting the bitrate and resampling the rate as it goes (using oggenc). How cool is that :-).

All the best,

Andrew

---

### Post by jocheem67 on 2009-03-21
Thanks for the insight.;)

However my "vobcopy --- avidemux" method hasn't failed me yet, so I'll stick to that.

The CLI is impressive but for encoding it's always a lot of wrong typed commands in my case:o

The times I did try to encode through transcode and mencoder, I always had terrible syncing-problems.

Having said that  must admit that I sometimes use the basic "lame" and "oggenc" commands..

---

