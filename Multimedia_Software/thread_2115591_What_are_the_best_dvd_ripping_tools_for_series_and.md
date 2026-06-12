---
title: "What are the best dvd ripping tools for series and films?"
date: 2013-02-13
forum: Multimedia Software
---

### Post by The_Reaper on 2013-02-13
I've a lot of dvd's and series. I wan't to Rip the films to avi files (xvid) and series to mp4 (h264).

I tried DVDFab for films and Handbrake for series both on windows.
I saw that Handbrake is for ubuntu too, but DVDFab not.

What are the best programas for lubuntu/ubuntu to rip dvd films and series?

---

### Post by bryanl on 2013-02-13
Handbrake, of course.

ogmrip ([http://ogmrip.sourceforge.net](http://ogmrip.sourceforge.net)) seems to be a decent alternate. You could examine what this does and go directly to command line and tweak for utmost control but the GUI approach simplifies things greatly and does an adequate job.

gddrescue, the GNU data recovery tool, is also useful if you have DVD's that are a bit difficult to read. This is run from the command line as, for example 'ddrescue /dev/sr0 -r 3 -b 2048 dvd.iso dvd.ddrlog' - then you can feed the iso to ogmrip or mount the iso (right click on icon to choose the proper open option) to feed to handbrake.

do make sure you've loaded ubuntu restricted extras to install the necessary codecs and run /usr/share/doc/libdvdread4/install-css.sh to enable DVD decrypting (of course, do be knowledgable about laws in your particular area regarding copying and decrypting)

handbrake has a ppa and the other two are in the repositories

---

### Post by The_Reaper on 2013-02-14
> **bryanl said:**
> Handbrake, of course.

ogmrip ([http://ogmrip.sourceforge.net](http://ogmrip.sourceforge.net)) seems to be a decent alternate. You could examine what this does and go directly to command line and tweak for utmost control but the GUI approach simplifies things greatly and does an adequate job.

gddrescue, the GNU data recovery tool, is also useful if you have DVD's that are a bit difficult to read. This is run from the command line as, for example 'ddrescue /dev/sr0 -r 3 -b 2048 dvd.iso dvd.ddrlog' - then you can feed the iso to ogmrip or mount the iso (right click on icon to choose the proper open option) to feed to handbrake.

do make sure you've loaded ubuntu restricted extras to install the necessary codecs and run /usr/share/doc/libdvdread4/install-css.sh to enable DVD decrypting (of course, do be knowledgable about laws in your particular area regarding copying and decrypting)

handbrake has a ppa and the other two are in the repositories

Thanks for your help.

---

### Post by evilsoup on 2013-02-14
Make sure that you use the version of HandBrake from [this PPA](https://launchpad.net/~stebbins/+archive/handbrake-releases), since the version in the 12.10 repositories is crippled.

> 
I wan't to Rip the films to avi files (xvid)


Why? H.264 in an MP4 will give you better quality at a given bit rate (or a smaller bit rate for a given quality) every time.

---

### Post by nonviolent on 2014-01-11
FWIW here is the script I use to backup my purchased DVDs.  
I put a dvd in my drive, use a keystroke launcher to run 'dvd2iso', and the resulting iso is placed in my home folder. 
For some DVD sets that have a common name I need to move/rename the .iso before I rip the next disk, or it will be overwritten. 

```

#!/bin/bash
# Create a damn backup of a dvd

outdir=dvd$RANDOM
outiso=iso$RANDOM
vlc dvd:///dev/sr0 --play-and-exit &
vlcpid=$!
sleep 13 && kill $vlcpid
ddrescue -n -b 2048 /dev/sr0 $outiso
eject /dev/sr0
dvdbackup -M -i $outiso -o $outdir
rm -rfv $outiso
first=$(find $outdir/ -maxdepth 1 -type d|tail -n 1)
second=$(basename "$first")
cd $outdir
mkisofs --dvd-video -o ../"$second".iso "$second"
cd ..
rm -rfv $outdir

```

If you have any questions, please. Don't ask.

- Z

---

### Post by VMC on 2014-01-12
> **evilsoup said:**
> Make sure that you use the version of HandBrake from [this PPA]("https://launchpad.net/~stebbins/+archive/handbrake-releases"), since the version in the 12.10 repositories is crippled.... I agree. You don't know its crippled until you install the ppa, or unless you've used it in the past.

---

### Post by andrew.46 on 2014-01-13
If you are interested in the comandline you would only need a handful of tools to get the job done. For example vobcopy to rip the dvds to disk (assuming you own the dvds) and then FFmpeg will handle all of the rest...

---

