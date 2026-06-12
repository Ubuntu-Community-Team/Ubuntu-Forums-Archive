---
title: "can't play .iso in mythbuntu 12.04"
date: 2012-04-26
forum: Multimedia Software
---

### Post by w1ll1am on 2012-04-26
I am trying to play backed up dvds in mythvideo on mythbuntu 12.04. I can play the .iso in totem or vlc but when I try to play it in myth I get this on the terminal.


2012-04-26 21:18:43.927742 I  Using protocol version 72
2012-04-26 21:18:43.928583 I  Using protocol version 72
libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
2012-04-26 21:18:44.587948 I  Using protocol version 72
2012-04-26 21:18:44.588634 I  Using protocol version 72
2012-04-26 21:18:44.599898 E  FileRingBuf(myth://Videos@192.168.1.105:6543/CURIOUS_CASE_BEN_BUTTON_DOM.iso): Seek(524288, SEEK_SET) Failed
			eno: Invalid argument (22)
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2012-04-26 21:18:54.605055 E  FileRingBuf(myth://Videos@192.168.1.105:6543/CURIOUS_CASE_BEN_BUTTON_DOM.iso): Seek(524288, SEEK_SET) Failed
			eno: Invalid argument (22)
2012-04-26 21:18:54.610274 E  DVDInfo: Failed to open device at myth://Videos@192.168.1.105:6543/CURIOUS_CASE_BEN_BUTTON_DOM.iso

I have libdvdread4 installed and libdvdcss2.

Please help

---

### Post by w1ll1am on 2012-04-27
Okay I have tried some things since I posted last. I have installed totem on my myth box and it plays .iso images fine. I have also installed mythtv on my desktop running ubuntu 12.04 and the newest mythtv and I get the same error.

So I take this as an issue with mythtv possibly ubuntu but not libdvdread.

Please help! Thanks

---

### Post by w1ll1am on 2012-04-30
Bump

---

### Post by w1ll1am on 2012-05-01
Well finally got it working. Here is what I had to do.

Go into the backend settings and go to storage directories and delete whats under video. Then add a new directory to where ever it is you are going to have your .iso. I have mine in /home/w1ll1am/videos I tried /home/w1ll1am/Videos which is the default video directory and it did not work.

Now go into your frontend settings and go to video and change the video location to the same as above. Then re scan to changes and it should work.

It seems this was an issue in like .23 and it was fixed in .24 and somehow was broke again.

---

### Post by w1ll1am on 2012-05-01
> **w1ll1am said:**
> Well finally got it working. Here is what I had to do.

Go into the backend settings and go to storage directories and delete whats under video. Then add a new directory to where ever it is you are going to have your .iso. I have mine in /home/w1ll1am/videos I tried /home/w1ll1am/Videos which is the default video directory and it did not work.

Now go into your frontend settings and go to video and change the video location to the same as above. Then re scan to changes and it should work.

It seems this was an issue in like .23 and it was fixed in .24 and somehow was broke again.

I lied this is wrong I actually have the backend pointing to a directory that doesn't exist and it works. /home/w1ll1am/video not /home/w1ll1am/videos if I change it to /home/w1ll1am/videos in the backend I get the error. 

So clearly there is something wrong but this is a temporary work around.

---

### Post by Fincer on 2012-05-12
Confirmed.

I have similar issues with the most recent Mythbuntu release: ISO files are playing OK when using VLC Player on the desktop, proving that this is not an issue of missing DVD/ISO libraries. MythTV frontend recognizes all videos files as it should do but it's unable to play any ISO files I have stored in my videos folder.

I hope the bug will be fixed soon.

---

### Post by BicyclerBoy on 2012-05-12
I'm not sure this is a bug..
The FE & BE video storage paths are not the same thing..

Myth can play encrypted DVDs & ISO from the FE only..
Storage groups are BE & are streamed to the FE.

If your BE & FE are separate machine you could try an NFS share; point the FE video folders at the NFS share of the BE ISO storage.

You can mount -o loop the ISO for the FE to access..

There is interesting thread here:
[http://www.gossamer-threads.com/lists/mythtv/users/497644](http://www.gossamer-threads.com/lists/mythtv/users/497644)

---

