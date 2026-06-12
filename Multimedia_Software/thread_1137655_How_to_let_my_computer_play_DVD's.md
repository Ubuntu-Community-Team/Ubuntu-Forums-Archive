---
title: "How to let my computer play DVD's"
date: 2009-04-25
forum: Multimedia Software
---

### Post by m3alnemer on 2009-04-25
Hello!

After a massive work on ubuntu (7.xx) to got a DVD working on i decide that i will start this post and get it running with your help.:)

The Problem:
MPlayer,vlc and xing won't play movie DVD's.
On Movie player it says: "An Error occurred: Could not read from resource".
On VLC: It says:
"Playback failure:
DVDRead could not read -1/4 blocks at 0x1540."

i see there are two directories for the DVD ROM in the /media file
one /cdrom the other /cdrom0. none of those is the one that VLC plays by default. It has /dev/sr0. I tried to change that to the /cdrom or /cdrom0. also i tried to play it with no menu's.

I read many threads about problems that look like mine, but at the end i end up with rebooting to Mr.Bill Gate's OS and play it on winDVD:(

I read about xing package, but i don't know even what is it. 
Some body talked about the restricted extras.


any idea how to get that working?


I'm now on Jaunty


m3alnemer

---

### Post by pytheas22 on 2009-04-25
Did you install the 'ubuntu-restricted-extras' package?  That will allow you to play most DVDs.  Disks that are encrypted in a weird way or use strange file formats may still pose a problem, however.

---

### Post by mc4man on 2009-04-25
You can follow up the above suggestion with this

```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

(installs libdvdread4 if not already installed and then runs built-in script to download and install libdvdcss2 from medibuntu


Edit:
As a simple little test while I was posting this before I burnt a jaunty live cd, and booted my little laptop up to it (on the live cd now

Ran 1 command, hooked up an external dvd drive and can play back dvd's with vlc and totem-xine 

```
ubuntu@ubuntu:~$ sudo apt-get install libdvdread4 vlc totem-xine libxine1-ffmpeg && sudo /usr/share/doc/libdvdread4/install-css.sh
```

> ubuntu@ubuntu:~$ vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
................clipped.................
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: THE_WRESTLER
libdvdnav: DVD Serial Number: 3a4ca44f
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ubuntu/.dvdnav/THE_WRESTLER.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000002c7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000883a
libdvdread: Elapsed time 0
....clipped....
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
[00000465] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000


> ubuntu@ubuntu:~$ totem-xine
....clipped....
libdvdnav: Using dvdnav version 1.1.16.3 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: THE_WRESTLER
libdvdnav: DVD Serial Number: 3a4ca44f
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ubuntu/.dvdnav/THE_WRESTLER.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000002c7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000883a
libdvdread: Elapsed time 0


---

### Post by m3alnemer on 2009-04-26
:guitar::guitar::guitar:

I got it for real it worked

I just posted the codes 
```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```


```
ubuntu@ubuntu:~$ sudo apt-get install libdvdread4 vlc totem-xine libxine1-ffmpeg && sudo /usr/share/doc/libdvdread4/install-css.sh
```

and i'm good like that

> ubuntu@ubuntu:~$ totem-xine
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
libdvdnav: Using dvdnav version 1.1.16.3 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/m3alnemer/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000014e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000409a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0031a60d
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0


I don't have the ubuntu restricted installed


Thanks All:KS

---

### Post by mdpalow on 2009-04-29
See link below.

mdpalow

---

### Post by stoobers on 2009-04-30
I can't get my dvd's to play.  I also can't play any dvd .iso files.

I have enabled the medibuntu repositories (i think)
I ran the following:

 sudo apt-get install libdvdread4 vlc totem-xine libxine1-ffmpeg && sudo /usr/share/doc/libdvdread4/install-css.sh

I still get this error:
[00000466] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
libdvdnav: demux error! 00 00 00 (should be 0x000001) 

Then the playback stops.  This right after the menu.  What do I do?

---

### Post by Wiebelhaus on 2009-04-30
The only way I've ever been able to get them to work was with [Medibuntu]("http://www.medibuntu.org/")  using  [this how to:]("https://help.ubuntu.com/community/Medibuntu")

Cheers!

---

### Post by mc4man on 2009-04-30
@ stoobers
That command was specially for jaunty, is that what you're running?

libdvdcss2 available here (for any current ubuntu version
[http://packages.medibuntu.org/jaunty/libdvdcss2.html](http://packages.medibuntu.org/jaunty/libdvdcss2.html)

If you are using jaunty post the complete error message (start to finish

---

### Post by Stoneface on 2010-10-03
> **mc4man said:**
> You can follow up the above suggestion with this
```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```
(installs libdvdread4 if not already installed and then runs built-in script to download and install libdvdcss2 from medibuntu

Works like a charm. Thanks! Can now play DVDs from region 3 on my MacBookPro . They gave me trouble before. Now I need to see if I can make the same adjustments on OSX 10.6.4 so I can play the DVD outside my VirtualBox VMWare Fusion 3.1 with Ubuntu Lucid Lynx) as well...

---

