---
title: "Problems burning CD/DVD"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by camellochapin on 2007-04-16
I installed GnomeBaker to burn CD/DVD, it has an easy to use interface but after clicking on "Burn" I get the following error message:
> cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-11-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .


I read the > read /usr/share/doc/cdrecord/README.ATAPI.setup

and everything is OK with the burning device... but at the bottom it says:

> Only users who are in the group "cdrom" are able to burn CDs.

I made a group called CDROM in System->Administration->Users/Groups and still I get the same error.

Please guys, help me ... I am kind of a rookie->intermediate linux user.

---

### Post by pirothezero on 2007-04-16
do you know what sg0 is? Doesn't sound like a cd burner to me. 

Go to edit -> preferences -> devices, what does it say for node for your drive?

---

### Post by camellochapin on 2007-04-16
> **pirothezero said:**
> do you know what sg0 is? Doesn't sound like a cd burner to me. 

Go to edit -> preferences -> devices, what does it say for node for your drive?

Hi there, actually I was also surprised with that "sg0".  But according to GnomeBaker -> Preferences -> Devices, the CD-Burner which is found is:

 > MATSHITA DVD-RAM UJ-841S ID 1,0,0 /dev/sr0.

so where does this > /dev/sg0 comes from? how can I fix it?

---

### Post by pirothezero on 2007-04-16
Thats interesting I have my cdroms on /dev/scd0 and /dev/scd1 yet gnomebacker under node shows them as /dev/sr1 /dev/sr0 as well. Probably its a symbolic link. 

Then ya sounds like a permission problem. I don't know if this would help but you could try a chmod on /mnt/cdrom with 0777

```
sudo chmod 0777 /mnt/cdrom
``` or whatever your cdrom is called.

---

### Post by TimJBart on 2007-04-17
I have this exact same problem with my CD as **sg0**

It does not show up in /mnt   should it?

---

### Post by TimJBart on 2007-04-17
Found a possible solution in another thread:

Try opening a terminal and typing,

```
gksudo gnomebaker
```

to run it with root privileges.

It seems to be burning the disk now.

Incidently, the guy in the other thread who couldn't burn also had a CD at **sg0**

The reason I'm burning a CD is I am going to clean install Feisty!  Hope burning CDs works in that!

---

### Post by camellochapin on 2007-04-17
> **TimJBart said:**
> I have this exact same problem with my CD as **sg0**

It does not show up in /mnt   should it?

Hi there, I couldn't find a solution for this problem and I was told by a friend that the program "brasero" was a very good one... I found it with Synaptics, installed it and try to burn a CD and worked perfectly!

Solution for this problem:  uninstall GnomeBaker and install/use Brasero.  =D>

---

### Post by jakev383 on 2007-04-17
[http://www.ubuntuforums.org/showthread.php?t=217472&highlight=CD+burning](http://www.ubuntuforums.org/showthread.php?t=217472&highlight=CD+burning)
That worked for me when I had the exact same problem.

---

### Post by ububaba on 2007-04-18
When I paste this:[COLOR="Blue"]
read /usr/share/doc/cdrecord/README.ATAPI.setup[/COLOR]
in Terminal it simply waits and waits.  Nothing seems to be happening,

---

### Post by gmos on 2007-04-23
Regarding Gnomebaker on Feisty. I played with the Feisty beta version for couple of weeks before upgrading on Friday. Found that Gnomebaker was doing strange things eg, not recognising the cd drive, or not writing ISO image but finalising disc as if it did.

Nautilus cd/dvd functions all seem to work fine - right click and copy/burn with no problems or errors, and at a really good speed.

In this case it seems a problem with Gnomebaker under Feisty. So far, this is the only major problem encountered with the upgrade to Feisty.

---

### Post by Fraoch on 2007-04-24
> **gmos said:**
> Regarding Gnomebaker on Feisty. I played with the Feisty beta version for couple of weeks before upgrading on Friday. Found that Gnomebaker was doing strange things eg, not recognising the cd drive, or not writing ISO image but finalising disc as if it did.

Aha, well I'm not the only one then.

Tried to burn the Ubuntu install ISO.  It acted like it did:

> wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'CD-RW GCE-8523B '
Revision       : '1.03'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1951488 = 1905 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 5644 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 11702
Writing  time:    4.183s
Average write speed   1.0x.
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:    9.465s
BURN-Free was never needed.

(this was a later test run)  But the whole thing finished in about 10 seconds and it only wrote 1/16" of data on the CD.  Obviously no 680 MB ISO, and there's no readable data on the disc.  Coaster anybody?

Burned the ISO according to [this]("https://help.ubuntu.com/community/BurningIsoHowto") and it worked fine?

---

