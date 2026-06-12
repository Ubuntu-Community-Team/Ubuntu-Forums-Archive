---
title: "Some Suggestions"
date: 2010-05-13
forum: Multimedia Software
---

### Post by gerowen on 2010-05-13
The feature in Gnome to mount archives as drives now is handy, however I have a suggestion, let me explain.

1)I make ISOs of my DVDs so I can keep all the menus and full quality video mobile.
2) As of right now Totem kicks out an error if I try to mount one of these images and play the location.
3) Even if I manually mount the images to /mnt/iso and try to play the location Totem kicks out an error.
4) VLC won't play the path that the archive mounter gives mounted ISOs either.
5) So as of right now to play one of my DVD ISOs I run [my own script](http://dl.dropbox.com/u/6017319/Software/MountISO%2010.5.12.tar.gz) to mount images in /mnt/iso and then I use VLC to "Play Disc" and just change the path to the disc accordingly.

My suggestions are the following, even though I know the Ubuntu team specifically isn't responsible for individual pieces of software like totem, maybe you guys can tell the right people.
1) Shorten the path the archive mounter mounts images to, make it some legible location like my little script above does with /mnt/iso.
2) Enable Totem to play "Discs" from a different directory (the mounted image).
3) When the Archive Mounter mounts an ISO, have it show up as a disc so media players' built in options of "Play *Discname*" show up when you mount a DVD image.

I would offer example code but I'm not a skilled enough programmer and I'm not familiar enough with the inner workings of Gnome/Totem to be helpful in that dept.  If I'm wrong and there's ways to do this already, please let me know.  If you guys can use my noobish script up there to work on this feel free to take the source code and do with what you please, it's one of very few things I've written that I actually tried to do in a "professional" manner (Readmes and such).

---

### Post by cchhrriiss121212 on 2010-05-13
I don't know why you need to mount an iso image if it is on your hard drive? I have some dvds on my hd which I can play by opening them with vlc, or navigating to the video_ts.ifo in /youriso/video_ts. Smplayer also has a feature that allows you to save the directory of dvds you might have on your hard drive.

---

### Post by gerowen on 2010-05-15
Scratch all this, for some reason Totem just decided to start playing images I mount with the built in archive mounter...

---

### Post by raygj on 2010-05-16
> **marcusdean.adams said:**
> Scratch all this, for some reason Totem just decided to start playing images I mount with the built in archive mounter...

Don't mount your .iso image files.
Just "right mouse click" on the .iso file and "open with" VLC media player.
Thats what I do to play my DVD movie image files(.iso) ....

---

