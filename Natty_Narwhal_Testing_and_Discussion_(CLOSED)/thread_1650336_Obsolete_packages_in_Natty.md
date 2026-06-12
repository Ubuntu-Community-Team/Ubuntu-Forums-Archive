---
title: "Obsolete packages in Natty"
date: 2010-12-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-12-21
I am starting to accumulate quite a few obsolete packages in my Natty test installation. Should I try to remove them, or just leave well enough alone?

Here is the current list:
> 
gir1.0-panelapplet-3.0
gir1.0-atk-1.0
gir1.0-freedesktop
gir1.0-gconf-2.0
gir1.0-gdkpixbuf-2.0
gir1.0-glib-2.0
gir1.0-gtk-2.0
gir1.0-gtk-3.0
gir1.0-pango-1.0
libdbusmunu-gtk1
libfolks-telepathy0
libfolks0
libgirepository1.0-1
adobeflashplugin
Thanks,
Tim

---

### Post by cariboo on 2010-12-21
I've removed them on my installs, with zero problems.

---

### Post by zika on 2010-12-21
> **ratcheer said:**
> I am starting to accumulate quite a few obsolete packages in my Natty test installation. Should I try to remove them, or just leave well enough alone?

Here is the current list:
Thanks,
TimAs far as I can see some of them are tied to some packages not so easy to get rid of... But, that is just me (or apt)...
Do they, really, bother You...?

---

### Post by cariboo on 2010-12-21
I've run into a bit of a strange one here. Yesterday I did a CLI install using the alternate iso, in oder to do some Gnome 3 testing. I installed the gnome-desktop-environment and the packages from gnome 3 builds ppa, along with gnome-shell from the ricotz testing ppa.

When using aptitude to install a package, It asks me if I want to remove 230 obsolete packages, that don't show up in synaptic.

As an aside when I installed the gnome-desktop-environment, I got all the debian branding, wallpaper and themes. I've sort of screwed the theming up a bit by trying to use the Ambiance theme, as all the blue was getting to me. :)

---

### Post by Harry33 on 2010-12-21
> **ratcheer said:**
> I am starting to accumulate quite a few obsolete packages in my Natty test installation. Should I try to remove them, or just leave well enough alone?
...

Those packages are all old. For example gir1.0 packages are now gir1.2 packages and libgirepository1.0-1 is now libgirepository-1.0-1. This is why they are not supported and they have been removed from official repos.

If you want to be absolutely sure, completely remove them one by one with synaptic.
It will tell you then, what dependants are also removed.

---

### Post by Harry33 on 2010-12-21
> **cariboo907 said:**
> I've run into a bit of a strange one here. Yesterday I did a CLI install using the alternate iso, in oder to do some Gnome 3 testing. I installed the gnome-desktop-environment and the packages from gnome 3 builds ppa, along with gnome-shell from the ricotz testing ppa.

When using aptitude to install a package, It asks me if I want to remove 230 obsolete packages, that don't show up in synaptic.

As an aside when I installed the gnome-desktop-environment, I got all the debian branding, wallpaper and themes. I've sort of screwed the theming up a bit by trying to use the Ambiance theme, as all the blue was getting to me. :)

I do not have installed the package gnome-desktop-environment.
Isn't the package gnome-settings-daemon_2.91.5.* breaking the GTK+2 theming?
I noticed that gdm lost its background and the session gnome-classic did not anymore have adjustable theming. The only one there was really ugly (looked like the one named "Simple").

---

### Post by ratcheer on 2010-12-21
> **zika said:**
> 
Do they, really, bother You...?

Not really, I guess. I just like to clean out the crud, as long as it is really crud.

Thanks,
Tim

---

### Post by ratcheer on 2010-12-21
> **Harry33 said:**
> Those packages are all old. For example gir1.0 packages are now gir1.2 packages and libgirepository1.0-1 is now libgirepository-1.0-1. This is why they are not supported and they have been removed from official repos.

If you want to be absolutely sure, completely remove them one by one with synaptic.
It will tell you then, what dependants are also removed.

Thank you, that is pretty much how I thought I should do it.

Tim

---

### Post by cariboo on 2010-12-21
> **Harry33 said:**
> I do not have installed the package gnome-desktop-environment.
Isn't the package gnome-settings-daemon_2.91.5.* breaking the GTK+2 theming?
I noticed that gdm lost its background and the session gnome-classic did not anymore have adjustable theming. The only one there was really ugly (looked like the one named "Simple").

I thought I'd just try it, to avoid installing anything Unity related. I've got a GDM background that I haven't been able to find yet, but this setup uses the Debian spacefun-grub and spacefun-desktop.

As the day continues, I'm finding more and more of the smaller applications that aren't running like, gedit, character map and screenshot. When running the standard two panel desktop, I can change theming, but gnome-shell won't even bring up the Appearances window.

[IMG]http://i.imgur.com/LuCNXl.jpg[/IMG]

 [IMG]http://i.imgur.com/FtBjLl.jpg[/IMG]

---

### Post by zika on 2010-12-22
> **cariboo907 said:**
> I thought I'd just try it, to avoid installing anything Unity related. I've got a GDM background that I haven't been able to find yet, but this setup uses the Debian spacefun-grub and spacefun-desktop.

As the day continues, I'm finding more and more of the smaller applications that aren't running like, gedit, character map and screenshot. When running the standard two panel desktop, I can change theming, but gnome-shell won't even bring up the Appearances window.

[IMG]http://i.imgur.com/LuCNXl.jpg[/IMG]

 [IMG]http://i.imgur.com/FtBjLl.jpg[/IMG]cariboo907 for the President of Unity-free Republic...

---

### Post by cariboo on 2010-12-22
I've still got 4 other Natty installs running Unity. :)

---

### Post by seeker5528 on 2010-12-22
> **cariboo907 said:**
> When using aptitude to install a package, It asks me if I want to remove 230 obsolete packages, that don't show up in synaptic.

But aptitude doesn't *say* they are obsolete, just that they will be removed, correct?

Aptitiude, in addition to wanting to remove the obsolete files, also wants to remove anything *it* thinks is auto-removable. What aptitude views as auto-removable is not necessarily identical to the list of things Synaptic views as auto-removable and in both cases you may not always want to get rid of *all* the things that are identified as auto-removable.

Obsolete files are obsolete, but may be something you installed from someplace not in your sources.list files, may be something that is only temporarily unavailable until the upgraded version makes it into the repositories, may be something you have to keep because something else you have installed still depends on it.

Usually I will keep obsolete packages for a while unless I recognize there is a 'newer but differently named because of binary incompatibly' package, the package is identified as a dummy/transitional package, the changlog in another package indicates the package in question is no longer used, it's something I recognize but just don't care *that* much about.

Later, Seeker

---

### Post by cariboo on 2010-12-22
That's true, aptitude says they are auto-removable. I don't have any obsolete or auto-removable packages listed in synaptic.

---

### Post by lidex on 2010-12-25
Interesting. When I mark 'libdbusmenu-gtk1' for removal, synaptic threatens to remove Cairo-Dock. Marking 'libgirepository-1.0-1' threatens probably forty packages, including firefox.

---

### Post by mc4man on 2010-12-25
libgirepository1.0-1 was updated (renamed to ) libgirepository[COLOR="Red"]-[/COLOR]1.0-1, and as seen you wouldn't want to remove

---

### Post by Harry33 on 2010-12-25
> **lidex said:**
> Interesting. When I mark 'libdbusmenu-gtk1' for removal, synaptic threatens to remove Cairo-Dock. Marking 'libgirepository-1.0-1' threatens probably forty packages, including firefox.

You really should not remove libgirepository-1.0-1 just like mc4man just wrote.
The package you can remove (old and deprecated, removed from repos) is this
libgirepository1.0-1.

Then, also the package libdbusmenu-gtk1 is old and removed from official repos).
So, no package in repos is depending on it. You can remove it.

Cairo-dock (latest version in repos is 2.2.0~4-0ubuntu1) depends only on two packages:
- cairo-dock-core
- cairo-doc-plug-ins

Of those, cairo-dock-plug-ins depends on libdbusmenu-gtk2
but not libdbusmenu-gtk1.

So what version of cairo-dock do you have installed?

Generally you should install the package deborphan.
Then in terminal just run:
deborphan
It will then tell you what packages are no longer needed by any other package and can be removed.

---

### Post by lidex on 2010-12-25
> **mc4man said:**
> libgirepository1.0-1 was updated (renamed to ) libgirepository[COLOR="Red"]-[/COLOR]1.0-1, and as seen you wouldn't want to remove

Ahh, way to be observant (is that a word?), mc4man. BTW, I have seen your work and I am impressed.
As for cairo-dock, I am using ppa version 2.2.1~0alpha1, blah blah blah maverick.

Merry Xmas guys.

---

### Post by Harry33 on 2010-12-25
> **lidex said:**
> Ahh, way to be observant (is that a word?), mc4man. BTW, I have seen your work and I am impressed.
As for cairo-dock, I am using ppa version 2.2.1~0alpha1, blah blah blah maverick.

Merry Xmas guys.

Well well lidex,
this is a Natty Narwhal Testing and Discussion Forum, not for Maverick.
The Natty gobject-introspection ABI naming change, that was uploaded with the version 0.9.12+git20101124-0ubuntu, did not, and will not happen in Maverick.

So this thread does not apply to you.

---

### Post by lidex on 2010-12-25
Yeah, but I am using Natty here and ppa version of cairo-dock. So is latest version as far as I can tell.
```
2.2.1~0alpha1~20101203-0ubuntu1~ppa0~maverick
```

---

