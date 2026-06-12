---
title: "K9copy Crashes"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by Purple Grant on 2007-06-02
I run feisty

I copied one DVD with K9 Copy and everything was fine·

Then I tried to run DEVeDe and ManDVD to put some AVIs on to DVD. This gave me horrible sound, which is apparently a known bug with mencoder (I messed about a bit with this, which is where I think my problems may lie.) under feisty.
So I took those off.

But now k9 Copy crashes as soon as it starts copying. (as does DVD95)

I've tried taking mencoder in and out a few times, along with some other things. But I am a noob stabbing blindly in the dark when it comes to codecs and things.

Can anyone help me?
 This is the error message...


(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1241806192 (LWP 5929)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6 0xb77dc65c in k9Cell::addNewVobus () from /usr/lib/libk9copy.so.0
#7 0xb77e470a in k9DVDBackup::copyEmptyPgc () from /usr/lib/libk9copy.so.0
#8 0xb77e95c8 in k9DVDBackup::copyCell () from /usr/lib/libk9copy.so.0
#9 0xb77e9d2d in k9DVDBackup::execute () from /usr/lib/libk9copy.so.0
#10 0x0806425b in ?? ()
#11 0x082959a0 in ?? ()
#12 0xbff163b4 in ?? ()
#13 0x080a3d8c in ?? ()
#14 0xbff163ac in ?? ()
#15 0xb62797fc in __pthread_mutex_unlock_usercnt ()
from /lib/tls/i686/cmov/libpthread.so.0
#16 0x08080738 in ?? ()
#17 0x081a4cb8 in ?? ()
#18 0x08227838 in ?? ()
#19 0xbff16418 in ?? ()
#20 0xb6d27ab0 in ?? () from /usr/lib/libqt-mt.so.3
#21 0x080806e0 in ?? ()
#22 0x08228728 in ?? ()
#23 0xbff16458 in ?? ()
#24 0xb685f88b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
Backtrace stopped: frame did not save the PC

---

### Post by marsbt on 2007-06-06
any update on this? I'm having similar crashes as soon as I ask it to open a DVD!

---

### Post by pemo on 2007-06-06
I've found that if you execute the program from the terminal "sudo k9copy", it runs.
Now, the only thing left is to change the permissions.
RGDS

---

### Post by Purple Grant on 2007-06-08
Tried it with sudo.

It still didn't work,  

I got this...


grant@grant-desktop:~$ sudo k9copy
Password:
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 10571

---

