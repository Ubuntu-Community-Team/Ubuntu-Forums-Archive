---
title: "ffmpeg - error after possible update"
date: 2010-01-05
forum: Multimedia Software
---

### Post by garryknight on 2010-01-05
I noticed that a lot of software updates were ready today so I installed all of them without thinking to make a note of what they were, so I don't know if ffmpeg or one of its dependencies was amongst them. The very next time I ran ffmpeg, it gave me an error I haven't seen before.

After downloading a file from BBC's iPlayer site using get-iplayer, I ran a script to convert it to a format suitable for my Samsung YP-Q2 personal media player. I copied the command out of that script and pasted it onto the command line so that I could capture the console output of that encoding session, shown below:

```
[garry tv]$ ffmpeg -i inputfile.mp4 -acodec libmp3lame -ar 44100 -ab 128k -ac 2 -vcodec mpeg4 -b 1024k -r 15 -s qvga outputfile.avi
FFmpeg version git-bcf9828, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Oct 25 2009 11:48:38 with gcc 4.4.1
  configuration: --enable-gpl --enable-nonfree --enable-shared --enable-pthreads --enable-libx264 --enable-libfaac --enable-libtheora
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.37. 1 / 52.20. 0
  libavformat   52.39. 2 / 52.31. 0
  libavdevice   52. 2. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9d27700]ISO: File Type Major Brand: isom
st:1 removing common factor 48 from timebase

Seems stream 0 codec frame rate differs from container frame rate: 100.00 (100/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'inputfile.mp4':
  Duration: 00:58:39.02, start: 0.000000, bitrate: 831 kb/s
    Stream #0.0(und), 1/50: Video: h264, yuv420p, 640x360, 1/100, 25 tbr, 50 tbn, 100 tbc
    Stream #0.1(und), 1/1000: Audio: aac, 48000 Hz, stereo, s16
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avcodec_channel_layout_num_channels
[garry tv]$

```This error, "undefined symbol" is what makes me think that either ffmpeg or one of its dependencies has been updated or the error would have occurred before now. I've been using the script with the command in the above form for some weeks now with no problems, almost always converting an MP4 (but sometimes a .mov) into an AVI.

Thinking that it might be the version of ffmpeg in the standard repos, I followed the advice of _[this thread]("http://ubuntuforums.org/showthread.php?t=1117283")_ and removed the standard ffmpeg and installed the one from Medibuntu. (Removing the standard one took WinFF and DVDRip with it, but I reinstalled those afterwards, and I'm sure they don't come into the equation otherwise.)

I re-ran the command and the error was exactly as before. Is ffmpeg recently borked or am I missing something obvious? Or something obscure, for that matter?

---

### Post by mc4man on 2010-01-05
What you might want to look at is where did this come from? (and where is it? (/usr/local/bin
> FFmpeg version git-bcf9828......built on Oct 25 2009

It's not the karmic repo version and I don't see where medibuntu has ever had a ffmpeg package ( only the libs in hardy and karmic

---

### Post by garryknight on 2010-01-06
It came from following option C in this post: [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

However, I've just realised that uninstalling ffmpeg, adding the Medibuntu repo to my sources, then installing ffmpeg, doesn't guarantee that I'm getting the Medibuntu version, does it? I've just gone into Synaptic and checked the Origin section. While multiverse has the libavcodec-extra-52 that the article talks about, I don't see ffmpeg anywhere on Medibuntu.

So it seems I reinstalled the same version I uninstalled. :( My own fault; that article dates from April last year.
Edit: I've just checked and my version of ffmpeg came from the main Ubuntu repo. "apt-cache show ffmpeg" gives this:
Version: 4:0.5+svn20090706-2ubuntu2

But I'm still no nearer understanding why I'm suddenly getting an undefined symbol error from a program that was running ok before. I'll have more time tomorrow, hopefully, so I'll do some exploring.

---

### Post by FakeOutdoorsman on 2010-01-06
> **garryknight said:**
> It came from following option C in this post: [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

However, I've just realised that uninstalling ffmpeg, adding the Medibuntu repo to my sources, then installing ffmpeg, doesn't guarantee that I'm getting the Medibuntu version, does it? I've just gone into Synaptic and checked the Origin section. While multiverse has the libavcodec-extra-52 that the article talks about, I don't see ffmpeg anywhere on Medibuntu.

So it seems I reinstalled the same version I uninstalled. :( My own fault; that article dates from April last year.
Edit: I've just checked and my version of ffmpeg came from the main Ubuntu repo. "apt-cache show ffmpeg" gives this:
Version: 4:0.5+svn20090706-2ubuntu2

But I'm still no nearer understanding why I'm suddenly getting an undefined symbol error from a program that was running ok before. I'll have more time tomorrow, hopefully, so I'll do some exploring.

The thread was originally posted in April 2009, but I try to keep it up to date as shown at the end of the original post: *Last edited by FakeOutdoorsman; 2 Weeks Ago at 11:30 PM.. Reason: added Medibuntu info for Karmic, removed ubuntu-restricted-extras option*

It seems that you are using a third-party FFmpeg.  Do you have any third-party repositories or PPAs enabled?  Show the output of your */etc/apt/sources.list* file and the output of any files in */etc/apt/sources.list.d/*.

---

### Post by mc4man on 2010-01-06
I would take a look in synaptic for what version of the shared ffmpeg libs are installed. - libavcodecXX, ect.
 (also take a look thru /usr/local for ffmpeg folders and files if the ones in synaptic are the karmic/medibuntu repo libs

your orig. post indicated that that ffmpeg (git) was built as 'shared'

It's pretty unusual for someone to offer a git ffmpeg package set vs. a svn one.

---

### Post by garryknight on 2010-01-06
**FakeOutdoorsman**:

My /etc/apt/sources.lst:
# deb cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
and the contents of /etc/apt/sources.list.d:

google-chrome.list
google-chrome.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
opera.list
opera.list.save
sportman1280-ppa-karmic.list
sportman1280-ppa-karmic.list.save
ubuntuone-beta-sources.list
ubuntuone-beta-sources.list.save

The sportman ppa is disabled.

~~~~~~~~~~~~~~~~~~~~~~~~~~
**mc4man**:

I'm not sure what I'd be looking for in /usr/local. There are some header files in include, a lot of libraries in lib, and 16 .ffmpeg files in share/ffmpeg.

As for the ffmpeg libs:
libavcodec-extra-52  version 4:0.5+svn20090706-2ubuntu3+medibuntu1
libavcodec-unstripped-52  version 4:0.5+svn20090706-2ubuntu3

I'm beginning to wonder if I missed out a step in FakeOutdoorsman's post, but I'm pretty sure I didn't.

---

### Post by mc4man on 2010-01-06
> I'm beginning to wonder if I missed out a step in FakeOutdoorsman's pos

It has nothing to do with that.. You installed or maybe built and installed ffmpeg as shared to /usr/local. Those libs, and ffmpeg if still installed in /usr/local/bin are conflicting with whats in /usr (the ones you want

I'd go to /usr/local as root,(Alt+F2, run gksu nautilus - not in terminal) and delete all ffmpeg files, libs and folders in
/usr/local/bin
/usr/local/include
/usr/local/share
usr/local/lib

Then run in terminal
```
sudo ldconfig
```

you may also want to then open synaptic, search ffmpeg and remove all the 'unstripped' versions of the ffmpeg libs.

---

### Post by garryknight on 2010-01-07
If I hadn't been so exhausted last night I would have realised straight away that that was precisely the problem. If ffmpeg is saying that it's a git version yet apt-cache show says it's an svn version, then obviously there are two versions on board. And /usr/local/bin is indeed where I found the misbehaving one.

How I ended up with two versions, I've no idea. I certainly haven't compiled one. I installed 9.04 then the nonfree stuff, then upgraded to 9.10, and then followed FakeOutdoorsman's post. Anyway, thanks to both of you for your input. It's been very helpful.

---

