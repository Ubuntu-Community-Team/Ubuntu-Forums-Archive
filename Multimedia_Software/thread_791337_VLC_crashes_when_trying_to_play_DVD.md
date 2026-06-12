---
title: "VLC crashes when trying to play DVD"
date: 2008-05-12
forum: Multimedia Software
---

### Post by Wikzo on 2008-05-12
I have a lot of troubles playing DVD discs on my laptop with Ubuntu 8.04. I think I got all the right codecs now, and I got VLC to start playing a DVD by default.

The problem is that VLC crashes a second after opening the DVD disc.

```
wikzo@iBuntu:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: MATRIX_RELOADED_DISC_1
libdvdnav: DVD Serial Number: 2EF27B53
libdvdnav: DVD Title (Alternative): MATRIX_RELOADED_DISC_1
libdvdnav: Unable to find map file '/home/wikzo/.dvdnav/MATRIX_RELOADED_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions: 2 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000f50
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000014fe
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000014fe)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0002975f
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
wikzo@iBuntu:~$ 

```

What should I do?
I used this guide to get the DVD codecs and get VLC to play DVD by default instead of Totem.[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD")

---

### Post by Wikzo on 2008-05-12
Okay, I just tried another DVD film - and it works. But it would be great to solve the crash by my other film...

The output of the working DVD film:

```
wikzo@iBuntu:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DVDVolume
libdvdnav: DVD Serial Number: c119f8f6        
libdvdnav: DVD Title (Alternative): DVDVolume
libdvdnav: Unable to find map file '/home/wikzo/.dvdnav/DVDVolume.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000005ec
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000348] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
[00000393] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000283] main playlist: stopping playback
wikzo@iBuntu:~$ 

```

Both DVD's are PAL like my laptop.

---

### Post by SorryGoFish on 2008-06-24
I think the issue is with new copyright protection. I'm trying to figure this out also. We may have to wait for libdvdnav to be updated.

---

### Post by SorryGoFish on 2008-06-24
I think [this]("http://www.mail-archive.com/freevo-devel@lists.sourceforge.net/msg16537.html") is related.

---

### Post by SorryGoFish on 2008-06-24
I got it to work by adding the medibuntu repository and installing w32codecs and libdvdcss2. You'll probably want to update other media applications too with that repository. You also probably don't need w32codecs for your problem. I believe there are many FOSS reasons for not downloading medibuntu packages, make that decision for yourself. I'm assuming you are running Hardy, if not make that change below as well.

```

sudo echo "deb http://packages.medibuntu.org/ hardy free non-free" >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libdvdcss2 w32codecs

```

I hope that helps you.

---

### Post by junglist313 on 2008-07-15
Having the same problems here. I have the medibuntu repositories installed, and have the latest version of libdvdcss. I notice this particularly on warner bros dvds like "V for Vendetta" and "The Matrix", but not exclusively. It seems to happen to me when changing chapters in a dvd. It will play the menus ok then the first chapter but freezes and crashes a few seconds before chapter 2 starts. If you choose a random chapter from the dvd menu it will play that chapter and then will crash in the same manner. If it makes a difference I have a lightscribe drive, am running hardy, and am using legit dvds.

---

### Post by mc4man on 2008-07-15
@ junglist313
Have you changed the launcher command for vlc? If not give it a shot. Right click applications -> edit menus -> expand sound and video on left side, on right side right click vlc -> properties and change the launcher comm from vlc %U to vlc %m.

Edit; %m is only good for ubuntu (not kubuntu)

---

### Post by junglist313 on 2008-07-16
The command currently says "wxvlc %F". What does that mean and why should I change it?

---

### Post by mc4man on 2008-07-16
I could find you a link that explains those parameters if you'd like. What it does mean is that vlc isn't going to navigate disks properly in dvd menu mode in some cases. %m is the best parameter to use, you really should change it to take that out of the equation if issues persist.
did you do an upgrade from 7.10? - wxvlc %F was what was used in 7.10

I'd use (for 8.04) just vlc %m   (note the space between vlc and %


[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

---

### Post by euchrid33 on 2008-07-20
I'm having the same problem, and changing the command to vlc %m doesn't make any difference.

---

### Post by chappejw on 2008-08-05
I have Hardy 8.04 and vlc also crashes when trying to play a dvd... changing the menu option from "vlc %U" to "vlc %m" did not fix anything it still crashes... I believe this is an issue with vlc not being able to deal with encrypted DVDs by default. Does anyone know how to add libdvdcss support for vlc?

---

### Post by chappejw on 2008-08-14
Easiest way to ensure VLC or Movie Player can play DVDs is to just install dvd::rip and make sure you get all of it's required dependencies which you will check in its interface. One or more of those dependencies will ensure you have DVD decryption available for VLC and Movie Player. I am not sure if this can help other players, but I know this helped me get VLC and Movie Player set up.

cheers... Jake

---

### Post by Agrajag27 on 2008-08-25
Jake, can you fill in the steps you did to get it working? Same problem here without a solution so far and I'm too new to Ubuntu to know what you did to install dvd::rip and it's dependencies.

---

### Post by chappejw on 2008-08-27
ok, if dvdrip is available via synaptic package manager, select and install. if not, get the latest from here...

**[http://exit1.org/dvdrip/doc/install.cipp#source_download](http://exit1.org/dvdrip/doc/install.cipp#source_download)**

...and unpack and install it.

[B]tar zxvf dvdrip-0.98.8.tar.gz
cd dvdrip-0.98.8/
sudo ./configure
sudo perl Makefile.PL[/B]

**make test**

if no errors occured with make test, go ahead and...

**make install**

...if all went well you now have DVD::rip installed

next open up the application and 

[B]edit > edit preferences

click the "check all settings" button
[/B]
[B][COLOR=Green]...met dependencies are in green

[COLOR=Red]...unmet dependencies are in red[/COLOR]
[/COLOR][/B]
use apt-get or synaptic package manager to get the unmet dependencies

once those are in place try your VLC and Movie Player with an encrypted DVD or original disc. Everything should be in working order including subtitles, chapters, special features etc...

Basically the only reason I installed DVD::rip was to ensure the right libraries or packages were installed to be able to decrypt DVDs for VLC & Movie Player. I was not sure what VLC needed in the way of libraries, but I thought some may be included with a DVD ripper.

Good luck...

---

### Post by chappejw on 2008-08-27
Sorry... in this following section I believe you can use either the **sudo ./configure** line or the **sudo perl Makefile.PL **I put both lines in by mistake.

------------------------------------------------
[COLOR=Red][B]tar zxvf dvdrip-0.98.8.tar.gz
cd dvdrip-0.98.8/
sudo ./configure
sudo perl Makefile.PL
[/B][/COLOR]------------------------------------------------

[COLOR=Red][COLOR=Black]either command will generate a Makefile, however I noticed the ./configure adds more options as shown by this diff....

monkey@zoo:~/Desktop/dvdrip-0.98.8$ diff   cfg.Makefile   perl.Makefile 
159c159,161
< MAN1PODS = bin/dvdrip
---
> MAN1PODS = bin/dvdrip \
>       bin/dvdrip-progress \
>       bin/dvdrip-splitpipe
651a654
>       bin/dvdrip-progress \
652a656
>       bin/dvdrip-splitpipe \
658c662,664
<         bin/dvdrip $(INST_MAN1DIR)/dvdrip.$(MAN1EXT) 
---
>         bin/dvdrip-progress $(INST_MAN1DIR)/dvdrip-progress.$(MAN1EXT) \
>         bin/dvdrip $(INST_MAN1DIR)/dvdrip.$(MAN1EXT) \
>         bin/dvdrip-splitpipe $(INST_MAN1DIR)/dvdrip-splitpipe.$(MAN1EXT) 
monkey@zoo:~/Desktop/dvdrip-0.98.8$


Hope that helps... [/COLOR][/COLOR][COLOR=Black]**dvdrip-0.98.8**[/COLOR][COLOR=Red][COLOR=Black] also has a good README...
[/COLOR][/COLOR]

---

