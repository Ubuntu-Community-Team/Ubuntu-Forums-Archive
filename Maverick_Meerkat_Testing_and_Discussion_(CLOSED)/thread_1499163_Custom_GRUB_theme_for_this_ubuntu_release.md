---
title: "Custom GRUB theme for this ubuntu release"
date: 2010-06-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Flyboarder on 2010-06-01
Is it possible to use grub2 version 1.98 and create a submenu? Or do I need to use burg? I want to make a theme like what is seen on the gfxboot for grub summer of code examples but with submenus.

---

### Post by Slug71 on 2010-06-01
I think you need to use burg.

---

### Post by ranch hand on 2010-06-01
> **Slug71 said:**
> I think you need to use burg.
Yep, he has got this just right.

I do not really go for burg but it is a very fine piece of work that seems to work very well.  

If you use custom menu entries, as I do, it doesn't do much for you but if you are using the generated entries it works very nicely.

There are quite a few themes already made for it so you should have  no trouble figuring out how to make your theme work.

---

### Post by SevenMachines on 2010-06-01
i think the graphical boot stuff for grub is in the experimental branch last i heard, i haven been paying attention to how much works being done on it but let me know how it goes if you try it

{EDIT] yep, burg looks really good, as far as i know it isnt destined for grub main so i havent really used it

---

### Post by ranch hand on 2010-06-01
Here is a link that may be useful if you want to fool around with burg;

[http://ubuntuforums.org/showthread.php?t=1371288&highlight=burg](http://ubuntuforums.org/showthread.php?t=1371288&highlight=burg)

It is from the 10.04-testing forum.

---

### Post by Starks on 2010-06-01
Topic title is really misleading.

Use questions, not declarations!

---

### Post by SevenMachines on 2010-06-04
doh! i should really pay attention :) gfxmenu is already included in the default grub-pc install ( and 10.04 ). i think someone (colin watson(?) ) is working on expanding functionality. i'll see if i can dig out some old stuff about how to play around with it

---

### Post by SevenMachines on 2010-06-04
directhex has put together a basic theme for gfxmenu to play around with [here]("http://www2.apebox.org/wordpress/linux/228/")
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-cd-boot](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-cd-boot)
[https://wiki.ubuntu.com/FoundationsTeam/Specs/MaverickCDBoot](https://wiki.ubuntu.com/FoundationsTeam/Specs/MaverickCDBoot)

[EDIT] Quick screenshot from maverick
[EDIT] Quick butchered gnome dune background by me, with the nice circular progress bar
[EDIT] Looks like submenu's arent there yet but some sort of implementation or 'pop up' submenu is on the cards

---

