---
title: "After ripping audio disks to .ogg systems fail to properly read new audio disks."
date: 2011-12-04
forum: Multimedia Software
---

### Post by MentatGhola on 2011-12-04
I was ripping cd's to my laptop running 11.10 and all of a sudden disk titles are no longer displayed by my system.  Also banshee is broken.  Here are the links to other threads I have posted on for this issue:

[http://ubuntuforums.org/showthread.php?t=1359894](http://ubuntuforums.org/showthread.php?t=1359894) [http://ubuntuforums.org/showthread.php?t=1586927](http://ubuntuforums.org/showthread.php?t=1586927)

I am starting a new thread because what is worse, now my desktop (running 10.10) after ripping a cd there is having a similer problem.  Audio cd's titles and track listings are unnamed by system and by all players i have tried.  Though i can still run banshee.  

When I try to open the disk from the places tab on the panel I get an error saying: "Could not open location 'cdda://sr0/' Failed to execute child process "sound-juicer" (no such file or directory".  I think this is a banshee problem and ripping cd's in banshee breaks something.

:-x

---

### Post by hansdown on 2011-12-04
Hi,MentatGhola.

Banshee is a little problematic right now.

Try

```
k3b
```

or

```
gnome baker
```

---

### Post by MentatGhola on 2011-12-08
kd3 and gnomebaker aren't in the repository.  to be more specific kd3 isn't located and:

```
sudo apt-get install gnomebaker
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnomebaker is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnomebaker' has no installation candidate

```

Though these seem to be cd burning/imaging apps and im not sure they are quite what im looking for not to mention the very file manager of my system appears to be broken and I have no idea what to do other than reinstall.

I should note:  I discovered that a workaround I attempted in order to run a 32 bit program called Guitar-Pro 6 in 64 bit 11.10, as well as 10.10 on my desktop, may be the culprit here creating conflicts with banshee.  Guitar-Pro support originally posted the workaround and then when a returned a couple months later it appears they retracted it and are now just saying basically that certain libraries that are rolledback/deleted/added cause a break in ubuntu.  Unfortunately I would need to do a reinstall i assume, and try ripping in banshee again to see whether or not this had anything to do with it.  The libs are related to libportaudio2.  This is what I know.  also note the workaround failed in 11.10 but not 10.10. :(

---

### Post by hansdown on 2011-12-08
Libportaudio2 has a few dependencies.

Try installing each dependency, to see if that is the fix.

Here's a link for 11.10

[http://packages.ubuntu.com/oneiric/libportaudio2](http://packages.ubuntu.com/oneiric/libportaudio2)

---

