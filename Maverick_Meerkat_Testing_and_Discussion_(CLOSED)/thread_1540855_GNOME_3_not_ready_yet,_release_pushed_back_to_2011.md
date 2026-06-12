---
title: "GNOME 3 not ready yet, release pushed back to 2011"
date: 2010-07-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by CoreyB. on 2010-07-28
[GNOME 3 not ready yet, release pushed back to 2011]("http://arstechnica.com/open-source/news/2010/07/gnome-3-not-ready-yet-release-pushed-back-to-2011.ars")

---

### Post by sikander3786 on 2010-07-28
Not a good news anyway but Maverick Meerkat was never going to have GNOME 3 included. It was already announced by Ubuntu Developers.

And don't think that Ubuntu 11.04 has any chances of including GNOME 3. Not confirmed even for 11.10. Fair chances for 11.10 if it gets released before April, May 2011.

---

### Post by jpeddicord on 2010-07-28
> **sikander3786 said:**
> Not a good news anyway but Maverick Meerkat was never going to have GNOME 3 included. It was already announced by Ubuntu Developers.

Maverick wouldn't have GNOME *Shell*. The other components of what would have been GNOME 3 would still be available.

---

### Post by go7Ul1ai on 2010-07-28
Absolutely typical.

---

### Post by hugmenot on 2010-07-28
I hope we can get some or all of Gnome 2.32 in. Some modules had good progress.

---

### Post by wilee-nilee on 2010-07-28
> **lee.jarratt said:**
> Absolutely typical.

Like using a bar chord on the guitar eh, lol.

---

### Post by cyberkilla on 2010-07-28
Quite a lot on their plate this time around.

The GNOME Shell stuff does look fancy, but graphics cards in Linux /rarely/ work properly first time (or ever, in some cases).

GNOME Shell doesn't support computers without 3D compositing enabled. What is the fall-back?

Well, the most obvious fall-back I can think of is to GNOME-Panel, a Nautilus desktop and Metacity. So, when you switch to/from a driver with 3D compositing, you change user interface paradigms too!

I'm not sure how much of a problem that will be to most people, but it seems like a strange situation to me.

Just to ensure that new users aren't greeted with little more than an empty screen after installation, a fall-back will need to be available, which means that GNOME Shell always has to be installed alongside something more reliable.

That's what bugs me about it. There aren't really any parallels you can draw from other OS's/DE's. If you don't meet the specs (or have some other problem) in Windows' Aero or KDE, you typically find yourself using the same menus, toolbars, tray icons, etc., but without the advanced visual effects.

With GNOME Shell, the menu system, notification icons, etc., seem to require compositing to be operational.

---

### Post by go7Ul1ai on 2010-07-28
> **wilee-nilee said:**
> Like using a bar chord on the guitar eh, lol.

It's funny because I don't use many barre chords in my music ^_^

Anyway, to keep on topic...

---

### Post by wilee-nilee on 2010-07-28
> **lee.jarratt said:**
> It's funny because I don't use many barre chords in my music ^_^

Anyway, to keep on topic...

I figured you didn't, most accomplished guitar players don't need them generally, just giving a fellow musician a hard time. ;)

---

### Post by ronacc on 2010-07-28
Well we got a reprieve this time , pray for further delays , like until 2111 .

---

### Post by Finalfantasykid on 2010-07-28
Somewhat dissapointing, but the right decision IMO, as the current Gnome shell has quite a few issues.

If the end result looks anything like that mockup, it will definitly be worth it.

---

### Post by cariboo on 2010-07-28
It looks quite similar to the Unity netbook desktop.

---

### Post by 23meg on 2010-07-28
Here's the official announcement on devel-announce-list:

[http://mail.gnome.org/archives/devel-announce-list/2010-July/msg00003.html](http://mail.gnome.org/archives/devel-announce-list/2010-July/msg00003.html)

---

### Post by Starks on 2010-07-29
Shell hasn't improved exponentially over the past 6 months like people hoped it would. The delay reflects both this and the animosity towards the project.

---

### Post by amano on 2010-07-29
> **jpeddicord said:**
> Maverick wouldn't have GNOME *Shell*. The other components of what would have been GNOME 3 would still be available.

Nope. Maverick would have sticked with GTK+ 2, while many GNOME 3 components required GTK+ 3. Thus Maverick would have shipped at best just some GNOME 3 components that still compiled for GTK+ 2 or were easy to backport.

---

### Post by seeker5528 on 2010-07-29
> **amano said:**
> Nope. Maverick would have sticked with GTK+ 2, while many GNOME 3 components required GTK+ 3. Thus Maverick would have shipped at best just some GNOME 3 components that still compiled for GTK+ 2 or were easy to backport.

:-?:-?:-?

Gnome will still have a release at the scheduled time and as far as gtk, gconf, and other base components are concerned it will be more or less the same as it would have been if it had be labeled Gnome 3 correct?

Just because there was no intention of including Gnome shell doesn't mean there was an intention to backport anything to Gnome 2. Where would be the sense in that? It would just be a lot of extra work for little or no gain.

Later, Seeker

---

### Post by Mr. Picklesworth on 2010-07-29
> **seeker5528 said:**
> :-?:-?:-?

Gnome will still have a release at the scheduled time and as far as gtk, gconf, and other base components are concerned it will be more or less the same as it would have been if it had be labeled Gnome 3 correct?

Just because there was no intention of including Gnome shell doesn't mean there was an intention to backport anything to Gnome 2. Where would be the sense in that? It would just be a lot of extra work for little or no gain.

Later, Seeker

Based on [the thread on the Gnome desktop-devel mailing list]("http://mail.gnome.org/archives/desktop-devel-list/2010-July/msg00133.html"), it sounds uglier than that to me. I could be reading it wrong, though.

The trouble is lots of modules have been ported specifically to use Gtk3 (and a few other Gnome 3 goodies), dropping legacy stuff and incorporating newer stuff. Now they're needing to backtrack &#8230; or just stick with the current stable version + some backported changes.

Don't take my word for it, though. This will probably become a lot clearer soon.

---

### Post by Slug71 on 2010-07-29
Meh, im liking the XFCE desktop better anyways.

---

### Post by seeker5528 on 2010-07-30
> **Mr. Picklesworth said:**
> The trouble is lots of modules have been ported specifically to use Gtk3 (and a few other Gnome 3 goodies), dropping legacy stuff and incorporating newer stuff. Now they're needing to backtrack … or just stick with the current stable version + some backported changes.

The GTK2 versus GTK3 sounded like a minor issue or non-issue in many cases if the advice about maintaining the option to compile with either version until some time after the Gnome3 release was followed. 

For things that depend on things that won't be released now, current stable + backported changes is always an option.

Don't know how much any of this will affect Ubuntu. It seems like mostly this will be sorted out upstream and Ubuntu devs will just need to decide what to include. In cases where the only real issue is that the Gnome devs don't want to put out a release where some of the Gnome modules use the new stuff and some use the old stuff, Ubuntu devs could choose to still include these newer things. 

Later, Seeker

---

### Post by teh603 on 2010-07-31
> **Slug71 said:**
> Meh, im liking the XFCE desktop better anyways.Yeah, I was going to suggest if they hate Gnome 3 that much they try Kubuntu and see if they like KDE better. If one desktop environment is that much of a headache, there's others waiting in the wings...

---

### Post by x-shaney-x on 2010-07-31
Well in my case I moved to gnome BECAUSE of KDE 4 and I still don't get on with it so I'm stuffed if they mess Gnome 3 up.

And I just don't like the alternative environments either.

---

### Post by darkstaar on 2010-07-31
> **CoreyB. said:**
> GNOME 3 not ready yet, release pushed back to 2011

...which means that my return to the K Desktop Environment will likely be pushed back to 2011.

---

### Post by MCVenom on 2010-07-31
> **darkstaar said:**
> ...which means that my return to the K Desktop Environment will likely be pushed back to 2011.
It's not K Desktop Environment, it's KDE Software Compilation, sheesh :P

---

### Post by teh603 on 2010-08-11
> **x-shaney-x said:**
> Well in my case I moved to gnome BECAUSE of KDE 4 and I still don't get on with it so I'm stuffed if they mess Gnome 3 up.Honestly, the only pre-KDE 4 system I've used was a POS running Xandros, with a package manager so broke it wouldn't resolve even one tier of dependencies and not enough disk space to run updates thanks to the stupidity that is a small drive with a UnionFS install designed to prevent updating.

I moved from Gnome to KDE because of the easy theme installation. Gnome's themes aren't well-packaged, and some of them just aren't as nice as the KDE ones. I stayed because of the document quicklaunch.

---

