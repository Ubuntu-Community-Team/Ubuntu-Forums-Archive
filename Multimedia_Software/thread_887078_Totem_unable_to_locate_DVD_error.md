---
title: "Totem unable to locate DVD error"
date: 2008-08-11
forum: Multimedia Software
---

### Post by emge757 on 2008-08-11
Hi, with a new Xubuntu installation, I'm unable to play DVDs. 

Yes, the codecs are loaded, with the Xubuntu-utils.

The DVD shows up on my desktop. But when totem loads, there's an error message: "error, unable to locate"

I'm sure this is probably something simple, TIA.

---

### Post by mc4man on 2008-08-12
The first thing to get out of the way - has a region been set **once** on the dvd drive? If you **know** or have ever used this drive to play commercial (encrypted)  dvds in windows then ignore. Otherwise here's how to ck.
[http://ubuntuforums.org/showthread.php?t=868547&highlight=regionset](http://ubuntuforums.org/showthread.php?t=868547&highlight=regionset)

Note: a region only has to be set once, after that leave it alone

It will be better for dvd movies to install vlc and if you want a totem player install totem-xine and set as default totem player

Why don't you follow this post and then see what you've got
If you know medibuntu has been added to your software sources skip those commands

[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

All of the instr. are good for xubuntu except how to set vlc as default movie player.
For that go Applications -> Settings -> Settings Manager -> Removable Drives and Media -> Multimedia. In the box for Video Cds/Dvds delete what's there and replace with
```
vlc %m
```

If you have any trouble after that run```
 sudo lshw -C disk
``` to ck. on the dvd drive and it's device node and /dev/links

---

