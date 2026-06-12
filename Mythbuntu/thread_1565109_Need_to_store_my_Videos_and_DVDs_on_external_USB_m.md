---
title: "Need to store my Videos and DVDs on external USB media player"
date: 2010-08-31
forum: Mythbuntu
---

### Post by petatkinson on 2010-08-31
Now that I think I have sorted out Myth I need to store my recordings and my DVDs on my external USB media drive.I know at present they are stored automatically in /var/lib/mythtv/videos which will store them on the hard drive in that "directory".In other words how do I redirect my recordings automatically to my external USB drive in Mythbuntu.

---

### Post by tgm4883 on 2010-08-31
In mythtv-setup, you need to change the storage directories for everything you want to store on the external drive to point to the external drive mountpoint

---

### Post by petatkinson on 2010-08-31
Ok.So instead of the default /var/lib/mythtv/videos if I enter /mediaplayer/videos it should automatically direct it to my media player.

---

### Post by LowSky on 2010-08-31
yes, but be aware that if the drive is not connected mythtv will not go back tot he default... it need to be changed back by hand.


make sure the drive has permissin to allow the mythtv user to read/write to the drive, if it is formated in a Linux format like EXT4

---

### Post by petatkinson on 2010-09-02
OK in the MythTV backend under Storage options for recordings, livetv and videos I use /media/ScreenPlayPro_HD/ {thats my extenal media path} went back to frontend ran Watch TV and was kicked back to the menu.Changed everything back to the default setup and everything is back to normal.Am I missing something.

---

### Post by LowSky on 2010-09-02
Did you create a recordings, videos, and liveTV folders within /media/ScreenPlayPro_HD? And did you give those folders the correct permissions for the mythtv user to read and write data?

---

### Post by petatkinson on 2010-09-03
Yes I created the relevant folders.As soon as I restore the default storage folders everything works as normal.You reckon it may be down to permissions.Ironically, the storage directory I set up for DVD ripping on the USB media drive works fine

---

### Post by klc5555 on 2010-09-03
> **petatkinson said:**
> Yes I created the relevant folders.As soon as I restore the default storage folders everything works as normal.You reckon it may be down to permissions.Ironically, the storage directory I set up for DVD ripping on the USB media drive works fine

Mythtv in Mythbuntu expects the entire storage path and recorded files to be owned by mythtv, to be part of the mythtv group, and to have permissions set to about 774 or 775, the way it's set up by default under /var/lib/mythtv/... If storage is mounted elsewhere and with owner/group/permissions set otherwise, you'll likely start out with various odd glitches of the sort you're experiencing that ultimately turn out to be permissions problems.

---

