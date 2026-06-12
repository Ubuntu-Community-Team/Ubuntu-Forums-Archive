---
title: "DVDs are mounted differently in Intrepid?"
date: 2008-11-15
forum: Multimedia Software
---

### Post by theShaggy on 2008-11-15
Hi guys, I discovered something that I don't recall happening before.

Basically, when I put a DVD into my drive, it takes the title of the movie and mounts it as that name.  I don't seem to recall this happening with earlier versions, and it therefore screws up my ability to use MythTV (since you have to specify which drive to be running from).  None of my media players (MPlayer, Totem, VLC) will play anything on a right-click any more, I have to specify which directory the DVD is mounted in.

Is there any way I can stop Intrepid from mounting DVDs this way, and just mounting in the old /media/dvdrom0 or /media/cdrom0 as I have it?  It's rather annoying.

---

### Post by mc4man on 2008-11-15
What version of 8.10 are you using? I don't see that in ubuntu (gnome) - dvds  are automounted to what's set in fstab, /media/cdrom0, /media/cdrom1, ect.

Kubuntu (kde4.1) is a bit different, by default dvds (dvd-rom) aren't auto mounted at all,

Players access thru the device. When they are 'mounted', either by opening with file manager or in konsole (mount /dev/dvd for example)  they are again mounted as specified in fstab. (/media/cdrom0, ect.

Whats your fstab show?

Edit:
Have yet to figure how to have a dvd-rom auto mount in kde4, whether it's possible and or of any value i don't know. ( not needed for playback

---

### Post by theShaggy on 2008-11-16
I managed to get MythTV running by directing to the /dev.  FOr some reason, 8.10 decided to rename all of my devices, so after upgrade I also had all my partitions go down.

I'm running Gnome.  I'll have a look into my fstab and see if anything is finnicky in there, but what happens is that it keeps /media/cdrom0 but won't let me access a DVD film.  Instead, it mounts /media/'dvdname'.  It's very strange.

---

