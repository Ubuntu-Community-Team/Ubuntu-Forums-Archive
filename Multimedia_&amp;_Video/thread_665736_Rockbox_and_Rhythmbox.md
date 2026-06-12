---
title: "Rockbox and Rhythmbox"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by mexpolk on 2008-01-12
**[COLOR="Red"]Didn't find a solution, so I'll be using original iPod's firmware for now.[/COLOR]**

Has anyone found a way to make Rhythmbox (or Banshee) to work for Rockbox? I mean, that when synchronizing the music it places in /media/ipod/Music instead of /media/ipod/iPodControl/Music?

I even tried to hack HAL fdi files, so my iPod was treated as a generic usb storage device and nothing seems to work.

best!

---

### Post by edm1 on 2008-01-12
you could use rsync (grsync for a gui).

---

### Post by mexpolk on 2008-01-12
Thanks for the reply "edm1"...

But what if I just want to pass some smart lists... Is that possible (I use rsync for other purposes also)? I got an iPod nano 4GB  so I have not too much room for all my music.

---

### Post by muszek on 2008-01-16
I keep my albums in a directory tree:
* tagged
** fresh
** player
** non-player
* non-tagged

Only tagged/fresh and tagged/player get to be on my iAudio x5 (30GB) w/ rockbox.  I don't know if it would worke nice if I only had 4GB, as swapping albums on and off the player must be a frequent task... .

Ideally I'd like to be able to just select artists/albums in rhythmbox and add/delete them from the player.  Do other programs give that functionality?

---

### Post by mexpolk on 2008-01-17
Well, after sneaking for a while my best bet seems to be gtkPod, it's a great application. With this application I can create playlist for my iPod (limited by size), and other disks as well.

As for my laptop I gonna stick to Rythmbox.

Thanks for your replies!

---

### Post by jrasmussen0 on 2008-02-25
[http://live.gnome.org/Rhythmbox/FAQ]("http://live.gnome.org/Rhythmbox/FAQ")

Create a .is_audio_device file on the root of the device and have a line like:
[INDENT]audio_folders=iPodControl/Music[/INDENT]

---

### Post by danwood76 on 2008-06-16
I know this thread is a little old but I have a solution if your still looking.

I have rockbox working with banshee (and rhythmbox I assume) the trick is do delete the ipod section in the hal settings file, or comment it out like I have.
Then create the .is_audio_device in the ipods root dir.

---

