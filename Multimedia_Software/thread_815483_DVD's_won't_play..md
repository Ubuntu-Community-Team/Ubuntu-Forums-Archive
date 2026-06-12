---
title: "DVD's won't play."
date: 2008-06-01
forum: Multimedia Software
---

### Post by kf4tqj on 2008-06-01
I went to this page: [http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+codecs]("http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+codecs") and copied this to my terminal: sudo
apt-get remove icedtea-gcjwebplugin
openjdk-6-jre openjdk-6-jre-headless openjdk-decs6-jre-lib && sudo
apt-get install alsa-oss compizconfig-settings-manager faac faad
gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0
sun-java6-fonts sun-java6-plugin unrar w32co
After working through some errors and dependency problems I now get this:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package icedtea-gcjwebplugin is not installed, so not removed
Package openjdk-6-jre is not installed, so not removed
Package openjdk-6-jre-headless is not installed, so not removed
Package openjdk-6-jre-lib is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
alsa-oss is already the newest version.
compizconfig-settings-manager is already the newest version.
faac is already the newest version.
faad is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-pitfdll is already the newest version.
liblame0 is already the newest version.
sun-java6-fonts is already the newest version.
sun-java6-plugin is already the newest version.
unrar is already the newest version.
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kf4tqj@kf4tqj-desktop:~$
I'm still getting the same errors that I had when I started. Mplayer says it can't read from source and when opening a DVD with VLC, VLC shuts off. What am I doing wrong? The drive is new and plays CD's ok. The computer identifies it as: CD-RW/DVD+-RW Drive. The computer is a Dell with a 2.8 gig processor and a gig of ram.
Thanks,
Woody

---

### Post by ubuntu-freak on 2008-06-01
That's just Part 1 of my how-to, have you completed the DVD playback section in Part 4?
 
I installed Hardy 64-bit fresh on Friday just gone and DVDs work flawlessly.
 
Nathan

---

### Post by Morty007 on 2008-06-01
RO, I tried your post as well but no dice. In VLC, I click open dvd but nothing happens. In gxine, it plays the inital Warning/copyright intro but then stops after the end of that. :confused:

---

### Post by mc4man on 2008-06-01
> In VLC, I click open dvd but nothing happens
open vlc thru the terminal, then try a dvd and read / post the print out. The error messages are usually informative. 
To eliminate the most basic cause of no playback do you know if a region has been set on your drive? (if you've played commercial dvds on windows then it has probably been set)If you've only used linux and or open source players (vlc ect.) then it probably hasn't.

---

### Post by kf4tqj on 2008-06-02
I just opened VLC with the terminal and got a string of these 3 things repeated over and over untill I killed
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***

I don't understand what it's telling me.
It is a new drive and hasn't ever played a DVD. It will play CD's though.
Woody

---

### Post by mc4man on 2008-06-02
Install regionset
```
sudo apt-get install regionset
```
Then with a _dvd in the drive_ run regionset from the terminal,  Ex.of _set drive_
> doug@doug-desktop:~$ regionset 
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET     [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available:4 
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]: n
In your case it won't say set under type and there would be 5 user controlled resets .
Set it to your region (1)
Then go into home directory and open the .dvdcss folder (hidden folder) and delete any folders inside. Then try vlc from terminal again. If it continues to error out post the _complete _terminal print out, the beginning is as useful as end


edit :
REGION 1 -- USA, Canada
REGION 2 -- Japan, Europe, South Africa, Middle East, Greenland
REGION 3 -- S.Korea, Taiwan, Hong Kong, Parts of South East Asia
REGION 4 -- Australia, New Zealand, Latin America (including Mexico)
REGION 5 -- Eastern Europe, Russia, India, Africa
REGION 6 -- China

---

### Post by kf4tqj on 2008-06-02
Nathan,
    Of course you were right. Once I went further down that page and got to Playing DVD's I added the rest of the code to the terminal and let it do it's thing. Then it still didn't work, but it clicked in my head that this machine used to run Windows so I re booted it and then it worked just fine.
Many Thanks,
Woody

---

