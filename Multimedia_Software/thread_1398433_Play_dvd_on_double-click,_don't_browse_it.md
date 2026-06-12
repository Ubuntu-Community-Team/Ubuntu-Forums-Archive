---
title: "Play dvd on double-click, don't browse it"
date: 2010-02-04
forum: Multimedia Software
---

### Post by cata00 on 2010-02-04
Hi all,

I'm configuring a Karmic box for some family friends who have never used GNU/Linux before. They are absolute no-power users, so I'm trying to make everything simple to minimize the amount of customer support I'll have to do in the future. :-)

One of the things that I don't like is that, when you insert a DVD and double-click on the disk's icon, the default action is to browse the disk. So what I see is a File browser with AUDIO_TS and VIDEO_TS. Granted, the window has a message about the files being on a DVD, and a button to open my player of choice. But to me, that's more than a new user should have to understand. Is there a way to just play the dvd when I double click it? My friends will never, ever, ever have any reason to browse the DVD.

To make things clear, the system does auto-play the DVD. However, if for some reason they close the player and want to open it again later by double-clicking the icon, it currently doesn't work.

Thanks!
Catalin

---

### Post by howefield on 2010-02-04
> **cata00 said:**
> ...if for some reason they close the player and want to open it again later by double-clicking the icon, it currently doesn't work.

Instead of double clicking, right click and select "Open with VLC" (assuming you install it) how easy is that ?

---

### Post by howefield on 2010-02-04
If that isn't simple enough, perhaps you could create a desktop launcher with a nice DVD type icon using something like vlc dvd:///dev/sr0 as the command to launch.

A double click on it would start the dvd.

You don't have to use vlc, you can use whatever player you want, and change the command to suit.

---

