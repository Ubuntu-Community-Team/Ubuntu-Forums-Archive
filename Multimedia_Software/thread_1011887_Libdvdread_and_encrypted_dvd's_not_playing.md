---
title: "Libdvdread and encrypted dvd's not playing"
date: 2008-12-15
forum: Multimedia Software
---

### Post by ushills on 2008-12-15
I appear to have the problem with libdvdread that means that I cannot play certain commercial DVD's in my ubuntu boxes.  The disk mount but does'nt play in any applications such a mplayer, vlc etc.

I have google about the patch for libdvdread that corrects the issue with incorret ifo being reported.  

How do I apply this patch

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=460400]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=460400")

or update to the latest libdvdread.

Will this also allow me to import these dvd's to my mythbuntu box.

---

### Post by mc4man on 2008-12-15
There are several ways, what you really want is an updated or patched libdvdnav4
For players that use the systems libdvdnav just install the latest libdvdnav4. (vlc, totem players, ect.

You can use intrepid's libdvdnav4 on hardy

[http://packages.ubuntu.com/intrepid/libdvdnav4](http://packages.ubuntu.com/intrepid/libdvdnav4)

Or you can install libdvdnav4-ifo (a redirect from existing libdvdnav4
[http://tobias.rautenkranz.ch/debian/](http://tobias.rautenkranz.ch/debian/)

info page 
[http://tobias.rautenkranz.ch/libdvdread_ifo.html.en](http://tobias.rautenkranz.ch/libdvdread_ifo.html.en)

It's easier to just use the Intrepid updated one. Just do a direct download and installl, don't remove your current version, let Gdebi handle.



If you want to 'fix' mplayer then you have three choices

Patch dvdread in the source and compile as normal to use it's internal dvdnav

Patch is here
[http://tobias.rautenkranz.ch/03-udf.patch](http://tobias.rautenkranz.ch/03-udf.patch)

Build a dvdnav version of mplayer that uses the systems libdvdnav4 (in this case it's necessary to use these libdvdnav4, libdvdread4 and -devs

[http://packages.debian.org/experimental/libdvdnav4](http://packages.debian.org/experimental/libdvdnav4)

[http://packages.debian.org/experimental/libdvdread4](http://packages.debian.org/experimental/libdvdread4)

Or the easiest if you don't want to build - The _latest mplayer_ from rvm (smplayer) is built as a dvdnav version. Ck. here, you'll want to add his ppa to get proper packages

[http://ubuntuforums.org/showthread.php?t=917700&highlight=smplayer](http://ubuntuforums.org/showthread.php?t=917700&highlight=smplayer)


As a point of reference (on a 8.04 install
 I'm using libdvdnav4 4.1.3-1, libdvdread4 4.1.3-1 for use with a dvdnav version of mplayer (installed) and built, but not installed 0.9.x versions of vlc - run from source folder)
 
I still have libdvdread3 0.9.7-8 installed to run vlc 0.8.6 (installed

I'm coming to the conculsion that vlc 0.9.x isn't ready for prime time

Edit: if you use a dvdnav version of mplayer and want a gui frontend, then use smplayer, gmplayer can have issues with the dvdnav enabled mplayer

---

### Post by ushills on 2008-12-16
> **mc4man said:**
> 

Patch dvdread in the source and compile as normal to use it's internal dvdnav

Patch is here
[http://tobias.rautenkranz.ch/03-udf.patch](http://tobias.rautenkranz.ch/03-udf.patch)
yer

Can you advise how I do this step.

Also will this enable ripping of these dvd's also.

---

### Post by mc4man on 2008-12-16
If you want to patch dvdread then it's pretty simple, probably several ways.
 Go to the patch, select all, copy, and then paste into a new text file. Rename it <anything>.patch (I used patch.patch) 

Download your source and put the patch file in the libdvdread folder, then in terminal cd to that folder and run patch.

Ex.
> Checked out revision 28155.
doug@doug-desktop:~/mplayer6$ cd mplayer; cd libdvdread
doug@doug-desktop:~/mplayer6/mplayer/libdvdread$ patch -i patch.patch
patching file dvd_reader.c
Hunk #1 succeeded at 1391 (offset -2 lines).
Hunk #2 succeeded at 1464 (offset -2 lines).
patching file dvd_reader.h
patching file ifo_read.c
Hunk #1 succeeded at 110 (offset 4 lines).
Hunk #2 succeeded at 1667 (offset 4 lines).


This will allow playback of most x-protect style titles (but not all, protections always evolve.

As far as anything else if you can read a disk...

---

