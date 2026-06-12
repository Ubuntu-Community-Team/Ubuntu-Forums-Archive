---
title: "mythbuntu 8.10 clean install, mount points messed up"
date: 2008-11-20
forum: Mythbuntu
---

### Post by ravennium on 2008-11-20
Hi there mythical ppl,

I made a clean install on my HTPC since my old hdd broke down :(
Anyway here comes the problem.
I did let the installer decide hoe to use the hdd. After install I started copying data to my 250GB SATA hdd from my network drive, after 10GB it said that disk was full :confused:

I had installed Kubuntu-desktop after mythbuntu installer, but for some reason I couldn't find those disk management tools from KDE4 ?
So I installed gparted. With that I could see that I have 11GB for use in home folder. For some reason there was approximately 230GB reserved for var/lib :confused:

So what is the easiest way to have that ~200GB for my usage, not for var/lib, surely it doesn't need that amount of space??

edit: Another install where I set the disk usage / /swap etc...? what are the "best" values for those?

edit: here's a screenshot [[IMG]http://img266.imageshack.us/img266/1594/mountjh9.th.jpg[/IMG]](http://img266.imageshack.us/my.php?image=mountjh9.jpg)[[IMG]http://img266.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by fatmonk on 2008-11-20
8.10 uses directories under /var/lib for all its media by default.

By selecting to allow the Myth install to create your partitions its created a small OS partition (about 20GB) and the 230GB for storing media.

You should be copying your data into the relevent folder under /var/lib/mythtv (they're pretty obvious or you can fid them in the setup screens).

Hope this helps,

FM

---

### Post by ravennium on 2008-11-21
Thanks fatmonk, didn't know that, but thought it to be something like that.
I made a clean install now since I use this HTPC also for other things than myth. :)

---

