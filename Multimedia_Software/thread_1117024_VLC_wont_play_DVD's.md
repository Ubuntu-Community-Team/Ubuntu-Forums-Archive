---
title: "VLC wont play DVD's"
date: 2009-04-05
forum: Multimedia Software
---

### Post by XWolf on 2009-04-05
I'm running 64x Ubuntu 8.10, I've got vlc installed and all of that, I throw in a dvd and it begins to play, video sound and everything for the Warning screens about pirating and the opening thing for example New Line Cinema production, but once it comes time for the menu to pop up all I get is the open vlc box like the movie just ended, no movie, no sound, nothing. I've tried browsing the disc and opening the .VOB files and they do the same thing it opens vlc but doesn't play anything. Does anybody have any ideas of what this is or a solution? I'm kind of new to ubuntu so it could be I haven't done something I need to or something like that.

---

### Post by coffeecat on 2009-04-05
Most likely thing is you've not got libdvdcss2 installed. You need this to decrypt encrypted commercial DVDs. You get libdvdcss2 from the [medibuntu]("http://www.medibuntu.org/") repository. Since you've installed VLC you may already have that repo enabled, but if not, follow the [howto here]("https://help.ubuntu.com/community/Medibuntu"). Now you can install libdvdcss2 via Synaptic.

While you're about it, it's a good idea to make sure you've got the package ubuntu-restricted-extras installed as well.

---

### Post by XWolf on 2009-04-05
I installed libdvdcss2, and got the ubuntu-restricted-extras package as well. Now when I go to play the dvd I get the following error, 
-----------------------------------------------------------------------------
Playback failure:

VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.

Playback failure:

DVDRead could not read block 0
-----------------------------------------------------------------------------

What does that mean? because I did see I had something installed called libdvdread3. I'm guessing that is the cause of the second playback failure...? But that didn't happen before.

---

### Post by coffeecat on 2009-04-05
No, you need libdvdread3 as well. If I remember correctly, that comes in with the restricted extras package.

I'm stumped. Try playing the DVD in Totem. And install mplayer and try that as well.

---

### Post by XWolf on 2009-04-05
MPlayer works but it's glitchy, has this graph looking thing pop up really quick and go away every so often.

Flash is messed up now too, anything requiring a flash plug in shows up grey now (youtube videos, etc.)

---

### Post by mc4man on 2009-04-05
Unfortunately while starting the 0.9.x versions of vlc from a terminal with vlc -vv  may show the problem will also produce alot of unneeded info.

Why don't you try checking on libdvdcss2 first

To do so first go into your your home folder (view -> show hidden files), find the .dvdcss folder and delete it.

Then open a terminal and start up vlc with this, attempt to play the disc, (media -> open disc, ect.) and after whatever does happen  close out vlc and look in home folder for a file 'vlc_output'.
It may have some useful info
```

export DVDCSS_VERBOSE=2 && vlc > vlc_output 2>&1
```


edit: was posting sametime as you, interesting that mplayer plays (sort of)

You could also try changing your audio and video ouputs (tools -> settings in vlc, if gmplayer then r. click on -> preferences  (remember to save in vlc

Also newline does sometimes use really screwed up structure protection, maybe post title name and or try a different dvd if available

---

### Post by XWolf on 2009-04-05
I don't know what any of this means lol but that is what I get in the output file
--------------------------------------------------------------------------
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdcss debug: opening target `/dev/scd0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key d0:16:92:33:78
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 26:91:e7:fa:3c
libdvdcss debug: using CSS key cache dir: /home/swan/.dvdcss/AHX-2002050317000900-2691e7fa3c/
libdvdcss debug: getting title key at block 314 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 26:91:e7:fa:3c
libdvdcss debug: decrypted title key e1:dd:c4:5e:dc
libdvdcss debug: title key is e1:dd:c4:5e:dc
libdvdcss debug: getting title key at block 10400 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 26:91:e7:fa:3c
libdvdcss debug: decrypted title key e1:dd:c4:5e:dc
libdvdcss debug: title key is e1:dd:c4:5e:dc
libdvdcss debug: getting title key at block 20146 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 26:91:e7:fa:3c
libdvdcss debug: decrypted title key e1:dd:c4:5e:dc
libdvdcss debug: title key is e1:dd:c4:5e:dc
libdvdcss debug: getting title key at block 3131275 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 26:91:e7:fa:3c
libdvdcss debug: decrypted title key e3:70:82:54:29
libdvdcss debug: title key is e3:70:82:54:29
libdvdcss debug: getting title key at block 3131279 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 26:91:e7:fa:3c
libdvdcss debug: decrypted title key e3:70:82:54:29
libdvdcss debug: title key is e3:70:82:54:29
libdvdcss debug: getting title key at block 3225194 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 26:91:e7:fa:3c
libdvdcss debug: decrypted title key df:98:59:a8:eb
libdvdcss debug: title key is df:98:59:a8:eb
libdvdcss debug: getting title key at block 3225198 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 26:91:e7:fa:3c
libdvdcss debug: decrypted title key df:98:59:a8:eb
libdvdcss debug: title key is df:98:59:a8:eb
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: AHX
libdvdnav: DVD Serial Number: 2ca40004
libdvdnav: DVD Title (Alternative): AHX
libdvdnav: Unable to find map file '/home/swan/.dvdnav/AHX.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[00000462] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[00000448] main decoder error: decoder is leaking pictures, resetting the heap
[00000449] main video output error: picture to date 0x1322798 has invalid status 6
[00000449] main video output error: picture to display 0x1322798 has invalid status 6
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000488] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: AHX
libdvdnav: DVD Serial Number: 2ca40004
libdvdnav: DVD Title (Alternative): AHX
libdvdnav: Unable to find map file '/home/swan/.dvdnav/AHX.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
--------------------------------------------------------------------------

---

### Post by mc4man on 2009-04-05
What's it's showing is that while it gets the initial 'disc' key and some title keys it's unable to retrieve any keys for the various title sets, in other words it's basically stopping at that point. (if you look closely all attempts are repetitions of same thing ( 3 different attempts and of almost no value

Normally you'd see something like this> .....clipped
libdvdread: Get key for [COLOR="Red"]/VIDEO_TS/VIDEO_TS.VOB [/COLOR]at 0x0000022b
libdvdcss debug: getting title key at block 555 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: title key is 00:00:00:00:00
libdvdcss debug: unencrypted title
libdvdread: Elapsed time 0
libdvdread: [COLOR="Red"]Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000030d[/COLOR]
libdvdcss debug: getting title key at block 781 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 2b:36:e4:e9:d7
libdvdcss debug: decrypted title key e8:c1:83:82:ba
libdvdcss debug: title key is e8:c1:83:82:ba
libdvdread: Elapsed time 0
libdvdread: [COLOR="Red"]Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000020ad[/COLOR]
libdvdcss debug: getting title key at block 8365 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 2b:36:e4:e9:d7
libdvdcss debug: decrypted title key e8:c1:83:82:ba
libdvdcss debug: title key is e8:c1:83:82:ba
libdvdread: Elapsed time 1
libdvdread: G[COLOR="Red"]et key for /VIDEO_TS/VTS_02_1.VOB at 0x0026d4b5[/COLOR]
libdvdcss debug: getting title key at block 2544821 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 2b:36:e4:e9:d7
libdvdcss debug: decrypted title key e6:50:b9:fb:48
libdvdcss debug: title key is e6:50:b9:fb:48 
............ect



Do you know if a region has been set on this drive?

While not always necessary to have a region set, not having it set can block access for the player

The movie (american history x) wouldn't have any structure protection that would be a problem  (was released before the 'good' protections came out

If you don't know whether a region has been set then install regionset
```
sudo apt-get install regionset
```

With a dvd in the drive run 
regionset
look at line 4 "type:", if it says none then go y and set to 1. if it says "set" then go n and exit

Ex. of a set drive
> doug@doug-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n


---

### Post by XWolf on 2009-04-05
When I type regionset it says the same exact thing as your example does.

---

### Post by euriconeto on 2009-04-10
Hi,
I have installed all codecs and followed most tips on threads re this issue, but both my players (Totem and VLC) doesn't play any DVDs. Tried installing mplayer too but that didn't work as well.
Keeps sending the same massage:
"main decode error: decoder is leaking pictures, resetting the heap"

Any help?
Cheers,
Eurico

---

### Post by beezwings on 2009-04-15
Hello all~

I'm having similar problems.  I've googled and followed many posts on installing libdvdcss2, my region is set, but I still cannot play certain DVDs (I think it's still an encryption issue). In Totem-Xine, I get the error: ""The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" and but I've installed and reinstalled.  I've tried deleting the .dvdcss folder, no help. In VCL, it tries to load, but nothing happens.  In mplayer I get a "seek" error. Any help would be appreciated, thanks!

---

### Post by thismuchiknow on 2009-05-04
Hi, like the posters above I have tried installing libdvd packages, reinstalled vlc, totem, mplayer and several other media players and none will work. I've read lots of posts on these boards about the problem but everything i've tried has not worked.

I'm not very knowledgeable on code or ubuntu so if I cant solve this soon I will basically have to give up and go to another Linux version or back to XP. I dont want to do that, so hope someone can help.

Any tips appreciated!

---

### Post by xc3RnbFO8P on 2009-05-04
Try this (jaunty):
[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5]("http://ubuntuforums.org/showpost.php?p=7197110&postcount=5")

---

### Post by bhold on 2009-05-05
> **beezwings said:**
> Hello all~

... In Totem-Xine, I get the error: ""The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" and but I've installed and reinstalled.  I've tried deleting the .dvdcss folder, no help. 

I have been having this problem a lot on 8.10 with encrypted DVDs. What seems to working, for now at least, is to remove the contents of the .dvdcss folder prior to inserting the DVD. I am not having this problem on 8.04  but I don't want to go back as long as the workaround holds.

---

### Post by bhold on 2009-05-05
After many problems trying to play DVDs on 8.10,with multiple players, I am giving up. Latest problem - subtitle font and color configuration in VLC does not work and they are almost unreadable. (Try watching Mongol without readable subtitles!)

Things work much better on 8.04, so I will use my 8.04 partition for DVD playback using VLC. I will continue to use 8.10 for most other things. I stay current on all patches, so will occasionally test DVD playback on 8.10 to see if things start working better.

Best of luck to those of you with more patience, time, and expertise than I have as you pursue solutions to these problems.

---

