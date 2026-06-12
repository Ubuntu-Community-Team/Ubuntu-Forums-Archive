---
title: "ConkyWeather disappeared after today's updates."
date: 2011-01-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-01-26
Just an observation! I don't know why though :-(
The rest of my conky display is good.

---

### Post by cecilpierce on 2011-01-26
It stopped working on the AWN applet awhile back, the only way I can see it is the gnome panel calender that comes and goes :(

---

### Post by Quackers on 2011-01-26
I don't have a calendar in conky, so can't comment on that. Everything but the weather forecast is working ok on my conky.

---

### Post by cariboo on 2011-01-26
There seem to be some missing weather applet related packages, missing, as I just got a notification that weather indicator applets weren't going to be installed during updates.

I have a system that is running nouveau drivers that this update wants to remove, so I'm using the aptitude safe-upgrade option.

---

### Post by ronacc on 2011-01-26
just like crackerjack you get a prise in every update:lolflag:

---

### Post by Quackers on 2011-01-26
> **ronacc said:**
> just like crackerjack you get a prise in every update:lolflag:

Lol, I get a surprise on every boot :-)

---

### Post by Quackers on 2011-01-26
I just ran the following updates 
```
gstreamer0.10-tools (0.10.31.3-1) to 0.10.32-1
libgstreamer0.10-0 (0.10.31.3-1) to 0.10.32-1
obexd-client (0.33-1) to 0.39-1
``` 
and conky weather is fixed! I don't know if one of those fixed it, but I haven't done anything else.
BTW some updates for libdrm are showing as available - but in light of cariboo907's top sticky, I declined them. One of them, at least, wants to remove Xorg. Not a good idea, for the moment :-)

---

### Post by Harry33 on 2011-01-27
> **Quackers said:**
> I just ran the following updates 
```
gstreamer0.10-tools (0.10.31.3-1) to 0.10.32-1
libgstreamer0.10-0 (0.10.31.3-1) to 0.10.32-1
obexd-client (0.33-1) to 0.39-1
``` 
and conky weather is fixed! I don't know if one of those fixed it, but I haven't done anything else.
BTW some updates for libdrm are showing as available - but in light of cariboo907's top sticky, I declined them. One of them, at least, wants to remove Xorg. Not a good idea, for the moment :-)

This is because you have upgrade plymouth (0.8.2-2ubuntu1) too.
Then libdrm packages are upgraded.
The naming of the package libdrm-nouveau1 changed to libdrm-nouveau1a.
The old one may be deleted.

---

### Post by Quackers on 2011-01-27
I didn't update the lbdrm packages as I think one of them wanted to remove Xorg iirc.

---

### Post by Quackers on 2011-01-27
I just ran all current updates and all is good:-)
Just one odd thing though, all my partitions now appear in the Unity sidebar as grey boxes with question marks in them. They are not mounted, as such, they are just shortcuts to them, but it's as if it can't find an icon for them. This is new! Nothing similar has happened before. I normally get to them through cairo dock.
Now my sideabr (if that's what it's called :-) ) is full! My trash can is getting squashed :-)

---

### Post by tjeremiah on 2011-01-27
> **Quackers said:**
> I just ran all current updates and all is good:-)
Just one odd thing though, all my partitions now appear in the Unity sidebar as grey boxes with question marks in them. They are not mounted, as such, they are just shortcuts to them, but it's as if it can't find an icon for them. This is new! Nothing similar has happened before. I normally get to them through cairo dock.
Now my sideabr (if that's what it's called :-) ) is full! My trash can is getting squashed :-)

I hope in the coming updates there will be an option to remove the mounts.

---

