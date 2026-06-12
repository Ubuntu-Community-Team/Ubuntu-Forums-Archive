---
title: "Can't find a way to watch dvd images from computer (.iso files)"
date: 2008-06-12
forum: Multimedia Software
---

### Post by alan_daniel on 2008-06-12
Hey all, I'm running 8.04 and have a problem. I have many of my own personal dvd's backed up on an external hard drive in .iso images because it makes for easy organization. I want to be able to watch the dvd's from my computer without going to search for the dvd itself, so I mount the iso just fine (I have a small application that automates it) into /media/iso_image.

The problem is that I cannot find a media player that will play "from a directory." I want it to treat the mounted image as a dvd and play it, menus and everything, but the best I can get it to do is using Totem (I think that's the name of it) and selecting one of the .VOB files (the actual movie files that are split to 1 GB each). This is a problem, because when the part of the movie that is on that particular .VOB is finished, I have to open the next section manually, treating it as if it were a completely different media file. I want to be able to just open the dvd in its entirety from the mounted image.

Am I missing something? I'm guessing there is a completely simple and logical solution to this. Thanks for any help.

---

### Post by wolfen69 on 2008-06-12
```
sudo mkdir /mnt/name_of.iso
```
```
sudo mount -o loop -t iso9660 name_of.iso /mnt/name_of.iso
```

---

### Post by aeiah on 2008-06-12
what i do is assign isos to open with mplayer. then i can just click on the iso and they play. it defaults to playing the largest stream though - ie: it will play the movie with the default language, and not show the menu.

try VLC, i think it may be possible to play .iso files straight into vlc without the need to mount. if it isnt possible perhaps you can just change the dvd drive path in vlc to where you mount your dvd .isos (if you always mount them to the same place)

---

### Post by Vivaldi Gloria on 2008-06-12
I am pretty sure that you can do this by dragging the folder onto vlc. Even dragging the iso might work but not sure about that one.

---

### Post by IanW on 2008-06-12
> **Vivaldi Gloria said:**
> I am pretty sure that you can do this by dragging the folder onto vlc. Even dragging the iso might work but not sure about that one.

Checking........... Confirmed! I can drag an iso onto VLC's window and the menu plays instantly.:popcorn:

---

### Post by disturbedite on 2008-06-12
kaffeine has also supported playing dvd (& prolly vcd, svcd, etc) iso images for quite a while now.

---

### Post by alan_daniel on 2008-06-12
Thanks for everyone's responses! I will try these suggestions out as soon as I can. I still have one question, though. Will these suggestions work with menus? That's one of the main things I want, because a lot of the dvd's I have are episode-driven dvd's like television shows, so I need to be able to select the episode I want.

---

### Post by mc4man on 2008-06-13
W> will these suggestions work with menus? Whatever your particular player is capable of will be the same whether you open from a directory (disk or video_ts on hdd) or from an .iso. Most of the major players support drag and drop, all can be added to the r.click open with. You can set a default r. click or double click thru r.click -> properties. If you want to browse to a .iso it is a file. (not directory)

---

### Post by Vivaldi Gloria on 2008-06-13
> **alan_daniel said:**
>  Will these suggestions work with menus?

Yes.

---

### Post by IanW on 2008-06-13
> **alan_daniel said:**
> Will these suggestions work with menus?
As I posted earlier:-
> **IanW said:**
> I can drag an iso onto VLC's window and the [COLOR="Red"]menu[/COLOR] plays instantly

---

### Post by jis on 2009-06-06
For me ```
xine dvd://image.iso
``` works best in ubuntu 9.04. I did not find a way to launch a DVD image by opening the file in xine's graphical user interface, though.

---

