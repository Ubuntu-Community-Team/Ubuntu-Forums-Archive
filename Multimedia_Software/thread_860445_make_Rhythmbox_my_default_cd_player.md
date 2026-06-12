---
title: "make Rhythmbox my default cd player"
date: 2008-07-15
forum: Multimedia Software
---

### Post by groundnut on 2008-07-15
At the moment Totem is my default cd player. However it does not play any cd. Instead it says an error occured. Location not found.

In the meantime I've installed Rhythmbox. Now I can play cd's. But it doesn't start automatically after I insert a cd.

How can I make Rhythmbox my default cd player?

kind regards,
Tony

---

### Post by teachop on 2008-07-26
I would like to do this as well.  The closest I was able to come is to get rhythmbox to start up and show the cd contents, but I still have to hit play.  

What I did to get it to start and show the cd right off was:
Settings > Settings Manager > Removable Drives and Media > Multimedia..

Then I changed the command for audio CDs to:
"/usr/bin/rhythmbox /dev/cdrom".  I am stuck from there.

---

### Post by mc4man on 2008-07-26
This is only a guess because I don't have xubuntu (8.04), but it behaves very much like gutsy.
Try this first
```
rhythmbox cdda:/
``` that should work for 1 drive at least
if you have 2 drives and above doesn't work for both drives try
```
rhythmbox %d
``` This should allow it to open even _if you have 2 drives._ Note that in either case you'll still have to click the play button to actually start playback (just the way rhythmbox works)

If you want an app that starts play without user intervention then use Amarok, the command for xubuntu and gutsy in removable drives and media -> multimedia is
```
amarok -cdplay %d
```

---

### Post by Yellow Pasque on 2008-07-26
I believe xfce works the same as gnome in this regard. Use gconf-editor or gksudo gedit /etc/gnome/defaults.list if xfce doesn't have a preferred app GUI.

---

### Post by mc4man on 2008-07-27
> I believe xfce works the same as gnome in this regard. Use gconf-editor or gksudo gedit /etc/gnome/defaults.list decided to take a quick look. What's interesting is that Xubuntu 8.10 like 7.10 uses removable drives and media to set default apps for autoplay yet unlike 7.10 it's defaults.list has lines starting with x-content/...... which are what's used to set a default choice.

It's actually is an exact copy of the one in hardy, including the apps set, some of which aren't even installed.

It's default line for cds is x-content/audio-cdda=rhythmbox.desktop (just like in hardy)

The defaults.list is there but has no influence, at least atm in regards to removable media
There's no volume-manager in gconf-editor but even if there was if would only use the the app with it's default launch command which may be unsuitable.

---

### Post by groundnut on 2008-07-27
Thanks,

Rhythmbox is my default cd-player now.
It works for both drives.
The rhythmbox cdda:/ command was sufficient.

---

