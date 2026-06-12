---
title: "Can't play DVDs in Maverick!"
date: 2011-02-20
forum: Multimedia Software
---

### Post by higashi on 2011-02-20
When I open a dvd with movie player in maverick, i get an error saying "Could not read from resource".
VLC gives me > Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
Playback failure:
DVDRead could not read block 0.

I found a thread that told me to run ```
sudo /usr/share/doc/libdvdread4/install-css.sh
``` but that didn't help. Any suggestions?

---

### Post by SleepWalkerX on 2011-02-20
Try adding the medibuntu repository and installing libdvdcss.

[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by gerowen on 2011-02-20
Bad DVD?  VLC should come with everything it needs out of the box.  That error literally says, "Could not read block 0" so it sounds like maybe a bad DVD, or a dirty DVD drive.  Installing libdvdread and libdvdcss may help, who knows.

---

### Post by PaulReaver on 2011-02-20
is the disc scratched or dirty?

do you have the codecs installed for playing mpeg2?
you'll need to install gstreamer-plugins-ugly gstreamer-plugins-bad libdvdnav4 and libdvdread4

then restart your pc. should work

---

### Post by PaulReaver on 2011-02-20
> **SleepWalkerX said:**
> Try adding the medibuntu repository and installing libdvdcss.

[http://medibuntu.org/](http://medibuntu.org/)

he already installed it from the medibuntu repo.... that's where the /usr/share/doc/libdvdread4/install-css.sh script installs it from :)

---

### Post by SleepWalkerX on 2011-02-20
Try opening the disc with totem (File -> Open Disc) and see what happens.  I'm betting its a libdvdcss problem.  If not, then yeah its a bad disc.

---

### Post by higashi on 2011-02-20
Thanks, Sleepwalker x, that did the trick :)

---

### Post by lozobo on 2011-03-06
Hi
It happened to me too, with an original and brand new DVD.

I've tried to run totem with the --debug option.
The output told that is missing the libdvdcss packet and try to read this file [1] in the doc.
There is told to download and install the packet that found here [2] (by svn or from normal releases). 
And then it worked all fine for me. (Finally i can watch Indiana Jones =D)

PS: To the developers or to the packager... Maybe it's the case to insert this packet in the repository? This just to avoid all of this "mess" to see a DVD... I use maverick and there isn't present... 
I think that add a packet is better than add an whole repository just for one packet...

[1] - /usr/share/doc/libdvdread4/README.Debian
[2] - [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

---

### Post by EvilNed01 on 2011-03-07
Hi, 

I too get the same error message.

I have all the resources mentioned installed - including the latest libdvdcss (altough it is referred to as libdvdcss2, but it is the latest version 1.2.10.

I cannot play DVDs with Totem or VLC or any other DVD player I have tried.

It is not a faulty DVD as I have tried it on a DVD player with no problems. It's brand new.

I am running Ubuntu 10.10, 64-bit version.

---

### Post by waynerking on 2011-03-19
I have been trying to play DVDs since first installing maverick, tried lucid, tried edubuntu, netbook, 32 and 64 bit, reinstalled more times than I ever did with windoze, and still no dvd player. VLC cannot open location, Mplayer played a few seconds then shows "internal data error"...Gnome player played 4 of 11 .avi files from DVD-DL, and mounted @ /media/ and played a mixed datadisc  mounted @/sys/block/sr0. I have linked all possible locations for mounting and still cannot play a commercial dvd at all. the drive just spins and tries to read..., then gives up..., "location not found" I have been googling this issue for a month, and tried everything suggested, but no luck. It's a new HP G62 netbook, TS-L633N DVD+/-/rw/dl super multi light scribe player. Intelpentium2coreT4500, 3gigs ram, ICH9M/m-e-sata AHCI controller. Any other links to try?

---

### Post by inobe on 2011-03-19
if anyone else is looking, you can find much of everything in the documentation.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

