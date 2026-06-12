---
title: "Unable to watch live TV w/ Mythtv"
date: 2008-05-11
forum: Multimedia Software
---

### Post by mechdesignron on 2008-05-11
I am using a kworld 110 amd 64 ubuntu 8.04
If I stop myth backend I can watch TV fine with me-tv.
If myth-backend is running I cannot (device or resource busy)
Everything else seems to be working fine with Myth-TV.
When I try to watch TV I get a black screen and it goes back to menu.
Here are the lines from the log file.

2008-05-11 13:34:53.878 TV: Attempting to change from None to WatchingLiveTV
2008-05-11 13:34:53.879 Using protocol version 40
2008-05-11 13:34:55.095 GetEntryAt(-1) failed.
2008-05-11 13:34:55.097 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2008-05-11 13:34:55.097 TV Error: LiveTV not successfully started
2008-05-11 13:34:55.097 TV Error: LiveTV not successfully started
2008-05-11 13:34:55.183 TV: Deleting TV Chain in destructor
2008-05-11 13:34:55.190 DPMS Deactivated 
2008-05-11 13:34:55.191 DPMS Reactivated.
2008-05-11 13:35:01.648 XMLParse::LoadTheme using /usr/share/mythtv/themes/neon-wide/ui.xml
2008-05-11 13:35:16.426 Deleting UPnP client...

Thank you for any suggestions.

---

### Post by sinkinglow on 2008-05-25
I had the same issue and I found that the directory that stores the recordings did not have the group mythtv on that directory. Do a ls -ld pathToRecordingsDirectory and see if the mythtv group is there. I changed this directory to be owned by my user but the mythtv group and that worked for me.

---

### Post by pevans91 on 2008-05-28
Hi! I'm getting exactly the same problem, although it's interesting to note, after selecting Watch TV, the screen blanks and returns to the menu. However, when then searching Recordings, MythTV shows the current program at the time of clicking Watch TV as being recorded, although it takes up 0 bytes. 

Another interesting fact is that, when on program guide, programs selected for record are successfully recording, and can be watched back without the blank screen error. It just seems to be the "Watch TV" function?

Any ideas? Btw, i tried the permissions idea above, no resolution though...

Thanks!

---

### Post by Jim-BobH on 2008-06-28
Yes, I had the same problem, even after I had set the rights on

/mnt/data/MythTV_Recordings to

root@Edward:/mnt/data# ls -l
drwxrwxr-x 2 mythtv jim 4096 2008-06-28 17:22 MythTV_Recordings

later, when I ran into the "can't watch TV" problem and found this thread, I looked and it was changed !

drwxr-xr-x  2 jim jim    1 2008-06-28 20:33 MythTV_Recordings

so i changed it AGAIN to

root@Edward:/mnt/data# chown mythtv:mythtv MythTV_Recordings/
drwxrwxr-x  2 mythtv mythtv    1 2008-06-28 20:33 MythTV_Recordings

and immediately (with no re-start or anything) I can watch TV !

Please pass this on to the developers (I can't find their forum); this is weird!

Also, does anyone know how to _remove_ a directory from the Recordings group in Mythbuntu 8.04? I would like to remove

/var/lib/... from the list, or otherwise force MythTV to _only_ use my data drive.

Jim

---

### Post by adonet on 2008-07-15
I use the D key when setting up a new directory. It deletes the actual directory

---

### Post by dlgaier on 2009-04-22
I need some help with my setup.  Everything seems to work fine until I try to watch Live TV.  When I start it, the screen goes black for about 10-15 sec, then returns to the menu.  I read through the messages above, and have checked the permissions on the recording directory.  I changed them both (group and owner) to mythtv, but it still does the same thing.  I end up with a file in the recording directory with zero length.

I know the card (WinTV 150) works because I installed it in a windows machine and downloaded the program from Hauppaugue (sp?), and it worked fine.  Here are the sections from the frontend and backend logs:

Frontend.log
2009-04-22 22:03:01.627 TV: Attempting to change from None to WatchingLiveTV
2009-04-22 22:03:01.628 Using protocol version 40
2009-04-22 22:03:09.357 RingBuf(/var/lib/mythtv/recordings/1002_20090422220301.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1002_20090422220301.mpg'.
2009-04-22 22:03:09.376 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/1002_20090422220301.mpg
2009-04-22 22:03:09.376 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-04-22 22:03:09.452 DPMS Deactivated 
2009-04-22 22:03:13.912 TV Error: LiveTV not successfully started
2009-04-22 22:03:13.961 DPMS Reactivated.
2009-04-22 22:03:26.636 Deleting UPnP client...

Backend.log
2009-04-22 22:03:01.636 TVRec(1): Changing from None to WatchingLiveTV
2009-04-22 22:03:01.644 TVRec(1): HW Tuner: 1->1
2009-04-22 22:03:02.845 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2009-04-22 22:03:02.854 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-04-22 22:03:08.338 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-04-22 22:03:09.379 TVRec(1): Changing from WatchingLiveTV to None
2009-04-22 22:03:13.782 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding

Any suggestions on what I should check?  I've been working on this for a while and am running out of ideas.

Thanks.

---

### Post by wolfen69 on 2009-04-22
are you using the right drivers? during setup, you need to change from the default video4linux drivers to the mpeg2 pvrx50 drivers. this is done from a pull down menu on one of the setup screens. just go to the setup menu and double check.

btw, where in CT are you from? i'm in stratford.

---

### Post by dlgaier on 2009-04-23
> **wolfen69 said:**
> are you using the right drivers? during setup, you need to change from the default video4linux drivers to the mpeg2 pvrx50 drivers. this is done from a pull down menu on one of the setup screens. just go to the setup menu and double check.

btw, where in CT are you from? i'm in stratford.


In one of the setup screens (backend?) I've told mythtv that I'm using a pvrx50 card, but I don't know if that took care of the drivers or not - do I need to do something else?

More info - when I scan for channels, it seems to see the right ones and puts them in the list, but when I try to watch live TV or record something (tried this last night), the file ends up with a zero length.

Another thought - I bought my card on ebay a few months ago, and I remember seeing a message in one of the forums about needing to use an earlier version of the driver files if the board is an earlier vintage.  Is that something I may need to look into?  I will pull out my board when I get a chance to see if I can find out when it was manufactured.

I live in Newtown and work in Wilton.

---

### Post by dlgaier on 2009-04-25
OK, I finally got it working, and you won't believe what it was ...

I've probably spent my spare time over the last 2 weeks checking drivers and settings and "how-to"s to find a solution to this problem.  Basically everything was set up correctly, I knew my WIN PVR-150 card worked (had tried it in windows machine), and when I scanned the channels in the present machine, it found them fine.  Unfortunately I couldn't get any live video - every time I tried, I got a file of zero size (either with LiveTV or with the "cat /dev/video0 > test.mpg").

Anyway, I finally remembered a post I read a while back about motherboards where the cards wouldn't work quite right in all the slots.  If I remember correctly, it said to put it as close to the CPU as possible.  My card was right next to the CPU, but when I moved it one slot farther away, everything started to work!  I'm sure I still have some other setup work to do, but at least I'm past that problem.  Hopefully this will help someone else avoid spending as much time as I did looking for what turned out to be a really silly problem!

---

### Post by Kypdurron5 on 2009-11-13
> **sinkinglow said:**
> I had the same issue and I found that the directory that stores the recordings did not have the group mythtv on that directory. Do a ls -ld pathToRecordingsDirectory and see if the mythtv group is there. I changed this directory to be owned by my user but the mythtv group and that worked for me.
I realize your post was over a year ago, but thanks!!  Totally solved my problem.  After restoring my PC from a backup I recreated the mythtv folder (didn't see a reason to back them up as I use mounted network storage instead) and couldn't watch live TV anymore.  I'm a complete linux novice but here's what I did:

1)  Under /var/lib/mythtv/ use "sudo chown USER recordings" to give ownership to local user (I created the folder while working as root)
2)  Then use right-click, properties-> permissions to give the mythtv "group" full read-write access.  

Works like a charm again!  Thanks so much!

---

### Post by markackerman8@gmail.com on 2010-04-23
Hallelujah, this Newbie has found the problem after pulling my hair out for weeks and assuming the problem was with tuner cards and it was simply my permissions for my mythtv folders needed to have "group" set to "mythtv" with read and write privileges., and BAMM it works.  

Thanks for the insight!!!

The Wintv-pvr-usb2 works great for analog ntsc cable and MythTV!

:guitar:

---

### Post by joiningtheherd on 2010-06-02
So...  Checked all of the above directory permissions(and tried several permutations on the permissions), but no dice.  The system is Amd64 running 10.04.  The channels scan fine.  Everything seems to work.  TvTime has no issues. etc.  Here are the relevant permissions and logs.

Permissions:
```
media@media-pc:~$ ls -l /media/MythTV/
total 4
drwxrwxrwx 2 mythtv mythtv    6 2010-06-02 22:21 banners
drwxrwxrwx 2 mythtv mythtv    6 2010-06-02 22:21 coverart
drwxrwxrwx 2 mythtv mythtv    6 2010-06-02 22:21 db_backups
drwxrwxrwx 2 mythtv mythtv   70 2010-06-02 22:21 default
drwxrwxrwx 3 mythtv mythtv   48 2010-01-13 19:20 Editing
drwxrwxrwx 2 mythtv mythtv    6 2010-06-02 22:21 fanart
drwxrwxrwx 2 mythtv mythtv    6 2010-06-02 22:21 livetv
drwxrwxrwx 2 mythtv mythtv    6 2010-06-02 22:21 screenshots
drwxrwxrwx 2 mythtv mythtv    6 2010-06-02 22:21 trailers
drwxrwxrwx 2 mythtv mythtv 4096 2010-06-02 22:21 videos

```

Log:
```
2010-06-02 22:11:28.220 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-06-02 22:11:28.221 Using protocol version 56
2010-06-02 22:11:53.221 TV: Attempting to change from None to WatchingLiveTV
2010-06-02 22:11:53.221 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-06-02 22:11:53.222 Using protocol version 56
2010-06-02 22:11:53.240 Spawning LiveTV Recorder -- begin
2010-06-02 22:12:00.242 MythSocket(2731ac0:43): readStringList: Error, timed out after 7000 ms.
2010-06-02 22:12:00.242 RemoteEncoder::SendReceiveStringList(): No response.
2010-06-02 22:12:00.242 Spawning LiveTV Recorder -- end
2010-06-02 22:12:00.243 GetEntryAt(-1) failed.
2010-06-02 22:12:00.245 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-06-02 22:12:00.245 TV Error: HandleStateChange(): LiveTV not successfully started
2010-06-02 22:12:00.246 We have a RingBuffer
2010-06-02 22:12:00.303 TV Error: LiveTV not successfully started 
```

Every part of the Myth TV install is local. It looks like there is  some problem with contacting the database, but the password is correct (default random password generated on install) and host ip's all match, default ports.  I'm punting on this one after three days ... final are here and I need to study.  I'd really appreciate some help.

-TD

---

### Post by markackerman8@gmail.com on 2010-06-07
I truly wish I could help further, but I am out of my league here.

Truly sorry, good luck

I will add that a guy named Mlord on this forum has solved some major problems with ease!

[http://www.digitalhome.ca/forum/showthread.php?p=1109811&posted=1#post1109811](http://www.digitalhome.ca/forum/showthread.php?p=1109811&posted=1#post1109811)

Tell him I referred you,

Mark

---

### Post by bradleypariah on 2010-06-13
I finally got it working too!  :-D

The previous fixes didn't quite work for me, I'll spare the details why.  ;-)

Here is the fix that worked for me:

```
sudo chmod -R 777 /var/lib/mythtv
```

If you're concerned that evil underpants gnomes will find out what TV shows you watch/record, exchange 777 for your favorite permissions binary.

Thank you so, so much to the previous posters in this forum.  Your help of others led me in the right direction.  I just had to pass along my successful method as well.  I wish everyone had this sweet setup.  I'm so stoked!

:guitar:

My MythBuntu setup is:
Ubuntu 10.04, 64-bit, fully updated 
MythTV installed from Ubuntu Software Center
Gigabyte K8-U Motherboard
AMD 3400+ Processor
2.5GB Kingston RAM
Hauppauge 1600 PVR PCI-card
Nvidia 6200 512MB using "current" driver

---

