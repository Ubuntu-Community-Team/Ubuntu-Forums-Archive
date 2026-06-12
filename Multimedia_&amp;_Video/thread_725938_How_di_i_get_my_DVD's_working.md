---
title: "How di i get my DVD's working???"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by emshains on 2008-03-16
I've been trying to watch my dvds for like a month, but i havent found detailed thread or how-to.
ive installed with apt-get livdvdcss2 and libdvdread. Still totem wines about libdvdcss, but mplayer tries to run the film, but it is budgy, it sort of hangs up, then tries to play the movie, but both the sound the video is screwed. Im tired of this. 

Ubuntu had more users if it had detailed instructions of how to play dvds.

---

### Post by AJB2K3 on 2008-03-16
[Use Search]("http://ubuntuforums.org/search.php")

We have all had trouble with totem and it has been posted lots of times.
doe's xine gui work?

[This may help]("http://ubuntuforums.org/showthread.php?t=724734")

---

### Post by 6205 on 2008-03-16
You cannot play DVD's with Totem-Gstreamer and because Totem-Xine is partially broken (cannot play some videos with vorbis audio) i'm using for DVD playback _only_ Xine Media Player - it's excellent and fully compatible with Compiz (not so dumb VLC) Playback of the rest of the videos leave to Totem-Gstreamer ("ubuntu-restricted-extras" metapackage will install all necessary gstreamer multimedia plugins)

[COLOR="Red"]sudo apt-get install xine-ui[/COLOR]

---

### Post by liquidfunk on 2008-03-16
I suggest VLC, all I did was install Libdvdcss2, install VLC, pop a DVD in and BANG! The magic happened.

---

### Post by emshains on 2008-03-16
Vlc wont even show a video window, just a toolbar. Ive installed libdvdcss2, VLC, totem-xine, xine, gxine, mplayer and every damn plugin for them and still no luck.

I have xine movie player, but i have no Xine DVD player, neither i can get it from synaptic.

---

### Post by xc3RnbFO8P on 2008-03-16
In terminal:
> xine
<return>  play video and show the output.

---

### Post by 6205 on 2008-03-16
> **emshains said:**
> Vlc wont even show a video window, just a toolbar. Ive installed libdvdcss2, VLC, totem-xine, xine, gxine, mplayer and every damn plugin for them and still no luck.

I have xine movie player, but i have no Xine DVD player, neither i can get it from synaptic.

Xine DVD Player is only my custom renamed shortcut, if you have_ xine-ui + libdvdcss2 + libdvdread3_ installed DVD movie playback must work

btw. i asume that you have enabled medibuntu repository for libdvdcss2 _medibuntu_ version

---

### Post by emshains on 2008-03-16
> **6205 said:**
> Xine DVD Player is only my custom renamed shortcut, if you have xine-ui + libdvdcss2 + libdvdread3 istalled DVD movie playback must work

btw. i asume that you have enabled medibuntu repository for libdvdcss2 medibuntu version

I have enabled medibuntu reps, i have installed all dependencies I could need.


Here is what I get with the terminal
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
AFD changed from -2 to -1
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open xine dvd:// %u with libdvdcss.
libdvdread: Can't open xine dvd:// %u for reading
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open xine dvd:// %u with libdvdcss.
libdvdread: Can't open xine dvd:// %u for reading
AFD changed from -2 to -1
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd1 mounted on /media/LITTLE_MISS_SUNSHINE for CSS authentication

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000141
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000182
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000182)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00002246
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00002246)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002c8ade
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x002c8ade)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002c8ae4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002c8ae4)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e371c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x002e371c)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e3721
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002e7e6e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x002e7e6e)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002e7e74
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x002e7e74)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002ea73e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x002ea73e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002ea744
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x002ea744)!!
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 1
AFD changed from -2 to -1
AFD changed from -2 to -1

---

### Post by mc4man on 2008-03-16
i wish you were using vlc - it's a little easier to troubleshoot - anyway what's the region of the dvd your trying to play and the region your drive is set to. If you have a region mismatch the keys have to be brute forced and sometimes on titles with structure protection this fails. (the brute forcing)

edit:if your drive has no region set then you need to set one. If you don't have a region mismatch, i.e. region2 drive, region2 disk, then try vlc - it may be better at retrieving keys from structure protected titles (little miss sunshine is an S.P. disc). Before running vlc go into home directory, find the .dvdcss folder and inside delete the file associated with little miss sunshine. then try vlc
If you have a region mismatch and vlc can't brute force then you need to put the proper keys into .dvdcss
[http://ubuntuforums.org/showthread.php?t=657516&page=3](http://ubuntuforums.org/showthread.php?t=657516&page=3)   (basically sharing keys)

---

### Post by xc3RnbFO8P on 2008-03-16
Install this again:

> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by emshains on 2008-03-16
> **Ringi said:**
> Install this again:

Done that, no effect, but i will try it again tomorow, i didnt reboot today btw.

Vlc doesnt give me any info on whats happening, xine pops out like two error logs, so i prefer xine.
But i will try to run VLC through the console tommorow, and post the results here again.

P.S. I dont want to start a vlc vc xine thread.

---

### Post by xc3RnbFO8P on 2008-03-16
You could also look in Synaptic Package Manager and search **xine** if something is missing.
And reinstall Xine.

---

### Post by cor2y on 2008-03-16
emshains for encrypted dvd playback please add the medibuntu repos to your source list.
visit [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to see how.
Next with those enabled , i suggest the following deb packages installed either via the terminal or synaptic.
libdvdcss2 (you should already have that installed)
libdvdnav
libdvdread3

With those installed and totem-xine you should be able to playback  encrypted commercial dvds now.

---

### Post by emshains on 2008-03-17
I know this would be a stupid mistake, but couldnt it be just a faulty dvd drive? Its like 7 years old, and it doesnt recognize dvd+r. 
I will try dvds out with another drive later.

---

### Post by dm6257 on 2008-03-19
Thanks a bunch.  I was about to give up on DVD playing on Ubuntu.  Your suggestions worked great with Xine.  

Dale

---

### Post by dm6257 on 2008-03-19
I followed Ringi's suggestion repeated below:

 Install the following:
Quote:
wget -c [http://packages.medibuntu.org/pool/f...untu4_i386.deb](http://packages.medibuntu.org/pool/f...untu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
Quote:
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

I was then able to play commercial DVDs using both Xine and Vlc.  Works great.  Nothing else worked.

WARNING:  Immediately after I got the DVD players working, I got an update notice that a newer version of libdvdcss2 was available from Medibuntu.  I installed the update and my dvd players scrambled the picture.  Something is amiss in the update.  I ran Ringi's scripts again and my DVD players are working again.  I disabled updates from Medibunti for the time being.

dm6257

---

### Post by Awperator on 2008-05-23
> **6205 said:**
> You cannot play DVD's with Totem-Gstreamer and because Totem-Xine is partially broken (cannot play some videos with vorbis audio) i'm using for DVD playback _only_ Xine Media Player - it's excellent and fully compatible with Compiz (not so dumb VLC) Playback of the rest of the videos leave to Totem-Gstreamer ("ubuntu-restricted-extras" metapackage will install all necessary gstreamer multimedia plugins)

[COLOR="Red"]sudo apt-get install xine-ui[/COLOR]

Sorry to resurrect an old thread on a different topic, but is there any information about Xine in Ubuntu supporting Vorbis?

---

