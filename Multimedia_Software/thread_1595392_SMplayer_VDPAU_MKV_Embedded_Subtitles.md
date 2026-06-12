---
title: "SMplayer VDPAU MKV Embedded Subtitles"
date: 2010-10-13
forum: Multimedia Software
---

### Post by hsoulen on 2010-10-13
Hi Folks,

Having a bit of an issue with SMplayer with VDPAU support on Lucid and wanted to see if anyone has any suggestions.

I have the latest Mplayer (VDPAU support), SMplayer as well as 256 Nvidia proprietary drivers installed and although I am getting great performance with VDPAU on mkv/mp4 files up to 1080p (majority of my rips are 720p) I cannot seem to get embedded subtitles to show.

Occasionally while fiddling with settings for Subs I see some of the subtitles render for a few seconds, always huge fonts and off to one side of the video (not at the bottom as expected) but I will only see them for a few seconds and then "boom" gone.

I have tried a bunch of things from changing the encoding, the position on the screen etc. have enabled/disabled compositing, selected alternate rendering options etc. but no go.

Anyone got this working?

**Update**: Does not matter what renderer I use, tried X11, xv etc. No embedded subtitles in any of my MKV files. Weird.

**Update2**: Marked solved as I answered my own question... PGS subtitles not yet supported in mplayer...

Cheers,

Hank

---

### Post by ridewithstyle on 2010-10-13
Hello there,

not true, PGS subtitles can be displayed in the latest mplayer, but you have to build it yourself. I did on 10.04 and it worked with all of my pgs subtitled mkvs. So get the latest source and you should be fine.

greetings, trws

---

### Post by hsoulen on 2010-10-13
> **ridewithstyle said:**
> Hello there,

not true, PGS subtitles can be displayed in the latest mplayer, but you have to build it yourself. I did on 10.04 and it worked with all of my pgs subtitled mkvs. So get the latest source and you should be fine.

greetings, trws

Thanks a bunch for the advice, I will give it a shot. Besides the usual gcc/headers are there any special sources or repos I need to build it (will google to be sure)?

Last thing, I promise... Did you compile with vdpau support?

Thanks again.

Hank

---

### Post by andrew.46 on 2010-10-13
Hi,

There is a guide for Maverick:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Andrew

---

### Post by hsoulen on 2010-10-14
> **andrew.46 said:**
> Hi,

There is a guide for Maverick:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Andrew

Thank you both very much for the help!

Cheers,

Hank

---

### Post by ridewithstyle on 2010-10-14
Hello there, 

and just in case someone wants to compile the pgs supported mplayer with vaapi xvba (read ATI) support, here is a nice script that does that does all that for you.

[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/)

just run that and update the settings in smplayer according to the screenshots you find here

[http://www.loggn.de/ubuntu-mplayer-inkl-smplayer-mit-vaapi-unterstutzung/](http://www.loggn.de/ubuntu-mplayer-inkl-smplayer-mit-vaapi-unterstutzung/)

it's in german, but just have a look at the screenshots, no further reading comprehension is needed. 

Enjoy

---

### Post by hsoulen on 2010-10-14
This is why I love this community!

Cheers for all your help.

Hank

---

### Post by andrew.46 on 2010-10-20
Hi ride,

> **ridewithstyle said:**
> PGS subtitles can be displayed in the latest mplayer, but you have to build it yourself. 

Bumped into the revision details the other day, looks like [July 10 is the date]("http://git.ffmpeg.org/?p=mplayer;a=commit;h=db6bfa65031c2397961d5af86c8877c34ce57a89")...

Andrew

---

