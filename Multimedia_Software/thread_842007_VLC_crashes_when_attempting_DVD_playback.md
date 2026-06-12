---
title: "VLC crashes when attempting DVD playback"
date: 2008-06-26
forum: Multimedia Software
---

### Post by AtomicClock on 2008-06-26
Hey guys, I just recently started using Ubuntu due to the advice of a friend of mine, and of course I love it.
Today I felt like watching a DVD, but VLC can't seem to open it.
I tried removing and reinstalling, but to no avail. 

I'm trying to watch Planet Earth. Totem can play it, but it doesn't support the menus, which I need. When trying to open a disc from VLC, it just crashes and closes. If I right click the DVD and choose to open it via VLC, it just freezes and I have to force quit. I tried opening the DVD via the terminal and here's what I got:

```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: E2938
libdvdnav: DVD Serial Number: 36376412
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/zaven/.dvdnav/E2938.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00011fc5
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00011fc9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0001201a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00021665
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 1
*** Zero check failed in ifo_read.c:1604
    for pgcit->zero_1 = 0x2c64

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1608 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***

*** Zero check failed in ifo_read.c:648
    for pgc->zero_1 = 0x00dc

*** libdvdread: CHECK_VALUE failed in ifo_read.c:667 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:669 ***
*** for pgc->cell_position_offset != 0 ***

libdvdnav: ifoRead_PGCIT failed - CRASHING!!!
vlc: vm.c:206: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

```

Seems like there's a problem with libdvdnav, but I can't figure anything.

Any ideas?

---

### Post by mc4man on 2008-06-27
Why don't you try updating your libdvdcss2 to version 1.2.9 .
I'm watching disk 2 right now. Use medibuntu to update from. If it's not in your sources see here.
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: E2938
libdvdnav: DVD Serial Number: 36378164

```

---

### Post by wolfen69 on 2008-06-27
i would just completely remove (along with any config files) vlc, libdvdread and libdvdcss2. and just re-install them. it cant hurt. after you uninstall them, do sudo apt-get clean and sudo apt-get autoremove

also, i see alot of people here with totem related problems. i dont think it's coincidence. if you can live with another player, i say get rid of totem. ive had real good results with media after i uninstalled totem. but what do i know?

---

### Post by mc4man on 2008-06-27
Once you have dvd playback going on vlc, (do install totem-xine and switch it to the default totem choice. See prev. link for how) if you want to 'cover all the bases' then install a patched libdvdnav4. _Don't remove_ the current installed version.  
 Open system -> software sources -> third party .. and add one at a time 
```
deb http://tobias.rautenkranz.ch/debian stable/
```
```
deb-src http://tobias.rautenkranz.ch/debian stable/
``` reload and then run
```
wget -qO - http://tobias.rautenkranz.ch/tobias.rautenkranz.asc | sudo apt-key add -
```after that run
```
sudo apt-get install libdvdnav-ifo4
```

When you open vlc from terminal you should see this
> VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread patched to play DVDs with DVD-Movie-Protect
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: E2938

That will take care of some structured protected disks that are unplayable otherwise (fairly rare in region 1)

page describing and mplayer source patch
[http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)

---

### Post by AtomicClock on 2008-06-27
Hey, thanks mc4man! It works now! Although, I tried adding those software sources, but it said that it was missing a public key, or something. It still works, though, so I'm happy.
Thanks again, man!

---

### Post by mc4man on 2008-06-27
If you want try adding the key again - shouldn't really matter if you can install libdvdnav-ifo4, you may get message about unverified whatever, just ignore
> doug@doug-desktop:~$ wget -qO - [http://tobias.rautenkranz.ch/tobias.rautenkranz.asc](http://tobias.rautenkranz.ch/tobias.rautenkranz.asc) | sudo apt-key add -
[sudo] password for doug: 
OK   [COLOR="Red"]<-[/COLOR]


If you have any prob. with vlc from this point out make sure the launcher command is ```
vlc %m
```
 r. click applications -> edit menus -> expand sound and video on left -> r. on right side click vlc -> properties and change comm. to above

---

### Post by Shannon_VanWagner on 2009-08-09
I had installed the dvd playback functionality in Jaunty per the instructions at ubuntuguide.org and still couldn't play a particular DVD movie.

When I used VLC or Mediaplayer to play the movie, the picture was scrambled and the application would then crash.

What fixed it for me was to cd into ~/.dvdcss and then remove the directory with the DVD movie name(contains a bunch of cryptically named files in it). After that, the DVD movie played fine.

---

### Post by gary_emms on 2009-10-04
I've found an answer but don't understand why it works.
I found that both Totem and VLC crashed when I tried to play a DVD. In frustration I installed Mplayer. I can now play DVDs in Mplayer, but without sound, however both Totem and VLC now work properly.
I'm using 9.10 so it could be a bug.:confused:

---

