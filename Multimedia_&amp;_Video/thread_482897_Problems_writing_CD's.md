---
title: "Problems writing CD's???"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by Chris Lappe on 2007-06-24
I am having a bunch of trouble writing CD's with Ubuntu. (I can read CD's and rip Music CD's fine)

At First every software package I tried would get to the "Preparing to write" stage and just sit there doing nothing.

K3B and Brasero both, and K3B would hang up the PC and I would have to reboot..

I then  installed "cdrskin" in K3B and made it the default writer.  Now instead of hanging up, when I try to burn a CD, K3B says. 

"Probably a buffer underrun occured"
"Please choose a lower burning spead"

I have tried all the way down to "1X" speed and get the same thing everytime.

The "Show Debugging output" says.

------------------------------------------------------------------------------------------------------------

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
CyberDrv CW058D CD-R/RW 13HD (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

K3bIsoImager
-----------------------
mkisofs print size result: 190 (389120 bytes)
Pipe throughput: 20480 bytes read, 0 bytes written.

Used versions
-----------------------
mkisofs: 1.1.2
cdrecord: 2.1-Emulation

cdrecord
-----------------------
cdrskin 0.2.2 : limited cdrecord compatibility wrapper for libburn
cdrskin: initializing libburn ... ok
cdrskin: NOTE : greying out all drives besides given dev='/dev/scd0'
cdrskin: scanning for devices ...
 done
cdrskin: NOTE : No usable drive detected.
cdrskin: HINT : Run this program as superuser with option --devices
cdrskin: HINT : Allow rw-access to the dev='...' file of the burner.
cdrskin: HINT : Busy drives are invisible. (Busy = open O_EXCL)
cdrskin: NOTE : ignoring unimplemented option : '-multi'
cdrskin: NOTE : option is waiting for a volunteer to implement it.
cdrskin: NOTE : ignoring unimplemented option : '-xa1'
cdrskin: NOTE : option is waiting for a volunteer to implement it.
cdrskin: FATAL : cannot find '/dev/scd0' among accessible drive devices.
cdrskin: HINT : use option  --devices  for a list of drive devices.
cdrskin: verbosity level : 1

-----------------------------------------------------------------------------------------------------------------------

Anyone know what I can do to fix this????

---

### Post by Pygi on 2007-06-24
Hello Chris,

From your post I got the impression that you are running feisty. Since feisty doesn't have newer cdrskin/libburn, and 0.2.2 is seriously outdated, I'd ask you to install newest cdrskin/libburn from:
[libburnia]("http://libburnia-project.org"): [http://files.libburnia-project.org/releases/libburn-0.3.6.tar.gz](http://files.libburnia-project.org/releases/libburn-0.3.6.tar.gz)

Please try, and report if that fixes your problem.

Kind regards,
Mario

---

### Post by Chris Lappe on 2007-06-24
Thanks Mario, I downloaded it and when I got to "Make Install" I got this message

make[1]: Entering directory `/home/jeff/Desktop/libburn-0.3.6'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ./libtool --silent --mode=install /usr/bin/install -c  'libburn/libburn.la' '/usr/local/lib/libburn.la'
/usr/bin/install: cannot create regular file `/usr/local/lib/libburn.so.4.1.1': Permission denied
make[1]: *** [install-libLTLIBRARIES] Error 1
make[1]: Leaving directory `/home/jeff/Desktop/libburn-0.3.6'
make: *** [install-am] Error 2


Do I need to run "Make Install" as root?

---

### Post by Pygi on 2007-06-24
Hey,

yes, please run "sudo make install" :)

KR,
M.

---

### Post by Chris Lappe on 2007-06-24
I did and it seems to have install, without any error messages, but when I try to burn a CD I am still getting the same messages.

"Probably a buffer underrun occured"
"Please choose a lower burning spead"

drskin 0.2.2 : limited cdrecord compatibility wrapper for libburn
cdrskin: initializing libburn ... ok
cdrskin: NOTE : greying out all drives besides given dev='/dev/scd0'
cdrskin: scanning for devices ...
cdrskin: NOTE : No usable drive detected.
cdrskin: HINT : Run this program as superuser with option --devices
cdrskin: HINT : Allow rw-access to the dev='...' file of the burner.
cdrskin: HINT : Busy drives are invisible. (Busy = open O_EXCL)
cdrskin: NOTE : ignoring unimplemented option : '-multi'
cdrskin: NOTE : option is waiting for a volunteer to implement it.
cdrskin: NOTE : ignoring unimplemented option : '-xa1'
cdrskin: NOTE : option is waiting for a volunteer to implement it.
cdrskin: FATAL : cannot find '/dev/scd0' among accessible drive devices.
cdrskin: HINT : use option  --devices  for a list of drive devices.
 done
cdrskin: verbosity level : 1

HELP!!!!!
 
If it helps, my CD-R Drive is a CyberDrv CWO58D

---

### Post by Pygi on 2007-06-24
Hey,

please calm down :)

Please try the following with libburn-0.3.6 tarball:

./configure --prefix=/usr
make
sudo make install

Make cdrskin default in k3b and try burning.

KR,
M.

---

### Post by Chris Lappe on 2007-06-24
> **Pygi said:**
> Hey,

please calm down :)

Please try the following with libburn-0.3.6 tarball:

./configure --prefix=/usr
make
sudo make install

Make cdrskin default in k3b and try burning.

KR,
M.

That seems to be making progress, but it still isn't writing.

K3B gave me...

"Using Cdrecord 2.1 Emulation"
"Starting TAO writing at 32X speed"

But after 5 minutes it still wasn't actually writing to the disk.

The debug report says

cdrecord
-----------------------
cdrskin 0.3.6 : limited cdrecord compatibility wrapper for libburn
cdrskin: verbosity level : 1
cdrskin: NOTE : greying out all drives besides given dev='/dev/sr0'
cdrskin: scanning for devices ...
cdrskin: NOTE : ignoring unimplemented option : '-xa1'
cdrskin: NOTE : option is waiting for a volunteer to implement it.
cdrskin: NOTE : Enforcing minimum track size of 614400 bytes
cdrskin: ... scanning for devices done
cdrskin: beginning to burn disc
cdrskin: status 1 burn_disc_blank "The drive holds a blank disc"
Track 01: data     0 MB        
Total size:        0 MB (00:06.00) = 300 sectors
Lout start:        0 MB (00:08/00) = 300 sectors
Starting to write CD/DVD at speed 32 in real TAO mode for multi session.
Last chance to quit, starting real write in   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
UNIX-SIGNAL:  SIGTERM  errno= 2
cdrskin: ABORT : Handling started. Please do not press CTRL+C now.
cdrskin: ABORT : Trying to ignore any further signals
cdrskin: ABORT : Drive is released and library is shut down now.
cdrskin: ABORT : Program done. Even if you do not see a shell prompt.

cdrecord command:
-----------------------
/usr/bin/cdrskin -v gracetime=2 dev=/dev/scd0 speed=32 -tao driveropts=burnfree -eject -multi -xa1 -tsize=190s - 

mkisofs
-----------------------
190
I: -input-charset not specified, using utf-8 (detected in locale settings)
Total translation table size: 0
Total rockridge attributes bytes: 251
Total directory bytes: 366
Path table size(bytes): 10
Max brk space used 0
190 extents written (0 MB)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Fossey -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jeff/k3b4L1YWa.tmp -rational-rock -hide-list /tmp/kde-jeff/k3bzrkTEa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-jeff/k3bsFypDa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-jeff/k3b1j8jub.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Fossey -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jeff/k3bz8y5sa.tmp -rational-rock -hide-list /tmp/kde-jeff/k3b4KO7Ra.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-jeff/k3bFG0Jfc.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-jeff/k3bYiNxzb.tmp

---

### Post by Pygi on 2007-06-24
What exactly are you trying to write?

---

### Post by Chris Lappe on 2007-06-24
> **Pygi said:**
> What exactly are you trying to write?

Data files, I plan to make CD backups of some files.

On another Linux forum, I saw someone report this exact same problem awhile back and they were told to do this command 

"cdrecord -scanbus -dev=ATAPI"

I ran it on mine and got.

wodim: ERROR: unknow subsystem (scd0) in (/dev/sr0)
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

I ran "wodim --devices" and got:

Beginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (1 found) :
----------------------------------------------------------------------
0    dev='/dev/sr0'   rwrw-- :  'CyberDrv'  'CW058D CD-R/RW'
----------------------------------------------------------------------

Then ran "wodim -scanbus" and got:

scsibus1:
        1,0,0   100) 'CyberDrv' 'CW058D CD-R/RW  ' '13HD' Removable CD-ROM
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

PS, I want to stop a second to thank you for your help, don't think it's not appreciated!

---

### Post by Chris Lappe on 2007-06-25
Been working on this again, I can now use K3B to write .iso files to CD and make music CD's from MP3's, but it still hangs when trying to make DATA CD's.

??????? :D

---

### Post by Pygi on 2007-06-26
Great, we've got ya going. About the data cd....
I suspect it's a k3b/genisoimage problem.

KR,
M.

---

