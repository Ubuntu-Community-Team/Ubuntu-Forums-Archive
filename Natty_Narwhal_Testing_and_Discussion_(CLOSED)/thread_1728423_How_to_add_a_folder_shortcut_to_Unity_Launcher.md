---
title: "How to add a folder shortcut to Unity Launcher"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DogMatix on 2011-04-13
I have a network drive and I would simply like to add a shortcut to it to the Unity Launcher. I know how to add shortcuts to applications but I'm banging my head on the wall trying to figure this out. I tried searching for related posts but have not found out how. Surely this is in fact simple and I've missed something obvious.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-13
It's pretty simple, you just have to write a .desktop file that starts nautilus in a given folder, give it execute permissions and drag it to the launcher.

---

### Post by DogMatix on 2011-04-13
How would I go about that?

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-13
> **DogMatix said:**
> How would I go about that?

Look at some of the .desktop files in /usr/share/applications . Most of the syntax is self-explanatory.

I love unity, it really brings back some of that old GNU/UNIX do-it-yourself spirit by removing sane configuration tools.

---

### Post by DogMatix on 2011-04-13
Cheers man. Think I've cracked it.

Yep! loving Unity too.

---

### Post by coffeecat on 2011-04-13
Make a desktop launcher by right-clicking on the desktop and choose "create launcher" For the command you'll need 'nautilus /path/to/folder' for a non-network folder. For a network folder I would guess something like 'nautilus smb://192.168.1.64/sharename/' or 'nautilus smb://hostname/sharename/' or whatever network protocol you use. You'll have to experiment and see what works. Once you've made the desktop launcher, simply drag it to the dock.

---

### Post by DogMatix on 2011-04-13
Thanks. Did not know about the right>click to create launcher.

Great tip.

---

### Post by coffeecat on 2011-04-14
Yes, I've found it useful.

I was in gnome-shell last night when I posted this and wasn't able to test it.

> **coffeecat said:**
> For a network folder I would guess something like 'nautilus smb://192.168.1.64/sharename/' or 'nautilus smb://hostname/sharename/' or whatever network protocol you use.

I've just tried 'nautilus smb://hostname/sharename/' with my NAS and it works just fine. Now to find an icon that doesn't look like the shell of a marine creature. :)

---

