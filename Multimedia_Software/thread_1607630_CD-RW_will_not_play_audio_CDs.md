---
title: "CD-RW will not play audio CDs"
date: 2010-10-28
forum: Multimedia Software
---

### Post by Bulletproofmask on 2010-10-28
Hello all.

I recently attached a CD-RW to my computer and have been unable to get it to recognize audio CDs.  Data disks work fine and an icon appears under Places and in /media, but inserting a standard music CD only makes my CD-RW icon disappear until the CD is ejected.

I have spent most of my day searching the forums and the rest of the web and have found other threads relating the same problem, but I have not found much along the lines of a solution.  

The audio CDs all work fine on a DVD drive that is also in use by the computer.  I am running 64bit Lucid Lynx.

---

### Post by Bulletproofmask on 2010-10-28
Here is the output for sudo lshw without an audio CD

```
 *-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW RW121032E
                vendor: CREATIVE
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc

```And this is it with an audio CD

```
 *-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW RW121032E
                vendor: CREATIVE
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1

```dmesg gives me a bunch of errors as the CD-RW tries to read the audio CD

```
[ 8344.775476] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8344.775479] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8344.775481] Info fld=0x0
[ 8344.775482] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8344.775486] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 8344.775491] end_request: I/O error, dev sr0, sector 0
[ 8344.776078] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8344.776081] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8344.776083] Info fld=0x0
[ 8344.776085] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8344.776088] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 8344.776093] end_request: I/O error, dev sr0, sector 0
[ 8344.776666] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8344.776669] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8344.776671] Info fld=0x0
[ 8344.776673] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8344.776676] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 8344.776681] end_request: I/O error, dev sr0, sector 0
[ 8344.777390] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8344.777392] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8344.777395] Info fld=0x0
[ 8344.777396] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8344.777399] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 8344.777405] end_request: I/O error, dev sr0, sector 0
[ 8344.777992] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8344.777994] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8344.777997] Info fld=0x0
[ 8344.777998] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8344.778001] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 8344.778007] end_request: I/O error, dev sr0, sector 0

```

---

### Post by drpjkurian on 2010-10-28
Hi Iam not sure but the I/O error is related to bad burning of the CD. So please copy the files from the CD on an another machine to a new cd. I am sure the newly burnt CD will definitely work in UBUNTU

---

### Post by Bulletproofmask on 2010-10-28
Thanks for the response.  None of the CDs I am trying are burned, they're just normal store-bought albums.

---

### Post by Bulletproofmask on 2010-11-02
Has anybody here had this problem, or have have any suggestions?

---

### Post by ezsit on 2010-11-02
Is there some copy-protection built into the CDs you just bought? Try older music CDs that you know to have worked in the past.

---

### Post by Bulletproofmask on 2010-11-04
I just went through my CDs and tested about 10 more in the CD Drive, and was met with the same results on each(icon disappeared from Places, CD does not show up in Banshee).  The CD's I'm using are just normal store-bought albums which I've had for years.

I noticed something else which may be important, however.  I've never checked Nautilus when playing audio discs in the DVD Drive because they have always worked without issue.  I do get an error message when I insert a disc into the DVD Drive:

**Unable to mount Audio Disc**

Location is not mountable



But again, the DVD Drive is able to read and play Audio CDs while the CD Drive is not.

---

### Post by mc4man on 2010-11-04
audio cd's don't get mounted (no filesystem to mount) but are accessed at a location. 

While I can no longer be too precise, did notice issues with a CREATIVE cd/cdrw drive, either staring in lucid or maverick (forget which,, dropped lucid for maverick in May.

As I remember, (replaced the drive due to the issues and because it was old), as soon as some discs were inserted the drive would disappear. (maybe just audio cd's, possibly others.

You could try - first restart to clear any failed operation concerning the drive, then insert an audio disc in the creative drive,  browse to home folder (view -> show hidden files),  look in .gvfs and see if there is a folder - 'cdda mount on sr[COLOR="Blue"]X[/COLOR]'

If you see that folder than you should be able to play thru a player - either from it's gui or cli using a /dev link for the drive
Ex. vlc - if creative is /dev/sr0
```

vlc cdda:///dev/sr0
```

Overall I found it better to dump the drive and add a second dvd drive

---

### Post by Bulletproofmask on 2010-11-05
Hi, Mc4man.  I remember reading your responses to some of the threads regarding similar CD Drive problems, and you are clearly very knowledgeable about the subject.  Earlier today I was restarting my computer in preparation to follow your advice, when my brother suggested I upgrade from 10.4 to 10.10 to see if that would have any positive effect on the issues I have been experiencing.

It did.  The CD Drive now seems to be functioning exactly as the DVD Drive does.  

There is still a problem, however.  It appears that I was wrong about the error message 'Unable to mount Audio Disc' only occurring through Nautilus.  The error message has been appearing every time I put an audio disc into the DVD Drive today(before the upgrade as well as after) and now the CD Drive generates the same error with audio discs.  Furthermore, I have to close and reopen Banshee in order for it to recognize the CD(whether it's in the CD Drive or DVD Drive).  

This is a better situation than the drive not being able to read audio CDs at all, but something must still be wrong.  Is Ubuntu trying to mount the CDs because it thinks they have valid filesystems on them?

---

### Post by Bulletproofmask on 2010-11-08
OK, my DVD Drive and my CD Drive both seem to be working properly now.  I found [this post]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/609020?comments=all") on Launchpad and installed 'gvfs-backends'.  That did the trick.  Thanks everyone who read or responded.

---

### Post by cntmn8td2006 on 2011-02-08
> **Bulletproofmask said:**
> OK, my DVD Drive and my CD Drive both seem to be working properly now.  I found [this post]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/609020?comments=all") on Launchpad and installed 'gvfs-backends'.  That did the trick.  Thanks everyone who read or responded.

Installing  'gvfs-backends' through the "Ubuntu Software Center" worked for me.

---

