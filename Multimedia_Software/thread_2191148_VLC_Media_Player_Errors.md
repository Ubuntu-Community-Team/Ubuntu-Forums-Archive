---
title: "VLC Media Player Errors?"
date: 2013-12-01
forum: Multimedia Software
---

### Post by ML7rcEx on 2013-12-01
I am running Lubuntu 13.10 and have installed the VLC media player. But when i try to play a dvd i get the following errors:

Playback failure:
DVDRead could not open the disc "/dev/dvd"
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd' check log for details.

Could someone help me out here please.

---

### Post by giles.wheatley on 2013-12-16
go to preferences disks. Select the CD/DVD Drive. note the /dev/sr0 or whatever it is.
Open VLC and select open disc. Edit the Disc device to the /dev/sr0 or whatever it was.
Click the play button.
Worked for me.
G

---

