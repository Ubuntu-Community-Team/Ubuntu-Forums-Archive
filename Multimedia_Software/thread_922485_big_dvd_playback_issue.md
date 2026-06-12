---
title: "big dvd playback issue"
date: 2008-09-17
forum: Multimedia Software
---

### Post by TheVelho on 2008-09-17
Hello,


I'm using a fresh install of Ubuntu Hardy. Everything works fine except DVD playback.

[LIST]
[*]DVDs mount correctly, I can see the title and the files
[*]I can see the movie menus on some DVDs
[*]I tried everything that was in the post-it section
[*]I tried so hard that I'm afraid I put a big mess in my install
[/LIST]

Any solution would be fine; I don't care if the DVDs work only with VLC and mplayer.

Totem says (in french): impossible to read from ressource

VLC says:
```
VLC media player 0.8.6e Janus
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: PARLE AVEC ELLE
libdvdnav: DVD Serial Number: bfb31b9a        
libdvdnav: DVD Title (Alternative): PARLE AVEC ELLE
libdvdnav: Unable to find map file '/home/omit/.dvdnav/PARLE AVEC ELLE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002b54
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00002b54)
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00026a15
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 4
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c :218 : ifoOpenNewVTSI:  L'assertion « 0 » a échoué.
Abandon

```
It looks like libdvdnav4 has a problem, I tried reinstalling it without success.


Thanks in advance!

---

### Post by mc4man on 2008-09-17
the first thing to get out of the way is if a region is set, see here, if it's set to region 2 good, exit out, if not set it to region 2

[http://ubuntuforums.org/showthread.php?t=868547&highlight=regionset](http://ubuntuforums.org/showthread.php?t=868547&highlight=regionset)

As far as libdvdnav4 some titles require either the new ver. or use of a patched ver.
For now I'd use the patched one, the new ver. (available from debian packages - lenny (testing) limits the error output in vlc.

Go here and follow instruction (add sources to system -> admin. -> software sources -> third party.) Don't  worry about the key error when reloading. Add the key from the terminal and then do the update and install of libdvdnav4-ifo
**Don't remove** current libdvdnav4

[http://tobias.rautenkranz.ch/debian/](http://tobias.rautenkranz.ch/debian/)

Try vlc again (before trying go to home dir. -> .dvdcss and shift/delete all the contents.

At some point you may want to change vlc's default launch command to vlc %m or make it default choice for dvd playback

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

If you get things going and want to add mplayer(gmplayer) as a default choice see here (on movies that need the new or patched libdvdnav4 mplayer must be compiled with a patched libdvdread, the libdvdnav4's mentioned above aren't used by mplayer

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by TheVelho on 2008-09-17
Thanks for your help.

Unfortunately, that didn't solve my problem, I get the same error message  with VLC.

---

### Post by mc4man on 2008-09-17
> Unfortunately.....
Unfortunate indeed.
There's no great mystery to dvd playback with vlc.(with the occasional exception of kubuntu.
 All that's typically needed is to install vlc, libdvdcss2 and provide a proper path to a mounted dvd video file system

Some people do benefit from downgrading libdvdcss2 to an earlier ver. (for 32 bit ubuntu

```
sudo /usr/share/doc/libdvdread3/install-css.sh
``` or if that errors
```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

You could also try with the *dvd in the driv*e this comm.

```
export DVDCSS_METHOD=title && vlc dvd://
```

It never hurts to delete .vlc in home dir. (settings go back to default

---

### Post by TheVelho on 2008-09-18
Thanks again. I tried what you proposed, and it still doesn't work. However, the problem has changed a bit :
  - some of the DVDs I could mount before don't even mount anymore;
  - some other DVDs *do* mount but VLC returns an "infinite loop error message" that looks like the following.
```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1419 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_a
```
All the DVDs I'm talking about are movie DVDs.

EDIT: oh, and mplayer dvd:// seems to work (with error messages), except that there is no sound and the picture is VERY buggy (black with strange sparse squares). At least it doesn't crash...

---

### Post by cj100570 on 2008-09-18
> **TheVelho said:**
> Hello,


I'm using a fresh install of Ubuntu Hardy. Everything works fine except DVD playback.

[LIST]
[*]DVDs mount correctly, I can see the title and the files
[*]I can see the movie menus on some DVDs
[*]I tried everything that was in the post-it section
[*]I tried so hard that I'm afraid I put a big mess in my install
[/LIST]

Any solution would be fine; I don't care if the DVDs work only with VLC and mplayer.

Totem says (in french): impossible to read from ressource

VLC says:
```
VLC media player 0.8.6e Janus
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: PARLE AVEC ELLE
libdvdnav: DVD Serial Number: bfb31b9a        
libdvdnav: DVD Title (Alternative): PARLE AVEC ELLE
libdvdnav: Unable to find map file '/home/omit/.dvdnav/PARLE AVEC ELLE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002b54
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00002b54)
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00026a15
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 4
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c :218 : ifoOpenNewVTSI:  L'assertion « 0 » a échoué.
Abandon

```
It looks like libdvdnav4 has a problem, I tried reinstalling it without success.


Thanks in advance!

This should solve your problems. Do a restart after issuing the following commands.

sudo aptitude install libdvdcss2
sudo /usr/share/doc/libdvdread3/./install-css.sh

---

### Post by mc4man on 2008-09-18
The error message your reporting is typical of when structure protection is present that libdvdread (dvdnav) can't handle. It doesn't seem possible that all of your titles have an advanced s.p. and if you installed libdvdnav4-ifo  then it's even more unlikely.
> 
some of the DVDs I could mount before don't even mount anymore; That is somewhat troubling, the players, libs, codes, ect. have *no impact* on a dvd file system mounting. That's *solely between the drive and Os.* (you can't discount the drive itself as the problem

Assuming the region's set and you've tried the patched dvdnav, the lower ver. of libdvdcss2 and the alternate way of extracting keys, then if you'd like, do this ( will create a fairly 'clear' environment

```
sudo aptitude purge vlc libdvdcss2 
```

If you want to start completely fresh add libdvdread3 to that list. (will remove libdvdnav4 , (& the -ifo one) mplayer, and some codec's, ect.
Then go into home and delete .vlc and .dvdcss if present

Go here and follow thru the instr.'s. 
At the bottom is a link to making vlc the default player, you don't have to do that but do set the launch command as described.

[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

If you want to re install the libdvdnav4-ifo (maybe hold off) you can simply go here, locate, and d. click on it.
/var/cache/apt/archives

Now if possible, find a *clean* dvd that was released at least 2 yrs. ago or if you can use a region 1 release even better. (this will eliminate structure protection issues that libdvdread (dvdnav) can't handle.
Give the dvd a try using vlc ->file -> open disk
When or if that fails (50-50) with the dvd in the drive run & post

```
sudo lshw -C disk
```

Obviously none of the above matters if the dvd doesn't mount.

---

### Post by Raymond Petit on 2008-09-18
Dear Velho,

     I have had problems with video playback myself.  After reading the forums I got the advice to download and install the following debian packages: libdvdcss2_1.2.9-1_i386.deb,libdvdplay0_1.0.0-1_i386.deb,libdvdread3_0.9.4-3_i386.deb,libdvdnav-4.1.2.  In addition, I installed the following debian package just to be safe:  w32codecs_20060611-0unofficialubuntu1_i386.deb.  I also plan to install these to as I like to use VLC as a backup if a DVD doesn't play properly in MPlayer.  Just google where to download the above packages and let the package installer do the rest.  I am a noob who is somewhat command line adverse although I like synaptic, I like the package installer much better.  I have had few problems since I installed these.  I even saved them to a pen-drive so I wouldn't have to search them out again when I updated from Gutsy-Gibbon.  If a dependecy is needed the package installer will tell you.  Good Luck!
         
                         R. Petit

---

### Post by TheVelho on 2008-09-18
Okay, I tried all this.

There is one (out of 5) DVD working perfectly. The others still don't work and VLC outputs:

```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread patched to play DVDs with DVD-Movie-Protect
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Voyage tokyo
libdvdnav: DVD Serial Number: c93e9a98        
libdvdnav: DVD Title (Alternative): Voyage tokyo
libdvdnav: Unable to find map file '/home/omit/.dvdnav/Voyage tokyo.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014c
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:1385
    for c_adt->zero_1 = 0xcdb7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1389 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_01_0.IFO).

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1389 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Found 0 VTS's
libdvdread: Elapsed time 0

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c*:218*:*ifoOpenNewVTSI:  L'assertion «*0*» a échoué.

```

All my DVD are zone 2 (even the working one).
Thanks again.

---

### Post by mc4man on 2008-09-18
> There is one (out of 5) DVD working perfectly
Then you are good as far as the player, libs ect.
Is this the title?
[http://www.amazon.fr/Voyage-%C3%A0-Tokyo-Chishu-Ryu/dp/B000M05W38](http://www.amazon.fr/Voyage-%C3%A0-Tokyo-Chishu-Ryu/dp/B000M05W38)
If so are the other 3 from this studio? G.C.T.H.V.

The error is showing an inability to read any of the .ifo's, why ?
It may be structure protection, mastering errors, stamping errors, phyical damage, some weakness in the drive, ect. 
Note that libdvdcss2 is not used to read the .ifo's so your cool there.

If you were to run this 
```
dd if=/dev/[COLOR="Red"]scd0[/COLOR] of=dvd.iso conv=noerror 
```

it would give some indication of whether structure protection was in place
( a *long series* of reported errors and very slow read speed,  (basically just copying the disk, with no decryption to an encrypted .iso

If you want to try adjust red if needed to match drive  (sudo lshw -C disk will show /dev/scd[COLOR="Red"]x[/COLOR]
Ctrl+c stops the command

edit : sorry had to adjust comm. to copy encryption but not fail on structure or other errors

---

### Post by TheVelho on 2008-09-20
I don't know what is the problem with the ifo stuff (I don't even know what ifo is, but the problem seems to be with ifo and libdvdnav according to error messages). Here is one more, from VLC, maybe that'll help:
```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread patched to play DVDs with DVD-Movie-Protect
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: PARLE AVEC ELLE
libdvdnav: DVD Serial Number: bfb31b9a        
libdvdnav: DVD Title (Alternative): PARLE AVEC ELLE
libdvdnav: Unable to find map file '/home/omit/.dvdnav/PARLE AVEC ELLE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Found 0 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c*:218*:*ifoOpenNewVTSI:  L'assertion «*0*» a échoué.
Abandon
```

Running the dd command you proposed yields:
```
dd: lecture de `/dev/scd0': Erreur d'entrée/sortie
44304+0 enregistrements lus
44304+0 enregistrements écrits
22683648 octets (23 MB) copiés, 1,43113 s, 15,9 MB/s
dd: lecture de `/dev/scd0': Erreur d'entrée/sortie
44304+0 enregistrements lus
44304+0 enregistrements écrits
22683648 octets (23 MB) copiés, 1,43571 s, 15,8 MB/s
dd: lecture de `/dev/scd0': Erreur d'entrée/sortie
44304+0 enregistrements lus
44304+0 enregistrements écrits
22683648 octets (23 MB) copiés, 1,44069 s, 15,7 MB/s
44304+0 enregistrements lus
44304+0 enregistrements écrits
22683648 octets (23 MB) copiés, 1,44093 s, 15,7 MB/s
```

Also I couldn't read "GCTHV" on the other DVDs so I guess they're not from the same studio. The working DVD comes from "SINFONIA distribution".

I don't have the non-mounting-DVD problem anymore.

---

### Post by Drakkor on 2008-09-22
Thanks, cj100570 that did solve all my problems,lol :)

---

### Post by cj100570 on 2008-10-28
> **Drakkor said:**
> Thanks, cj100570 that did solve all my problems,lol :)

Gld to have been helpful. :guitar:

---

