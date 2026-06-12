---
title: "Songbird installs again everytime i start it up?"
date: 2008-05-06
forum: Multimedia Software
---

### Post by UndeadAlex on 2008-05-06
hey guys, i just installed songbird using the .deb.
every time i start it up, i have to agree to the terms and conditions and somewhat "install" it again
has anyone experienced this?
i need help cause i really like Songbird

---

### Post by erick.mendes on 2008-06-03
I got the exactly same issue over here, it started after I installed some Ubuntu updates, but I don't know if there's any relation.

Im using Hard Heiron fully updated, and I'm having the same issue on Songbird 0.5 and 0.6rc2 build 20080530003727, and, btw, it's pretty annoying.

One more thing happen to me:

It also created 4 "download" songbird bookmark when you execute it, and every time you close it, execute it again, accept the ULA again, choose the language again, it creates one more "download" bookmark...

That's annoying me a lot, because I'm loving Songbird, till that started.


ps.: Here's the list of my recent updates, so if anyone got any idea if an update maybe the cause of it, stand up and leave an message.

Jun 03 2008:

Upgraded the following packages:
linux-libc-dev (2.6.24-17.31) to 2.6.24-18.32
linux-restricted-modules-common (2.6.24.12-17.36) to 2.6.24.13-18.41


Jun 02 2008:

Updated(?) the following packages:
eog (2.22.1-0ubuntu2) to 2.22.2-0ubuntu1
evince (2.22.1.1-0ubuntu1) to 2.22.2-0ubuntu1
file-roller (2.22.2-0ubuntu1) to 2.22.3-0ubuntu1
gcalctool (5.22.1-0ubuntu1) to 5.22.2-0ubuntu1
gedit (2.22.1-0ubuntu1) to 2.22.3-0ubuntu1
gedit-common (2.22.1-0ubuntu1) to 2.22.3-0ubuntu1
gnome-applets (2.22.1-0ubuntu2) to 2.22.2-0ubuntu1
gnome-applets-data (2.22.1-0ubuntu2) to 2.22.2-0ubuntu1
gnome-keyring (2.22.1-1ubuntu1) to 2.22.2-0ubuntu1
gnome-menus (2.22.1-0ubuntu1) to 2.22.2-0ubuntu1
gnome-panel (1:2.22.1.3-0ubuntu1) to 1:2.22.2-0ubuntu1
gnome-panel-data (1:2.22.1.3-0ubuntu1) to 1:2.22.2-0ubuntu1
gtkhtml3.14 (3.18.1-0ubuntu1) to 3.18.2-0ubuntu1
gvfs (0.2.3-0ubuntu5) to 0.2.4-0ubuntu1
gvfs-backends (0.2.3-0ubuntu5) to 0.2.4-0ubuntu1
gvfs-fuse (0.2.3-0ubuntu5) to 0.2.4-0ubuntu1
libeel2-2 (2.22.1-0ubuntu1) to 2.22.2-0ubuntu1
libeel2-data (2.22.1-0ubuntu1) to 2.22.2-0ubuntu1
libgnome-keyring0 (2.22.1-1ubuntu1) to 2.22.2-0ubuntu1
libgnome-menu2 (2.22.1-0ubuntu1) to 2.22.2-0ubuntu1
libgtkhtml3.14-19 (3.18.1-0ubuntu1) to 3.18.2-0ubuntu1
libgvfscommon0 (0.2.3-0ubuntu5) to 0.2.4-0ubuntu1
libpam-gnome-keyring (2.22.1-1ubuntu1) to 2.22.2-0ubuntu1
libpanel-applet2-0 (1:2.22.1.3-0ubuntu1) to 1:2.22.2-0ubuntu1
python-gmenu (2.22.1-0ubuntu1) to 2.22.2-0ubuntu1
seahorse (2.22.1-0ubuntu2) to 2.22.2-0ubuntu1

---

### Post by erick.mendes on 2008-06-03
Btw, I've openned an Post on Songbird forum for this issue too, in hope someone help us out:

[http://www.songbirdnest.com/node/3231](http://www.songbirdnest.com/node/3231)

---

### Post by erick.mendes on 2008-06-03
Just found a way to workaround this issue:

I've tried to launch songbird using "gksu songbird", instead as trying to launch it from my user.

Just to make it clear: the songbird folder is owned by my user and my group. Still, everytime I try to launch it, it was showing me the ULA and language screen.

Now with "gksu songbird" it's working flawlessly. By the little knowledge I got in linux, I suppose the problem is that I'm not the onwer of the folder where Songbird stores the information that it already presented me that innitial screen, or am I wrong?

A buddy suggested to deleted songbirds's folder in the "/tmp" folder. No sucess, got ULA again. 

Well, "gksu songbird" is working, so for now I'm saved.

---

### Post by UndeadAlex on 2008-06-07
im so happy, i got it to work, i just got the new tar.gz file from the songbird site(amd version) and downloaded to desktop. then extracted the file, and put it in my user folder, and then ran it. somehow it got installed and stays that way =]

---

