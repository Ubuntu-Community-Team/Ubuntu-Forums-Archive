---
title: "problem playing dvd's"
date: 2011-04-25
forum: Multimedia Software
---

### Post by etyson on 2011-04-25
Hi All,

I have a Thinkpad with a factory-stock DVD-RW in the bay and a Plextor  USB bluray player.  I've used both of these to play DVD's in Kubuntu  10.04 about 6 months ago.  I've upgraded to 10.10 and I can't play  DVD's -- in VLC (favourite) xine, or mplayer.  

VLC complains: 

Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr1'. Check the log for details.

or

Your input can't be opened:
VLC is unable to open the MRL 'dvd:///media/SPARTACUS_S1_D1'. Check the log for details.


I created a log file (RW all groups) and have pointed VLC to it but VLC never writes to it.  It's empty.

----------------------------------------------------------------------


Typing "mplayer dvdnav://" gives


MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvdnav://.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/user6/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
Couldn't open DVD device: /dev/dvd (Input/output error)
No stream found to handle url dvdnav://


Exiting... (End of file)






Any ideas??

---

### Post by wilee-nilee on 2011-04-25
Generally these are needed
libdvdread
libdvdcss2
w32 codecs

You can get them from medibuntu, I think the dvdread is stock though.
 [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by etyson on 2011-04-25
> **wilee-nilee said:**
> Generally these are needed
libdvdread
libdvdcss2
w32 codecs

You can get them from medibuntu, I think the dvdread is stock though.
 [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)



Tried to install but looks like I have the most current versions:

apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


 sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

---

### Post by handy on 2011-04-25
Both of your drives work for reading data from optical media?

Can you play audio CD's on them?

---

### Post by SeijiSensei on 2011-04-25
How about "mplayer dvd://1" followed by "mplayer dvd://2", etc?  What happens when you insert the DVD?  Does the device popup appear in the system tray and list options for handling the medium?  What do you see for optical disc handlers in System Settings > Device Actions?

---

