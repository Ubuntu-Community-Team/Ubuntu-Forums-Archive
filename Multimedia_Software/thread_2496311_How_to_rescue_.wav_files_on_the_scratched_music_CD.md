---
title: "How to rescue .wav files on the scratched music CD."
date: 2024-03-23
forum: Multimedia Software
---

### Post by satimis on 2024-03-23
Hi all,

I found several music CDs having scratches on them.  They can neither be detected nor be mounted.  Then I clean them with toothpaste.  Now they can be detected on DVD-Writer and mounted.  On File-manager all music tracks, .wav format, are displayed but I could nether play them on VLC media player nor copy them to the storage drive.

On Google search cdda2wav and cdparanoia are suggested as the tool for recovering tracks on audio CD.  

On Terminal;
$ apt policy cdda2wav```

cdda2wav:
  Installed: (none)
  Candidate: (none)
  Version table:

```

$ apt policy cdparanoia```

cdparanoia:
  Installed: 3.10.2+debian-14build2
  Candidate: 3.10.2+debian-14build2
  Version table:
 *** 3.10.2+debian-14build2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```
cdparanoia is already installed but I have no knowledge running it.

Please shed me some lights.  Alternatively other suggestions are also welcomed.

Thanks in advance.

Regards

---

### Post by Dennis N on 2024-03-23
If you have .wav files stored on a CD, then it has a file system and isn't an audio CD (which doesn't). So utilities that read audio CDs will not help here. My guess is that you probably have to use other data recovery tools that are used to recover data on HDDs or SDDs. I haven't used any myself, so someone who is familiar with these tools hopefully will suggest what to use.

---

### Post by The Cog on 2024-03-24
> If you have .wav files stored on a CD, then it has a file system and isn't an audio CD
But a file manager can sure make it look like .wav files. I just tried (I admit I'm on Mint not Ubuntu right now) a real CD (Smashie and Nicey's Lets Rock) and clicked it in Nemo file manager. It showed up looking full of .wav files. Double-clicking a track played in in my default audio player, and drag-dropping a track to the desktop dropped a .wav file. The conversion seemed to be performed by a gvfs-cdda process which was high in cpu usage while "copying" the file, and exited when I ejected the disk.

I gather from distant memory that cdparanoia is best at reading scratched CDs, with a wide range of retry options. I don't remember the details many years later, but that's the one I suggest you read up on.

---

### Post by satimis on 2024-03-24
> **The Cog said:**
> But a file manager can sure make it look like .wav files. I just tried (I admit I'm on Mint not Ubuntu right now) a real CD (Smashie and Nicey's Lets Rock) and clicked it in Nemo file manager. It showed up looking full of .wav files. Double-clicking a track played in in my default audio player, and drag-dropping a track to the desktop dropped a .wav file. The conversion seemed to be performed by a gvfs-cdda process which was high in cpu usage while "copying" the file, and exited when I ejected the disk.

I gather from distant memory that cdparanoia is best at reading scratched CDs, with a wide range of retry options. I don't remember the details many years later, but that's the one I suggest you read up on.
Thanks for your advice.

What you said is correct if the music CD is without problem.

I'm now copying/duplicating all my music CDs to hard-drive.  Please see my another posting below;

About ripping music CD to mp3 files
[https://ubuntuforums.org/showthread.php?t=2496103](https://ubuntuforums.org/showthread.php?t=2496103)

I found 4 music CD disks having problem unable to play on my Onkyo CD Deck.  They are also unable to work on my DVD-writer.

Regards

---

### Post by Dennis N on 2024-03-24
OK, you got my attention.

I looked at this just now with a retail audio CD. When inserted in a DVD drive, a lot of reading goes on and "Audio disc" appears in "Places" menu. When I selected that, Files opens and shows .wav files which surprised me. I copied one .wav to my main drive, and it plays in my Linux music player.

I looked at mount to see if the cd is mounted, and the gvfs thing is being used. 

[dmn@Sydney gvfs]$ ls
'cdda:host=sr0'

I'm pretty sure that years ago this would not work. **It raises the question, why do we need a ripper application if we can just read and copy the tracks with the file manager?** (the ripper would find the titles in the cddb, though - Files does not do that.)

Also noticed, Disks does not show any partitions or file system on the audio cd, but sees it as "Media: audio cd rom disk"

Many years ago, we backed up files by making a "data CD" which required a disc burner to create. I put a known data CD of miscellaneous files made with Win XP in 2003. Still fine after 20 years! It shows in Disks as "Media: CD-R disc" and mounts under /media/<user-name> like any other removable drive, but according to Disks, this disc has a file system of type Isofs, Brasero still has the option for "Data CD" project.

Interesting stuff.

Good luck with your data rescue!

---

### Post by TheFu on 2024-03-24
Sometimes badly scratched CDs cannot be read. That's the hard truth.  I have a few.  Usually, it isn't the whole disc IME, but I certainly need a new copy of Van Halen II. ;(  There must be 2 files that skip on that disc and I've never gotten a copy off.

---

### Post by satimis on 2024-03-24
Hi all,

Up to now I have duplicated/copied 62 Music CDs on the storage hard drive without problem.  Only those 4 music CDs with scratches have problem.

Steps performed;
1. Play the music CD on Onkyo CD deck.  If no problem
2. Mount the Music CD on DVD-Writer of computer with;
- Insert the Music CD
- Mount the music CD with;
- Right-click Audio Disc icon -> select "New Window"
- After a while File Manager will pop-up, displaying all tracks on the music CD```

Track 1.wav
Track 2.wav
Track 3.wav
Track 4.wav
...
...
etc

```
- select all tracks with mouse-pointer and drag->paste them to the storage folder

It works without failure except having scratches on the music CD.

The copied tracks can be played on VLC media player seamlessly.

Now I have to search a new CD disk and burn the tracks for checking.  If I can't find new CD disk on shelves, can I use a Re-Write CD for testing?

Another question where is the mount point of the Audio CD?

Regards

---

### Post by Dennis N on 2024-03-24
> cdparanoia is already installed but I have no knowledge running it.
Look at the man page of cdparanoia. That has all the options and what they do.
Or look at cdparanoia --help

---

### Post by satimis on 2024-03-24
> **Dennis N said:**
> Look at the man page of cdparanoia. That has all the options and what they do.
Or look at cdparanoia --help
Thanks.  I'll check it later.

Do you know where is the mount point of the CD disk/DVD-Writer if mount GUI (via its icon) ?

I found following discovery is very useful in editing the .txt file showing the contents of all CDs tracks.  If typing them manually it'll take lengthy time to finish.

There are many "image to text" online websites. Take a photo of those information on the printed box of the CD with mobile phone.  Upload the photo to their websites to convert the photo/image to text.  Then copy&paste the text to the .txt file

Regards

---

### Post by TheFu on 2024-03-24
To see mount points, use either the **lsblk** command or **df -Th**.
Beware that some "fake" mounts will be shown and sometimes gio/gvfs mounts don't get shown at all - i.e. fake.

---

### Post by Dennis N on 2024-03-24
> Do you know where is the mount point of the CD disk/DVD-Writer if mount GUI (via its icon) ?
I used the mount command and saw this line:
```
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```
Then:
```
dmn@Sydney:~$ ls /run/user/1000/gvfs
'cdda:host=sr0'

```
so I can tell this is for the optical drive.

You can look up gvfs on Google to get information. Too technical for me.

BTW,
 
**df -Th** did not show anything on this connection.
and
**lsblk -o name,mountpoint** does not give a mount point for sr0. That column is blank for this device.

(Using Ubuntu 23.10)

---

### Post by Yellow Pasque on 2024-03-24
> **Dennis N said:**
> It raises the question, why do we need a ripper application if we can just read and copy the tracks with the file manager?
Technically, you dont, but .wav's take up more space than FLAC, and aren't as friendly to tag.

---

### Post by satimis on 2024-03-24
> **Dennis N said:**
> I used the mount command and saw this line:
```
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```
Then:
```
dmn@Sydney:~$ ls /run/user/1000/gvfs
'cdda:host=sr0'

```
so I can tell this is for the optical drive.

You can look up gvfs on Google to get information. Too technical for me.

BTW,
 
**df -Th** did not show anything on this connection.
and
**lsblk -o name,mountpoint** does not give a mount point for sr0. That column is blank for this device.

(Using Ubuntu 23.10)
Thanks for your advice.

For both working Audio Disc and problem Audio Disc

$ sudo mount /dev/sr0 /mnt/cdrom```

mount: /mnt/cdrom: can't read superblock on /dev/sr0.

```

Why ?

Regards

---

### Post by satimis on 2024-03-24
> **TheFu said:**
> To see mount points, use either the **lsblk** command or **df -Th**.
Beware that some "fake" mounts will be shown and sometimes gio/gvfs mounts don't get shown at all - i.e. fake.
Thanks

It is very strange.

File Manager shows all tracks of the problem Audio Disc but no mount point could be found. Please see attached screenshots
screenshot_df-Th.png
screenshot_file_manager.png

I couldn't play the tracks running VLC Media Play.  The PC will freeze if playing any track.

But checking a working Audio Disc with "df-TH", also no mount point is found.  Please see attached screenshot;
screenshot_df-Th_working_audio-disc.png

Regards

---

### Post by Yellow Pasque on 2024-03-25
> **satimis said:**
> File Manager shows all tracks of the problem Audio Disc but no mount point could be found. 
...
But checking a working Audio Disc with "df-TH", also no mount point is found. 

That is expected. Again, audio CD's do not have filesystems that mount normally. The system is using gvfs to make it look like a data CD. You can look  at:
```
gvfs-mount
```

---

### Post by satimis on 2024-03-25
> **Yellow Pasque said:**
> That is expected. Again, audio CD's do not have filesystems that mount normally. The system is using gvfs to make it look like a data CD. You can look  at:
```
gvfs-mount
```
Hi,

Thanks for your advice.

$ gvfs-mount /dev/sr0 /mnt/cdrom/```

gvfs-mount: command not found

```

$ sudo gvfs-mount /dev/sr0 /mnt/cdrom/```

sudo: gvfs-mount: command not found

```

$ apt policy gvfs-common```

gvfs-common:
  Installed: 1.48.2-0ubuntu1
  Candidate: 1.48.2-0ubuntu1
  Version table:
 *** 1.48.2-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1.48.1-4 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main i386 Packages

```

But gvfs-common already installed

Regards

---

### Post by tea for one on 2024-03-25
> gvfs-mount has been deprecated and it is redirected to gio mount
[https://manpages.ubuntu.com/manpages/focal/en/man1/gvfs-mount.1.html](https://manpages.ubuntu.com/manpages/focal/en/man1/gvfs-mount.1.html)

Using Ubuntu 22.04 and external usb dvd reader.
Commercial audio CD recognised and available with Files (Nautilus)
```
edited@edited-22-04:~$ gio list cdda://sr0
Track 1.wav
Track 2.wav
Track 3.wav
Track 4.wav
Track 5.wav
Track 6.wav
Track 7.wav
Track 8.wav
Track 9.wav
edited@edited-22-04:~$
```

---

### Post by satimis on 2024-03-25
> **tea for one said:**
> [https://manpages.ubuntu.com/manpages/focal/en/man1/gvfs-mount.1.html](https://manpages.ubuntu.com/manpages/focal/en/man1/gvfs-mount.1.html)

Using Ubuntu 22.04 and external usb dvd reader.
Commercial audio CD recognised and available with Files (Nautilus)
```
edited@edited-22-04:~$ gio list cdda://sr0
Track 1.wav
Track 2.wav
Track 3.wav
Track 4.wav
Track 5.wav
Track 6.wav
Track 7.wav
Track 8.wav
Track 9.wav
edited@edited-22-04:~$
```
Hi,

Thanks for your advice.

$ which gio```

/usr/bin/gio

```

mount music CD disc GUI
right-click music CD disc ICON -> Mount

$ gio list cdda://sr0```

Track 1.wav
Track 2.wav
Track 3.wav
Track 4.wav
Track 5.wav
Track 6.wav
Track 7.wav
Track 8.wav
Track 9.wav
Track 10.wav

```

Can I mount music CD disc on Terminal?

Regards

---

### Post by satimis on 2024-03-25
Hi all,

Performed following test on the music CD disc having problem to play .wav files and fail to copy .wav files to hard drive

1. Insert the music CD disc
2. Mount music CD GUI
3. 
$ gio list cdda://sr0```

Track 1.wav
Track 2.wav
Track 3.wav
Track 4.wav
Track 5.wav
Track 6.wav
Track 7.wav
Track 8.wav
Track 9.wav
Track 10.wav
Track 11.wav
Track 12.wav

```

$ mkdir ~/Downloads/Test_folder

$ ls -ald ~/Downloads/Test_folder```

drwxrwxr-x 2 satimis satimis 4096 Mar 25 19:05 /home/satimis/Downloads/Test_folder
```

But how to copy all .wav files on ~/Downloads/Test_folder  ?

Thanks in advance

Regards

---

### Post by Yellow Pasque on 2024-03-25
There's probably a way to copy the tracks like files with gvfs, but you are doing this the hard way. Use a ripper like k3b. It will check the disc for errors with libcdparanoia, convert from .wav to whatever format you want, and automatically name and tag the files for you. Or you can just rip to unnamed, untagged .wav files if that's really what you want for some reason.

---

### Post by satimis on 2024-03-25
> **Yellow Pasque said:**
> There's probably a way to copy the tracks like files with gvfs, but you are doing this the hard way. Use a ripper like k3b. It will check the disc for errors with libcdparanoia, convert from .wav to whatever format you want, and automatically name and tag the files for you. Or you can just rip to unnamed, untagged .wav files if that's really what you want for some reason.
If the music CD disc is working without problem of scratches, I can copy all track.wav files with copy&paste command seamlessly.  This is a damaged music CD disc.  I can't do it in the same way..

Performed following test:-
$ cd ~/Downloads/Test_folder/

$ abcde -a cddb,read,encode,tag,move,clean -d /dev/cdrom \
> -j 4 -o flac,vorbis:"-q 6" -V -x
```

.....
.....
.....
5: Il corsaro: Atto terzo. "Eccomi prigionero!" (Corrado)
6: Il corsaro: Atto terzo. "Ei dorme?" (Gulnara, Corrado)
7: Il corsaro: Atto terzo. "Seid la vuole ... Non sai tu che sulla testa" (Gulnara, Corrado)
8: Il corsaro: Atto terzo. "Sul capo mio discenda" (Corrado, Gulnara)
9: Il corsaro: Atto terzo. "La terra, il ciel m'abborino..." (Gulnara, Corrado)
10: Il corsaro: Atto terzo. "Voi tacete..." (Medora, Gulnara, Corrado, ancelle, corsari)
11: Il corsaro: Atto terzo. "Per me infelice" (Corrado, Medora, Gulnara, ancelle, corsari)
12: Il corsaro: Atto terzo. "O mio Corrado, appressati" (Medora, Corrado, Gulnara, ancelle, corsari)
[End] q 

```

$ ls ```

abcde.8f09d70c

```

$ ls abcde.8f09d70c/```

asin.1       cddbdiscid   cddbquery.2  data-musicbrainz  mbdiscid  status
asin.2       cddbquery    cddbread.1   datasource.1      mbid.1
cddbchoices  cddbquery.1  cddbread.2   datasource.2      mbid.2

```

I'm stuck here.

Regards

---

### Post by Yellow Pasque on 2024-03-25
> **satimis said:**
> If the music CD disc is working without problem of scratches, I can copy all track.wav files with copy&paste command seamlessly.  This is a damaged music CD disc.  I can't do it in the same way..

If it won't automatically mount with gvfs like other music CD's and you can't rip it, then the disc is probably damaged too badly, especially if a normal CD player can't read it. Even if you get the right gvfs mount command, it's not going to work in that case. I hope I'm wrong, but good luck..

---

### Post by Dennis N on 2024-03-25
How it works (to the best of my knowledge):

A ripper works one track at a time using location information in the CD's table of contents (TOC). If the TOC of the CD is damaged, the start bit of tracks may not be readable. So it can't be ripped. There is no fix. If you bought the CD, You need to get a replacement.

---

### Post by satimis on 2024-03-25
> **Dennis N said:**
> How it works (to the best of my knowledge):

A ripper works one track at a time using location information in the CD's table of contents (TOC). If the TOC of the CD is damaged, the start bit of tracks may not be readable. So it can't be ripped. There is no fix. If you bought the CD, You need to get a replacement.
This is an old music CD

OK

Let me try a working music CD disc first.

What command shall I execute to copy all output of
$ gio list cdda://sr0

to a folder after | command

Thanks

---

### Post by Dennis N on 2024-03-25
If it's a good playable CD, then I have only used the GUI ripper/encoders. For example, asunder. It has a preferences dialog with all the encoder settings, like destination, encoding format (mp3, aac, flac, etc), quality, and the format for what the file names look like. I can't advise on the gio thing you show.

If it's important to replace, being old doesn't mean you can't find another for sale on the internet. New or used.

---

### Post by TheFu on 2024-03-25
You might try using **ddrescue** to create an image of the CD on disk.  **ddrescue** (gddrescue package name) will keep trying to get all the data is can, assuming the device can be seen by the OS.  Let it have 5+ passes to try. If it finishes, then it thinks it got the data/iso.  Then you cal look up the specific _loop_ **mount** required to open it for ripping.  The resulting file is like pointing at a real disc device.

This is just a lead. I can't provide exact commands or steps. Sorry.  I've never used it with a music CD, but I have used it with data disks that also had 10% par2 files. It worked well enough that no data was lost.

---

### Post by tea for one on 2024-03-25
Try this (although my CD was not damaged)
It will copy all the tracks.
```
cp -r /run/user/1000/gvfs/cdda:host=sr0 ~/Downloads/Test/
```
N.B. Your destination folder has a slightly different name.

If this is unsuccessful, more advice here [https://forums.linuxmint.com/viewtopic.php?t=316604](https://forums.linuxmint.com/viewtopic.php?t=316604)

---

### Post by satimis on 2024-03-25
> **tea for one said:**
> Try this (although my CD was not damaged)
It will copy all the tracks.
```
cp -r /run/user/1000/gvfs/cdda:host=sr0 ~/Downloads/Test/
```
N.B. Your destination folder has a slightly different name.

If this is unsuccessful, more advice here [https://forums.linuxmint.com/viewtopic.php?t=316604](https://forums.linuxmint.com/viewtopic.php?t=316604)
For good music CD disc

$ cp -r /run/user/1000/gvfs/cdda:host=sr0 ~/Downloads/Test_folder_3/

$ ls Downloads/Test_folder_2/```

'cdda:host=sr0'

```

$ ls Downloads/Test_folder_2/cdda\:host\=sr0/```

'Track 10.wav'  'Track 15.wav'  'Track 1.wav'   'Track 24.wav'  'Track 6.wav'
'Track 11.wav'  'Track 16.wav'  'Track 20.wav'  'Track 2.wav'   'Track 7.wav'
'Track 12.wav'  'Track 17.wav'  'Track 21.wav'  'Track 3.wav'   'Track 8.wav'
'Track 13.wav'  'Track 18.wav'  'Track 22.wav'  'Track 4.wav'   'Track 9.wav'
'Track 14.wav'  'Track 19.wav'  'Track 23.wav'  'Track 5.wav'

```

For damaged music CD disc
It can be mounted

On File-manager:
It also shows all track .wav files

$ mkdir ~/Downloads/Test_folder_3
$ cp -r /run/user/1000/gvfs/cdda:host=sr0 ~/Downloads/Test_folder_3/
It holds there for prolonged time, no files copied.

Regards

---

### Post by Dennis N on 2024-03-26
cdrdao (see the link in post #27 by tea for one) looks like it is a utility that would help in recovery when the TOC has errors. It's new to me and I'm making note of it if ever needed. I suggest you try what is done there. It's probably already installed (see below). So there is a way to possibly recover the music, but the original CD will never play again. All you can do is burn a new CD once all the music is recovered.

_Possible useful utilities for your task:_
 
```

brasero/mantic 3.12.3-2 amd64
  CD/DVD burning application for GNOME

cdrdao/mantic,now 1:1.2.4-3 amd64 [installed,automatic]
  records CDs in Disk-At-Once (DAO) mode

cue2toc/mantic 0.4-5.1 amd64
  converts CUE files to cdrdao's TOC format

```

---

### Post by satimis on 2024-03-26
> **Dennis N said:**
> cdrdao (see the link in post #27 by tea for one) looks like it is a utility that would help in recovery when the TOC has errors. It's new to me and I'm making note of it if ever needed. I suggest you try what is done there. It's probably already installed (see below). So there is a way to possibly recover the music, but the original CD will never play again. All you can do is burn a new CD once all the music is recovered.

_Possible useful utilities for your task:_
 
```

brasero/mantic 3.12.3-2 amd64
  CD/DVD burning application for GNOME

cdrdao/mantic,now 1:1.2.4-3 amd64 [installed,automatic]
  records CDs in Disk-At-Once (DAO) mode

cue2toc/mantic 0.4-5.1 amd64
  converts CUE files to cdrdao's TOC format

```
Non of them installed here

post #27 is for Linux Mint.  I'm now working on Ubuntu 22.04.  I don't know whether the steps work here?

---

### Post by tea for one on 2024-03-26
> **satimis said:**
> Non of them installed here
post #27 is for Linux Mint.  I'm now working on Ubuntu 22.04.  I don't know whether the steps work here?
Post 29 from Dennis N suggests a good way forward.

Brasero, cdrdao and cue2toc are in the 22.04 universe repository
Insert your CD > Open brasero > Disc copy > Select a disc to write to > Image File > Properties (to choose your destination folder)
The Disc copy operation will output two files:-
Audio Disc.toc
Audio Disc.toc.bin
Have a look at the audio disc.toc (table of contents) and see if there is any corruption/missing details.

cdemu is an active project and is available via a ppa  [https://launchpad.net/~cdemu/+archive/ubuntu/ppa](https://launchpad.net/~cdemu/+archive/ubuntu/ppa)

I'm almost tempted to damage a CD and give this a go :)

---

### Post by satimis on 2024-03-26
> **tea for one said:**
> Post 29 from Dennis N suggests a good way forward.

Brasero, cdrdao and cue2toc are in the 22.04 universe repository
Insert your CD > Open brasero > Disc copy > Select a disc to write to > Image File > Properties (to choose your destination folder)
The Disc copy operation will output two files:-
Audio Disc.toc
Audio Disc.toc.bin
Have a look at the audio disc.toc (table of contents) and see if there is any corruption/missing details.

cdemu is an active project and is available via a ppa  [https://launchpad.net/~cdemu/+archive/ubuntu/ppa](https://launchpad.net/~cdemu/+archive/ubuntu/ppa)

I'm almost tempted to damage a CD and give this a go :)

Performed following test

1. Install Brasero
2. Insert the damaged music CD
3. Start Brasero -> Copy a CD > select the damaged music CD

It just hangs on screen without much progress.  Please see attached screenshot;
screenshot_copying_cd.png

Finally I have to cancel it.

Mount the damaged music CD (GUI).  File manager show all track .wav files.  Please see attached screenshot

Regards

---

### Post by tea for one on 2024-03-26
Which option did you select?
It should be "Create Image" as attachment.
Yes, it is slow and may take longer than listening to the CD itself - possibly depends on how much damage the CD has suffered.

You still have the terminal option using [COLOR="#0000FF"]cdrdao[/COLOR] (as detailed in the link from post 27)?

---

### Post by Dennis N on 2024-03-26
> It just hangs on screen without much progress. Please see attached screenshot; Finally I have to cancel it.
It would be nice to see Brasero give an error message. You may be more likely to see one with the cdrdao command. I decided to check it out. There were several command options, but I used it to make a backup copy of a CD in two steps:

In terminal change to a working directory first. Then,
1) make an data file of the source CD and a TOC file (this step is what Brasero was doing, I think)
```
cdrdao read-cd --datafile mytest.bin mytest.toc
```
At this point, you can pause and examine the TOC for anomalies. It's a text file.
I continued to make a copy of my disk.
2) from the same working directory, write a copy to a blank CD-R
```
cdrdao write mytest.toc
```

If step 1 fails as yours did with Brasero, you may get some error message with this utility. At least you can monitor the progress.

_Some other rescue tools that look  relevant to your task:_

```
ddrescueview/mantic 0.4.5-1 amd64
  graphical viewer for GNU ddrescue map files

ddrutility/mantic 2.8-4 amd64
  set of data recovery utilities for use with GNU ddrescue

forensics-extra/mantic,mantic 2.49 all
  Forensics Environment - extra console components (metapackage)

gddrescue/mantic 1.27-1 amd64
  GNU data recovery tool

myrescue/mantic 0.9.8-3 amd64
  rescue data from damaged disks

safecopy/mantic 1.7-7 amd64
  data recovery tool for problematic or damaged media
```

---

### Post by satimis on 2024-03-26
> **Dennis N said:**
> It would be nice to see Brasero give an error message. You may be more likely to see one with the cdrdao command. I decided to check it out. There were several command options, but I used it to make a backup copy of a CD in two steps:

In terminal change to a working directory first. Then,
1) make an data file of the source CD and a TOC file (this step is what Brasero was doing, I think)
```
cdrdao read-cd --datafile mytest.bin mytest.toc
```
At this point, you can pause and examine the TOC for anomalies. It's a text file.
I continued to make a copy of my disk.
2) from the same working directory, write a copy to a blank CD-R
```
cdrdao write mytest.toc
```

If step 1 fails as yours did with Brasero, you may get some error message with this utility. At least you can monitor the progress.

_Some other rescue tools that look  relevant to your task:_

```
ddrescueview/mantic 0.4.5-1 amd64
  graphical viewer for GNU ddrescue map files

ddrutility/mantic 2.8-4 amd64
  set of data recovery utilities for use with GNU ddrescue

forensics-extra/mantic,mantic 2.49 all
  Forensics Environment - extra console components (metapackage)

gddrescue/mantic 1.27-1 amd64
  GNU data recovery tool

myrescue/mantic 0.9.8-3 amd64
  rescue data from damaged disks

safecopy/mantic 1.7-7 amd64
  data recovery tool for problematic or damaged media
```
Performed following steps
Insert the same damaged music CD disc, without mounting it.

$ mkdir ~/Downloads/Test_folder_4
$ cd ~/Downloads/Test_folder_4/
$ ls

no output.  It is an empty folder

$ which cdrdao```

/usr/bin/cdrdao

```

$ cdrdao read-cd --datafile mytest.bin mytest.toc
```

....
....
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Reading toc and track data...

Track   Mode    Flags  Start                Length
------------------------------------------------------------
 1      AUDIO   0      00:00:33(    33)     05:27:07( 24532)
 2      AUDIO   0      05:27:40( 24565)     06:50:30( 30780)
 3      AUDIO   0      12:17:70( 55345)     05:28:50( 24650)
 4      AUDIO   0      17:46:45( 79995)     08:24:48( 37848)
 5      AUDIO   0      26:11:18(117843)     09:02:40( 40690)
 6      AUDIO   0      35:13:58(158533)     06:56:72( 31272)
 7      AUDIO   0      42:10:55(189805)     10:14:05( 46055)
Leadout AUDIO   0      52:24:60(235860)

PQ sub-channel reading (audio track) is supported, data format is BCD.
Raw P-W sub-channel reading (audio track) is supported.
Cooked R-W sub-channel reading (audio track) is supported.
Copying audio tracks 1-7: start 00:00:00, length 52:24:60 to "mytest.bin"...
Track 1...
Found ISRC code.
02:22:000:57:00  

```

(the time keeps on changing but very slow.  The LED light of DVD-Writer is continue flashing -> Stop -> Flashing again etc.)

It is now more than an hour passed;
```

mytest.bin	105.6 MB

```

No mytest.toc created.  The LED light of DVD-Writer stops flashing.

I have to stop it and eject the music CD disc

Regards

---

### Post by satimis on 2024-03-26
Hi@DennisN

Continued on my #35 above

The easy way to rescue undamaged .wav files is with "copy&paste" command.

Steps:
1. Insert the damaged music CD disc and mount it.
2. The track.wav files will be displayed on File Manager
3. Copy&Paste the track.wav files to a folder(pre-created) on the storage drive, ONE-by-ONE (not selecting all track.wav files)
4. Play the copied track.wav files on "VLC Media Player" to check which track.wav file damaged. The clicking noise will inform me

Then I can burn the good track.wav files on a new CD disc.

Is there any way to rectify the damaged track.wav files?

Regards

---

### Post by Dennis N on 2024-03-27
it appears that it is reading the TOC, but then can't copy the data of track 1? 

My copy output was this:

```
Copying audio tracks 1-10: start 00:00:00, length 25:53:70 to "mytest.bin"...
Track 1...
Track 2...
Found pre-gap: 00:00:24
Track 3...
Found pre-gap: 00:00:06
Track 4...
Found pre-gap: 00:00:15
Track 5...
Found pre-gap: 00:00:13
Track 6...
Found pre-gap: 00:00:12
Track 7...
Found pre-gap: 00:00:02
Track 8...
Found pre-gap: 00:00:14
Track 9...
Found pre-gap: 00:00:06
Track 10...
Found pre-gap: 00:00:03
Found 112 Q sub-channels with CRC errors.
Found disk catalogue number.
Reading of toc and track data finished successfully.


```
Copying (ripping) took about 8 minutes. Burning the new CD took another 2 minutes.
 
Your output says "Found ISRC code." Mine didn't. That's a difference, but right now I don't know what that implies. Was track 1 (where it got stuck) one of the "bad" files?
I wonder if cdrdao with the --read-raw option added would make a difference. The Linux Mint guy used it.
```
cdrdao read-cd --read-raw --datafile mytest.bin mytest.toc
```

It's good that you could copy the "good" files with the file manager. I suspect a rip and encode program like **Asunder** could too, because you can select those specific good files to copy. It would encode them to flac or other format as well.

For rescuing the remaining "bad" files: you might try one of the rescue utilities shown in post #34: **gddrescue** and **myrescue**.

Information on ddrescue: 
 [https://www.gnu.org/software/ddrescue/ddrescue.html](https://www.gnu.org/software/ddrescue/ddrescue.html)
 
 General Help:
 [https://www.makeuseof.com/tag/how-to-repair-and-recover-data-from-damaged-cds-or-dvds/](https://www.makeuseof.com/tag/how-to-repair-and-recover-data-from-damaged-cds-or-dvds/)

---

### Post by satimis on 2024-03-27
Hi@Dennis N

There are 7 track.wav files displayed on File Manager.  Please refers to the screenshot attachment on #32 above
```

Track 1.wav	working perfect without problem
Track 2.wav	damaged with cracking noise on playing
Track 3.wav	damaged with cracking noise on playing
Track 4.wav	damaged with cracking noise on playing
Track 5.wav	damaged with cracking noise on playing
Track 1.wav	working perfect without problem
Track 1.wav	working perfect without problem

```

3 track.wav files are working perfect.

I'm now looking around to see whether there is a solution removing the cracking noise

---

### Post by TheFu on 2024-03-27
> **satimis said:**
> Is there any way to rectify the damaged track.wav files?

1. Buy a replacement disc.

Looks like all other options have already been posted. Whether you tried them all, is a different question.

---

### Post by Holger_Gehrke on 2024-03-27
Another option (after making copies of the readable tracks) would be to try to resurface the disk. Obviously this can go horribly wrong, but if you've got the readable tracks of the disk copied first there's no reason not to try.

A bit of background: a CD is made up of multiple layers: A carrier of clear plastic on top of which there's the actual data layer (stamped into the carrier on mass fabricated discs; on burned CDs it's a layer of a some kind of lacquer that reacts to strong laser light by changing some of it's properties) on top of that there's a reflective layer and then the label. So in contrast to what everyone believes the label side is actually the side of a CD that's really susceptible to damage. There's only a few µm of material between your data and any harm on that side. Check the CD by holding it up against a light-source to see whether there's any damage of that kind. If there is, then you might as well not bother. 

Damage to the clear underside of the disk on the other hand is not quite as problematic. While scratches (or dirt) on that side might make reading impossible, the data is still there and polishing off a thin layer of material using a soft cloth and some kind of abrasive (or - in the case of dirt - just simply cleaning) might make it readable again. You can find tutorials on the net and there are also professional services who will do it for a price that's a lot less than the price of a new CD.

Holger

---

### Post by satimis on 2024-03-27
> **TheFu said:**
> 1. Buy a replacement disc.

Looks like all other options have already been posted. Whether you tried them all, is a different question.
It is not easy to get the replacement of Italian opera CDs here.

I'm trying hard to rescue following 2 Italian opera CDs which are covered with scratches:-
1. Il Corsaro by Verdi
2. L'Italiana in Algeri by Rossini

I purchased them in Italy on traveling in the past.

I still have another headache to convert VHS tapes of Classics, including Opera, to .mp4 video.  I have no device to play them.

Regards

---

### Post by satimis on 2024-03-27
> **Holger_Gehrke said:**
> Another option (after making copies of the readable tracks) would be to try to resurface the disk. Obviously this can go horribly wrong, but if you've got the readable tracks of the disk copied first there's no reason not to try.

A bit of background: a CD is made up of multiple layers: A carrier of clear plastic on top of which there's the actual data layer (stamped into the carrier on mass fabricated discs; on burned CDs it's a layer of a some kind of lacquer that reacts to strong laser light by changing some of it's properties) on top of that there's a reflective layer and then the label. So in contrast to what everyone believes the label side is actually the side of a CD that's really susceptible to damage. There's only a few µm of material between your data and any harm on that side. Check the CD by holding it up against a light-source to see whether there's any damage of that kind. If there is, then you might as well not bother. 

Damage to the clear underside of the disk on the other hand is not quite as problematic. While scratches (or dirt) on that side might make reading impossible, the data is still there and polishing off a thin layer of material using a soft cloth and some kind of abrasive (or - in the case of dirt - just simply cleaning) might make it readable again. You can find tutorials on the net and there are also professional services who will do it for a price that's a lot less than the price of a new CD.

Holger
Hi Holger,

Thanks for your advice.

I'm now duplicating/copying my music CDs to hard drive.  I have >500 music CDs.  Some of the music CDs were purchased abroad in my past traveling. >90% are classics, including Symphony, Concerto, Opera, etc.

In recent few days I have succeeded duplicating/copying 120 music CDs to the storage hard drive without problem.  Only 4 music CDs are found covering with scratches.  I have cleaned them with toothpaste and 75% alcohol with no result.

One damaged Opera CD can be mounted on DVD-Writer with all tracks .wav displayed on File Manager but I couldn't copy them to computer.  It is very strange.

I'm still working.

Regards

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Duplicating/copying music CDs to a hard drive of computer is quite easy with Copy&Past command.  It is not time consuming.  

I'm investing most of my time in copying/converting the content on their printed boxes to text files in computer.  The technology is "image to text".  I just take a photo on the box of music CD with a mobile photo, sending the images to computer and converting the image to text.

**[COLOR="#FF0000"]To re-arrange the text on the converted .txt file is quite time-consuming[/COLOR]**

---

### Post by satimis on 2024-03-31
Hi all,

Up-to-now I have duplicated/copied >200 music CDs to hard-drive without problem, only discovering 5 CDs with scratch problem.  I have 2 WD magnetic hard-drives for this job, each retaining a copy of my 500 music CDs. So in case one hard drive having problem, I still have another drive.

I have another thought of uploading my stock of CDs to YouTube or similar website for private use, only friends with password able to listen them online.

I'll create slideshow for each CD.  The video will be scenery and the CD will be as background music.  No indication of singer/player/orchestra etc. would be displayed on the slideshow.  This wouldn't infringe the patent right.  There is no patent right for Classic.  Their composers already passed away long time ago.

Comment and suggestion would be appreciate.

Regards

---

### Post by TheFu on 2024-03-31
It isn't patents. It is copyright law.  

If youtube sees it and cares at all, expect your account to be closed for violating copyright terms.  Different countries have different copyright laws.  In the US, it is usually 125 yrs from the creation date of the copyright item, since all copyrighted material can be sold to non-human entities with unlimited lives. 

[https://en.wikipedia.org/wiki/List_of_countries%27_copyright_lengths](https://en.wikipedia.org/wiki/List_of_countries%27_copyright_lengths) says most copyrights are "life + 50 yrs".  Different copyrights apply for different creation countries.  Ever wondered why CDs have different countries listed on them?  I bet it is for copyright reasons.

---

### Post by satimis on 2024-03-31
> **TheFu said:**
> It isn't patents. It is copyright law.  

If youtube sees it and cares at all, expect your account to be closed for violating copyright terms.  Different countries have different copyright laws.  In the US, it is usually 125 yrs from the creation date of the copyright item, since all copyrighted material can be sold to non-human entities with unlimited lives. 

[https://en.wikipedia.org/wiki/List_of_countries%27_copyright_lengths](https://en.wikipedia.org/wiki/List_of_countries%27_copyright_lengths) says most copyrights are "life + 50 yrs".  Different copyrights apply for different creation countries.  Ever wondered why CDs have different countries listed on them?  I bet it is for copyright reasons.
The composers of Classics died long time ago.  There is no copyright alredy.

Composers:
Beethoven 1770
Paganini 1782
Bach 1685
Mozart 1756
Verdi  1813
Rossini 1792
etc.

I have a good stock of Classical music CDs and VHS tapes in particular Opera.  They were purchased in Milano (Milan in English) Italy.  Nowadays it is not easy to purchase them.  My friends expect to share with them.

I have visited "Teatro alla Scala" (or "La Scala") in Milan, Italy when I was traveling there.  I almost have traveled the whole Italy except Sicily. 

La Scala
[https://simple.wikipedia.org/wiki/La_Scala](https://simple.wikipedia.org/wiki/La_Scala)

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
It is NOT easy to get a ticket to "Teatro alla Scala".  Tickets are sold several months in advance.  How can I get a ticket as a tourist in Milano?

I just waited in the entrance hall of "Teatro alla Scala" for an Italian, having ticket but unable to see the performance.  Then I got the ticket in luck.  The Italian won't sell the ticket to me with profit added, just the ticket price.

My Italian friend told me this trick.  It works 99%

---

### Post by Holger_Gehrke on 2024-03-31
The limiting factor for the duration of copyright on recordings of classical music actually isn't the lifetime of the composer but of the performers. Performing (and recording) a piece of music is seen as a separate act of creation of artwork.

Copyright law does distinguish between 'Legal' and 'Natural' persons as owners of copyrights. For natural persons (a.k.a. humans) it's life + something in most countries while for legal persons (a.k.a. companies) it's a fixed length. There's also a difference between 'work for hire' and independent creation of a work of art but that mostly affects artists working for companies and what rights they have in regards to their creations (this is a topic which is quite important in regards to comics and animation and has led to a lot of interesting legal conflicts).

So recordings of classical music are not out of copyright if they were made in the last 100 or so years. The score is probably public domain, but publishers are pulling the same trick as publishers of classic literature: they add something to the original work (an essay, a biography, a history of notable performances ...) that is new and therefore not out of copyright ...

There are recordings of classical music that are licensed under various creative commons licenses. Kimoko Ishizaka recorded 'Die Goldberg Variationen', 'Das Wohltemperierte Klavier' und 'Die Kunst der Fuge' and published the recordings along with the scores under CC-0; there's also the MusOpen Project which has at least a DVD's worth of mp3s (or flac, but then it's way more than one DVD ...) available under various licenses. You'll also find performances by high school or college orchestras on archive.org that usually have a very liberal license if they mention licensing at all. 

If you just want to put some background music to a slide show on YouTube there is an Audio Library on YouTube that you can use.

Holger

---

### Post by TheFu on 2024-03-31
Copyright is important for software too.  

Patents are sometimes, but not really as often as they are granted.  Most software patents don't deserve the patent.  A group of friends went through a list of audio patents related to telephony when MP3 audio was new and filed the same patents again, just with "mp3" instead.  The company paid the group $35K for each approved patent and covered the filing fees. They were granted!  They tried to do the same for GSM, AAC and all other audio types, but were beaten out by others.  Split between their group, it was "new car" time, not "pay off house" time.

---

### Post by satimis on 2024-03-31
> **Holger_Gehrke said:**
> The limiting factor for the duration of copyright on recordings of classical music actually isn't the lifetime of the composer but of the performers. Performing (and recording) a piece of music is seen as a separate act of creation of artwork.
It is correct.  There is no copyright for classics created by those composers listed on my posting above.  You can play their music pieces at any time.  But there are copyrights for performance.

> 
There are recordings of classical music that are licensed under various creative commons licenses. Kimoko Ishizaka recorded 'Die Goldberg Variationen', 'Das Wohltemperierte Klavier' und 'Die Kunst der Fuge' and published the recordings along with the scores under CC-0; there's also the MusOpen Project which has at least a DVD's worth of mp3s (or flac, but then it's way more than one DVD ...) available under various licenses. You'll also find performances by high school or college orchestras on archive.org that usually have a very liberal license if they mention licensing at all.
Das Wohltemperierte Klavier (The Well-Tempered Piano) is a performance

Die Kunst der Fuge (The Art of Fugue) is also a performance.
It is an incomplete musical work of unspecified instrumentation by Bach.

> 
If you just want to put some background music to a slide show on YouTube there is an Audio Library on YouTube that you can use.

I'm not in short of background music.  I can extract a short piece/theme of the classics as background music.

---

### Post by TheFu on 2024-03-31
"Fair Use" to be 100% safe is 15sec or less.  

People can try and push it to 30s, but don't be surprised if those get flagged.  Flagging tools are automated by some music producers.  

Really comes down to how strict the people who created the audio CDs wants to be.  Some artists specifically tell their publishers they don't want the bad press that going after copyright infringement causes.  Others are relentless - it was their work product and they want to be paid for any use that isn't clearly meant.  Certain high-profile artists/bands are known to be like this.  Buying a CD means non-commercial use, in a small, home, venue.  Buying a retail CD doesn't convey commercial use license or the right to broadcast.  The intended purpose for music CDs is for them to be used "like a book" - by people in the same room.  If people in different rooms can hear the same copy from the same original CD, that violates the license intent.  In theory, a music CD that gets ripped and is placed on both a home media server AND on your phone would violate the copyright because it is possible for two people in different rooms to listen to the same music at the same time.

Let your conscience be your guide, since we all have different ideas for what is "fair" and there are different laws in different jurisdictions.  There are a few countries where optical media sold to home users had a surcharge to pay back the artists for all the infringement that typically happened.   [https://www.cpcc.ca/en/](https://www.cpcc.ca/en/) is an example.

---

### Post by satimis on 2024-04-01
> **TheFu said:**
> 
- snip -

There are a few countries where optical media sold to home users had a surcharge to pay back the artists for all the infringement that typically happened.   [https://www.cpcc.ca/en/](https://www.cpcc.ca/en/) is an example.
I'm talking on Classics not Hits.

**[COLOR="#FF0000"]The performance made by;[/COLOR]**
London Philharmonic Orchestra
New York Philharmonic Orchestra
Boston Symphony Orchestra
Berlin Philharmonic 
Accademia Filarmonica Romana
etc.

**[COLOR="#FF0000"]The performance made by;[/COLOR]**
Jascha Heifetz (Violinist)
Hilary Hahn (Violinist)
George Enescu (Violinist)
Yehudi Menuhin (Violinist)
etc.

Daniel Barenboim (Pianist)
Vladimir Horowitz (Pianist)
Arthur Rubinstein (Pianist)
etc.

Luciano Pavarotti (Singer)
Renée Fleming (Singer)
Maria Callas  (Singer)
Joan Sutherland (Singer)
etc.

Neither I have Hits collection nor having knowledges on Hits.

---

