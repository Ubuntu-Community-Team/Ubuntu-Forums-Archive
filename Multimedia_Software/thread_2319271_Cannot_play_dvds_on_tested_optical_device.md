---
title: "Cannot play dvds on tested optical device"
date: 2016-04-02
forum: Multimedia Software
---

### Post by robert48 on 2016-04-02
Hello

I have been trying to play a dvd on my Ubuntu 15.10 64bit AMD chipped desktop. I have not played a dvd for a while. The attempt failed using both vlc and video player (totem??). I run with pre-released updates. Error message from vlc is:-  
 [COLOR=#ff0000]
Playback failure:[/COLOR]

 [COLOR=#000000]DVDRead could not read block 0.[/COLOR]


I took the physical optical out and changed it with one from a near identical machine running the same version of Ubuntu. When trying again with this known working optical drive it failed to run the dvd on my machine. The machine I swoped drives with runs both optical drives successfully and both play the dvd. One difference noted is the successful machine is Intel chipped.

 So I think I am looking at a driver issue in my AMD chipped machine.

Can you help please?

EDIT

Upon further research from Ubuntu Help I found that I lacked the appropriate css software. problem resolved with:-

```
[LEFT][COLOR=#3C3C3C][FONT=monospace]sudo /usr/share/doc/libdvdread4/install-css.sh[/FONT][/COLOR][/LEFT]
```

---

### Post by ajgreeny on 2016-04-02
To help others, please mark the thread as SOLVED from the Thread Tools menu up top.

---

