---
title: "How do I change the screen res?"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by chris9902 on 2006-07-29
I'm using my laptop to run ubuntu now and have everything up and running but my screen res is way off.

It's running at 1024x768 but should be 1280x960. I don't have any option for it in the drop down and don't know how to change it.

I did a search and got lots of stuff about nVidia and ATI cards but my gaphics card is just a built in Intel thing.

can anyone help, thanks.

---

### Post by Jagot on 2006-07-29
If it is an onboard Intel chip then you probably need 915resolution.  Enable the universe repo then:

```
sudo aptitude update
sudo aptitude install 915resolution
```

It comes with instructions in /usr/share/doc/915resolution/ but with my laptop it automatically detected the native resolution and just required me to kill the xserver and reload to get it working.

---

### Post by chris9902 on 2006-07-30
hi, thank you for the reply but it's not doing anything. I'm a total newbie so i'm sure it's me but it just says this

```
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "915resolution"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

