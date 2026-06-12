---
title: "CD's Won't Play in 6.06 LTS"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by JustDon on 2006-11-18
When I insert a CD (that I burned in Windows, also plays in Windows Media Player and Real Player), I get this message:

[COLOR="Blue"]Could not read the CD

Sound Juicer could not access the CD-ROM device '/dev/hdc'
Reason: Permission denied[/COLOR]

I also did:

[COLOR="Blue"]dhatcher2@dhatcher2-desktop:~$ sudo su
Password:
root@dhatcher2-desktop:/home/dhatcher2# sound-juicer -d %d

(sound-juicer:13904): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@dhatcher2-desktop:/home/dhatcher2#[/COLOR]

What do I need to do to be able to play CD's in Ubuntu?

---

### Post by JustDon on 2006-11-30
I also tried this with a master recording (bought CD) and the exact same thing happens, why can I not play a CD in Ubuntu?

---

### Post by JustDon on 2006-12-02
I downloaded VLC Media Player through AutoMatix and it plays the WMA files perfectly (from my XP partition), I corrected the CD player by:

sudo adduser <username> cdrom

It was a permission issue.

---

