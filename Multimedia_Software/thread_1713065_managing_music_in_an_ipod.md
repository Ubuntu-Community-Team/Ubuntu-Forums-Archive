---
title: "managing music in an ipod"
date: 2011-03-23
forum: Multimedia Software
---

### Post by nitzan on 2011-03-23
Hi.

I have two machines running ubuntu 10.10, one which acts as a media server to which i connect with the other (laptop) using ssh.
All of the music is on the media server and I mount it with samba on the laptop.

I want to be able to manage music in my ipod (a very old one, probably G1 or G2) but I can't seem to make it work...

When I connect it to the laptop it looks ok, and the ipod is visible in Rhythmbox but I can't add music to the ipod, not sure why, maybe because all of my music is on the server and not local?
If I try to sync the ipod and my library it says that there's not enough disk space since the library is far bigger than the capacity of my ipod.

When connected to the server, I mount the ipod but the Rhythmbox just don't display it.  I checked in the plugins and the ipod support is enabled.

Any idea how I can make it work?
Thanks.

---

### Post by shantiq on 2011-03-23
hi nitzan    i would suggest gtk ipod manager 

```
sudo apt-get install gtkpod
```


also banshee

> Banshee is a media management and playback application for the GNOME desktop, allowing users to import audio from CDs, search their library, create playlists of selections of their library, sync music to/from iPods and other media devices, play and manage video files and burn selections to a CD.





or use some of the one in software centre shown in the image hipo ipod looks promising too


[CENTER][[IMG]http://img171.imageshack.us/img171/7537/fhngh.th.png[/IMG]](http://img171.imageshack.us/img171/7537/fhngh.png)
[/CENTER]

---

### Post by nitzan on 2011-03-23
Thanks, this application seems just about what I need.
But, seems like my ipod has a problem, the gtk ipod says something about bad filesystem..

I'll just take it to work where there's a mac and try to restore the hd, then I'll give it another try.

---

