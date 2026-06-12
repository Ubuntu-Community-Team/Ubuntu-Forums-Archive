---
title: "QDVDAuthor errors"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by mibadt on 2006-06-19
Hi,
While trying to author a DVD I did the following:
1. Allocated folders with lots of space for project and tmp files.
2. Added 4 mpeg files (total 1.8 GB)
3. Added main menu background and 4 entries
4. Pressed OK.

QDVDAuthor initially an OK, showed all "fixing VOBU.."
and finaly erred stating  it couldn't opn the main menu mpeg -it didn't exist (not exact phrasing).

What am I doing wrong?:mad:

---

### Post by meng on 2006-06-19
I have not had any good experiences with QDVDAuthor. I use DVDStyler instead, but I believe it's not in repositories.

---

### Post by mibadt on 2006-06-20
[QUOTE=meng]I have not had any good experiences with QDVDAuthor. I use DVDStyler instead, but I believe it's not in repositories.[/QUOTE]

Thanks, I'll try that one too.
:D 
Regards,

Michael Badt

---

### Post by disturbed1 on 2006-06-20
DVDStyler for the win ;)

If you goto the home page there are .deb files that install fine on Ubuntu.

[http://dvdstyler.sourceforge.net/](http://dvdstyler.sourceforge.net/)

1.5b5 was just released, but the debs are at 1.5b4. I haven't noticed any issues with b4. Grab both debs, you'll get an error trying to run DVDStyler without wxsvg.

---

### Post by little cazy on 2006-06-27
qdvdauthor won'ted open for me, so i tied on the terminal and i got this:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Could not create QMPlayerWidget engine, will default to QXineWidget

*** glibc detected *** corrupted double-linked list: 0x08c36648 ***
Aborted
:confused: :confused: :confused:

---

### Post by little cazy on 2006-06-27
sorry all i had to do was:
deinstall it {competely}(qdvdauthor)
reinstall it
then restart the computer
warrining:can _not_ just restall it

---

