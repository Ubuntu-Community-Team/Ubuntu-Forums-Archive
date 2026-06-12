---
title: "DVD data files read only"
date: 2007-11-23
forum: Multimedia Production
---

### Post by alfreddo on 2007-11-23
Having been used to Nero burning software on the PC I am trying to use GnomeBaker and k3b on my KDE desktop.

If I burn data files to DVD using either of these programs, then open them in OpenOffice wordprocessor, they open as 'read only' and cannot be  modified. The menus don't seem to give an option of choosing read/write before burning.

Second, having got this result using GnomeBaker, I reformatted the DVD using k3b before burning more files. When I looked at the disk in OpenOffice, the Gnomebaker files were still there as well as the k3b files, so the disk can't have been formatted.

Would It be simpler to purchase the Linux version of Nero?

---

### Post by LaRoza on 2007-11-23
It would be easier to use a flash drive. RW disks are flakey in my experience, especially when used in more than one comptuer/OS

---

### Post by alfreddo on 2007-11-23
Looking at the properties of my DVD+RW drive (Philips DVDRW 1208) I find that 'read' is ticked. When I try to add 'write' I get the message: 'Sorry, couldn't change the permissions of 'CD-RW/DVD+RW Drive: Gnomebaker Data Disk.'

The DVD drive used to work perfectly when I had Windows installed on the machine, but it seems partially disabled now - eg there doesn't seem to be an option in the software for burning DVD-Video movies to disk, only read-only data files. Presumably the device driver is at fault. I'll see if Philips have a Linux driver available.

Any other suggestions ? An alternative driver perhaps? Or a DVD rewriteable drive that is known to work with Ubuntu ?

---

### Post by pietjanjaap on 2007-11-24
If you burn a data dvd then you are not able to save the file again, yes it is read only, and yes you are using a RW dvd. This because you made a data dvd, these are read only.

look for something like "packet writing"
Not very safe for files!!!!!!!


    * Rainbow Books
    * File systems
          o ISO 9660
                + Joliet
                + Rock Ridge
                      # Amiga Rock Ridge extensions
                + El Torito
                + Apple ISO9660 Extensions
          o Universal Disk Format
                + Mount Rainier

Packet writing is an optical disc recording technology used to allow writeable CD and DVD media to be used in a similar manner to a floppy disk. Packet writing allows the user to access the contents of a CD-R or CD-RW disc directly through a mounted filesystem (Unix, Linux, Mac OS X) or drive letter (Windows). Without packet writing software, one would have to use regular CD mastering recording software to burn a whole disc.

Packet writing can be used both with once-writeable media such as CD-R, DVD+R and DVD-R, and also with rewriteable media such as CD-RW, DVD+RW and DVD-RW. Once-writeable media cannot however recover space once used; A deleted file does not free space on the disk, and a modified or overwritten file occupies additional space even if the file size has not increased. When the free space on a once-writeable disk is exhausted, no further update to the disk is possible. Rewriteable (RW) media can have all the files deleted on a formatted disc, or information can be overwritten. The downside is CD-RW will fade to the point it isn't readable as the re-crystalized alloy de-crystalizes. Formatted CD-RWs seem to fade out faster than unformatted CD-RWs. [citation needed] People who assume RW media can be updated and reformatted many times just like a floppy disk eventually discover that their data has disappeared. And there are only so many times it can be completely erased and reused - it varies from disc to disc, and can vary with age and use. [citation needed]

Several competing and incompatible packet writing disk formats have been developed, notably those of Roxio Drag-To-Disc (formerly DirectCD), Nero AG InCD, and Sonic Solutions Drive Letter Access. Proposed standards include UDF 1.5 and Mount Rainier.

---

### Post by alfreddo on 2007-11-24
Thanks for clarifying the matter of packet writing software. Points taken.

I also want to burn DVD-Video files - by which I mean a VIDEO-TS folder containing about 10 files with file endings such as .bup and .vob, which when burned to a DVD can be played on a standalone DVD player or a computer. I can do this easily using Nero on Windows. 

I have GnomeBaker v.0.6.0 installed on my Ubuntu PC. In the help files under the heading 'future' is listed 'creating video DVDs'.

K3b doesn't seem to offer video DVD as a burning option either.

Does any suitable Ubuntu program capable of burning video DVDs yet exist, or is it something we have to look forward to in the future ?

Or am I missing something (won't be the first time)

---

### Post by pietjanjaap on 2007-11-25
K3b can burn video dvd.

Look in de pulldown of the program.
Go to "file", then "new project"



You can make a big button in the middle yourself.

---

### Post by alfreddo on 2007-11-25
OK.  Found File -- New Project -- burn Video DVD.

transferred video files into the Video-TS folder in K3b. Total size 2,8GB
Inserted formatted 4.7GB disk in drive.
Clicked on 'burn'. Got error message:

Found media: no media
Please insert an empty Double
Layer DVD+R medium
into drive.
Philips DVDRW1208 (dev/hdc)

Clicked on 'force'.  Got this message:

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-29-386
Devices
-----------------------
PHILIPS DVDRW1208 1.34 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD+RW] [DVD-ROM; DVD+RW; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R96R]

K3b
-----------------------
Size of filesystem calculated: 1477623

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
:-[ READ DISC INFORMATION failed with SK=3h/ASC=57h/ACQ=00h]: Input/output error

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1477623 -dvd-compat -speed=1.5 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
/usr/bin/X11/mkisofs: Warning: -follow-links does not always work correctly; be careful.
Warning: Disabling Joliet support for DVD-Video.
/usr/bin/X11/mkisofs: Warning: -follow-links does not always work correctly; be careful.
Warning: Disabling Joliet support for DVD-Video.
1477623
/usr/bin/X11/mkisofs: Warning: -follow-links does not always work correctly; be careful.
Warning: Disabling Joliet support for DVD-Video.
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-alfred/k3bNNBaNa.tmp -rational-rock -hide-list /tmp/kde-alfred/k3bM3pOic.tmp -joliet -hide-joliet-list /tmp/kde-alfred/k3bE9bnnb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-alfred/k3bIu62tb.tmp -dvd-video -f /tmp/kde-alfred/k3bVideoDvd0 


Does this make any sense ?

---

### Post by alfreddo on 2007-11-28
I've just tried to burn a Video-DVD again, using k3b, and it worked - no problems at all. A little slower than Windows - 15 minutes for a 2.8 GB file as opposed to 12 minutes - but that doesn't matter. 

I used a Sony DVD+RW disk formatted first on my Panasonic DVD recorder. The result played back faultlessly.

Weird...

---

