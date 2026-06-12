---
title: "Can't create multisession DVD+R with growisofs"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by ewanchic on 2008-02-07
I am using a server installation of Gutsy 7.10. There is no GUI.
I'm trying to do a simple multisession test on a DVD+R.
I got this information from the man pages: [http://linux.die.net/man/1/growisofs]("http://linux.die.net/man/1/growisofs")

The basic idea is to:
Step 1 - Start the first track
> growisofs -Z /dev/dvd -R -J /some/files
Step 2 - Append each additional track
> growisofs -M /dev/dvd -R -J /more/files
Step 3 - Close the Disk
> growisofs -M /dev/dvd=/dev/zero

Here is what's happening:
-------------------------

Step 1 - Start the first track:
> 
root@ubunutu:/media/sdc1/backups/rt/2008/02# growisofs -Z /dev/hda -R -J /media/sdc1/backups/rt

Executing 'genisoimage -R -J /media/sdc1/backups/rt | builtin_dd of=/dev/hda obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Unexpected joliet directory length 110 expected: 114 ''
/dev/hda: "Current Write Speed" is 16.4x1352KBps.
 54.76% done, estimate finish Thu Feb  7 10:57:36 2008
Total translation table size: 0
Total rockridge attributes bytes: 676
Total directory bytes: 4448
Path table size(bytes): 32
Max brk space used 0
9151 extents written (17 MB)
builtin_dd: 9152*2KB out @ average 1.1x1352KBps
/dev/hda: flushing cache
/dev/hda: closing track
/dev/hda: closing session


Now this worked...I think. My drive's light stayed on...forever? So I unmounted it but there was noting to unmount? So I hit the but. After a couple red flashes of the light, the DVD popped out. I popped it into my Windows drive, it showed up as blank. I placed it back into my ubuntu drive and mounted it...that worked and i could read it. So i unmounted the DVD and continued on with Step 2.

Step 2 - Append each additional track:
I moved an existing file out of the current directory and into another: /media/sdc1/backups/rt/2008/02/ rt.2008.02.06.tgz , and added a new file:  /media/sdc1/backups/rt/2008/02/ rt.2008.02.07.tgz 
> 
root@noah:/media/sdc1/backups/rt/2008/02# growisofs -M /dev/hda -R -J /media/sdc1/backups/rt
Executing 'genisoimage -C 16,11200 -M /dev/fd/3 -R -J /media/sdc1/backups/rt | builtin_dd of=/dev/hda obs=32k seek=700'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Rock Ridge signatures found
Using 000;1 for  /.. (..)
genisoimage: Error: '/..' and '/media/sdc1/backups/rt/..' have the same Rock Ridge name '..'.
Unable to sort directory
:-( genisoimage has failed: 1


I've looked through this forum, and on google with no avail. I hope there is somewhat out there that can help with this issue. Thanks.

---

### Post by ewanchic on 2008-02-11
Some additional things to add.

I've been studying K3B to see how they create a muslitsession DVD+R. It worked. I was able to burn a single track that was readable by Windows. And then a second track that it too was readable by windows. Works Good.

So I'm analyzing K3B debuging output to study what is done to create these multisession burns. It looks to me like genisoimage is the program that does most of the dirty work of setting up Rock Ridge, Joliet, the file pathes, etc, and then rely on growisofs to actually burn the image to CD.

I am going to contact the developers of cdrkit and see if I can get some better direction.

---

### Post by cjpetrie on 2008-04-08
The first time I have tried to use Gutsy for growisofs -M, I got the same problem:
Rock Ridge signatures found
Using 000;1 for  /.. (..)
genisoimage: Error: '/..' and 'unsaved/..' have the same Rock Ridge name '..'.
Unable to sort directory 
:-( genisoimage has failed: 1

---

### Post by ewanchic on 2008-04-08
I'm glad some else is looking :)

Well.. I did my research...and it took some months.

Too make a long story short, genisoimage won't work. Period. One of their developers informed me (or at least someone from their forum) that their software is old and outdated, and due for major upgrade for a couple of months/years now. ](*,)  I apparently stumbled upon one of their own bugs. :confused: nice. 

So. moving along, the original cdrecord by Joerg Schilling himself, which is still update and kept strong, isn't exactly written to burn multi-session (or, as he corrected me, multi-border) DVDs, or more specifically DVD+Rs because the code is not compatible  across all platforms. bummer.

However, there is hope. :guitar:

Thomas Schmitt has developed a super-awesome program called "xorriso". It's not designed with the iso/image/track idea. Instead you treat it like a true backup program, backing up files, moving files around in different directories, removing files, etc, as each additional track is burned. 

There are some refreshing issues, but it gets the tracks burned and that's what's important to me. I'm actually hoping to help out with that at some point. Anyway... here is the install file:

There is a xorriso release tarball (containing the application
and all three libburnia libraries needed):
  [http://scdbackup.sourceforge.net/xorriso-0.1.2.pl00.tar.gz](http://scdbackup.sourceforge.net/xorriso-0.1.2.pl00.tar.gz)

For more info, see [http://scdbackup.sourceforge.net/xorriso_eng.html](http://scdbackup.sourceforge.net/xorriso_eng.html)
                   [http://scdbackup.sourceforge.net/man_1_xorriso.html](http://scdbackup.sourceforge.net/man_1_xorriso.html)


Now for the ubuntu install version (^_^)
--------------------------------------------------------
Step 1: Get build Essentials
```
apt-get install build-essential
```

Step 2: Pick a place to download. I personally choose /usr/catalog/xorriso. Modify to your own usage.
```

mkdir -p /usr/catalog/xorriso
cd /usr/catalog/xorriso
wget http://scdbackup.sourceforge.net/xorriso-0.1.2.pl00.tar.gz

```

Step 3: Download xorriso
```
wget http://scdbackup.sourceforge.net/xorriso-0.1.2.pl00.tar.gz
```

Step 4: Uncompress xorriso
```
tar -xvf xorriso-0.1.2.pl00.tar.gz
```

Step 5: Configure, Compile, and install
```

cd xorriso-0.1.2
./configure
make
make install

```

Step 5: Read and Use
All you need to do is call xorriso from the prompt. Execute ```
man xorriso
``` for more information, or For more info, see [http://scdbackup.sourceforge.net/xorriso_eng.html](http://scdbackup.sourceforge.net/xorriso_eng.html) and [http://scdbackup.sourceforge.net/man_1_xorriso.html](http://scdbackup.sourceforge.net/man_1_xorriso.html)


\\:D/ Have Fun!

---

