---
title: "Cd not mounting into /media"
date: 2009-09-07
forum: Multimedia Software
---

### Post by Esthellin on 2009-09-07
I want to rip music off the cd I have. Pop it into the tray and it can be played through VLC. However, I can't see it in the /media folder. I have looked in the cdrom0 folder and nothing is there. I went to Computer and opened the audio disc, and it opens in the location "cdda://sr0/". Any idea why the audio disc is not appearing in the /media folder (eg being mounted)? I have tried setting the mount point for the drive to be /media/cdrom0 but to no avail.

Note: It is a CD-RW/DVD+-RW drive on a Toshiba laptop. Dvd's mount correctly (into a separate folder in /media).

---

### Post by HappyFeet on 2009-09-07
All you need to do is install either Soundjuicer, Asunder, Grip, or Ripperx to rip music from a cd. You can find those in synaptic package manager.

---

### Post by bogdan.veringioiu on 2009-09-08
Hi.

Audio cd's will not be mounted probably, as they not contain normal (usual) data. You will only be able to play them, or rip them.
You will see mounted only the cd's/dvd's containing data (mp3, videos, etc).

Cheers.

---

### Post by Esthellin on 2009-09-09
The cd contained music files made by iTunes I think. Perhaps the format of the cd was in cd audio format rather than as a data disc.

I checked with a data disc, that had MP3 files on it. This appeared in a separate folder in the /media folder, but still nothing appeared under cdrom or cdrom0.
N.B. I noticed there was a link withint the root filesystem, linking to the cdrom folder in /media. Why is their one in this directory? Doesn't make sense. The fact that the link cdrom within the /mediafolder points directly to the folder next to it also seems pointless.

Thoughts?

---

### Post by LostinSpacetime on 2009-10-03
I have the same problem. I was always using foobar2000 for riping audio cds. After upgrading to 9.04 audio cds arn't mounted in /media/cdrom0 any more and wine applications cannot recognize any audio cds. Please post any solutions since this is quite annoying.

Thanks!

---

### Post by Esthellin on 2010-11-04
> mount /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

> dmesg | tail

[ 3487.953088] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 3487.953102] end_request: I/O error, dev sr0, sector 2496
[ 3487.953249] UDF-fs: No anchor found
[ 3487.953254] UDF-fs: No partition found (1)
[ 3488.131378] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3488.131391] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 3488.131403] Info fld=0x10
[ 3488.131407] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 3488.131421] end_request: I/O error, dev sr0, sector 64
[ 3488.131479] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

[---]

Something about an illegal mode when trying to open a track on the cd. (as in track with sectors not an audio track).

Google searched did not come up with anything useful.

---

### Post by ezsit on 2010-11-04
I don't know about other people, but audio CDs don't mount for me, never have. I play them and rip them with ripperx and asunder all the time. I just thought that audio CDs normally do not mount. It's never been a problem playing or ripping them. There are decent native linux cd rippers, why use Wine and Windows apps?

Asunder
RipperX
Soundjuicer
K3B
KaudioCD
Rhythmbox

Probably a half dozen more that I can't think of.

---

### Post by Esthellin on 2010-11-04
> **ezsit said:**
> I don't know about other people, but audio CDs don't mount for me, never have. I play them and rip them with ripperx and asunder all the time. I just thought that audio CDs normally do not mount. It's never been a problem playing or ripping them. There are decent native linux cd rippers, why use Wine and Windows apps?

Asunder
RipperX
Soundjuicer
K3B
KaudioCD
Rhythmbox

Probably a half dozen more that I can't think of.

Thankyou very much for the reply. I just installed RipperX. It rips the cd's beautifully. And best of all, you can set what the file name is and turn off folder creation. Very handy. And it is easy to add in track info, both manually and with the cddb function.

A note to uses of this program: you need to install an mp3 encoder (such as lame) before mp3 encoding works. Don't use twolame (or toolame) as it doesn't encode mp3 files, only mp2. 

Should this thread be marked as solved? Technically, we couldn't mount the cd's, but we did solve the purpose of the mounting, e.g to burn cd's easily. Ill see if I can change the thread name to a more useful one.

EDIT: It looks like that the thread names can only be changed by moderators. Could a moderator please change the thread to "[SOLVED] burning cd's - need to mount into /media ?"?

---

### Post by Esthellin on 2010-11-04
See below for reasons behind not mounting audio cds and a program to get around it.
[http://www.linuxforums.org/forum/red-hat-fedora-linux/54232-mount-audio-cd.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/54232-mount-audio-cd.html)

Also the following link under 4.5. Mounting, Unmounting, and Ejecting Devices
[http://www.faqs.org/docs/Linux-HOWTO/CDROM-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/CDROM-HOWTO.html)

They don't explain much, but the main idea I think is that audio cd's shouldn't be mounted, due to the way the tracks are stored on the system. But data cd's can be mounted because they are...well...data, so they have filesystem structure on the system that can be mounted onto Linux and viewed.
Ill add more if I find anything else.

EDIT:It seems I was pretty close: [http://www.linuxconfig.org/HowTo_mount_cdrom_in_linux](http://www.linuxconfig.org/HowTo_mount_cdrom_in_linux) in the section 5. Mounting Audio CD's

---

