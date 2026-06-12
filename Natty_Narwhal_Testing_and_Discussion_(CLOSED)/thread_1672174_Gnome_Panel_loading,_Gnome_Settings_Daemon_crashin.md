---
title: "Gnome Panel loading, Gnome Settings Daemon crashing in desktop session?"
date: 2011-01-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2011-01-20
This has been happening to me on a pristine, up to date install of Natty inside VirtualBox 4 (with 3D support). When I log in to the Unity desktop, the Gnome panel loads (as well as Compiz, with Unity and all that). Every single panel applet fails to load, each one throwing its own angry error message. Then, most of the time, Gnome Settings Daemon crashes and I get that wonderful unthemed GTK thing going on. Unity and the panel continue to fight each other for dominance at the top of the screen.
(Does it sound nasty enough yet?)

When I load the Classic desktop, everything is a lot happier and Gnome Settings Daemon does not crash.

Does this happen to anyone else? Any idea what this may be, or if there's a bug report for it?

---

### Post by lzfy on 2011-01-20
I got the same problem under VB4 with 3D. And since the last update it seems that unity isn't installed anymore. When I run unity --replace I get the message "The program 'unity' is currently not installed.  You can install it by typing: sudo apt-get install unity" 

When I try to install unity I get:
>  unity : Depends: libnux-0.9-0 (< 0.9.16) but 0.9.16-0ubuntu1 is to be installed
         Depends: libunity3 (>= 3.2.0) but it is not going to be installed
E: Broken packages

---

### Post by mc4man on 2011-01-20
> pristine, up to date install of Natty
There was awhile ago some similar intermittent behavior in real installs (both here and others)

Haven't seen it at all as of late though I now tend to do a fresh install every week or less.
No sure what "pristine" means but there is a strong possibility that an install from X days/weeks ago plus updates may not equal an install from the current state of 'today' (plus any add. updates )

---

### Post by ruik on 2011-01-21
I'm having exactly the same problem!

---

### Post by cecilpierce on 2011-01-21
there must be some file to edit or delete to get gnome-panel to stop loading in the desktop version of unity, does anyone know ???  :p

---

### Post by ronacc on 2011-01-21
as far as the applets failing to load I get that here on classic desktop every boot , reload them and all is well , seems like a timing problem as to when they are loaded .

---

### Post by pressureman on 2011-01-21
Yep, still happening to me too, on classic desktop. I think classic desktop is being giving very low priority by the devs at the moment. If it's still a problem when 11.04 is released, I'll be thinking hard about switching to a different distro. I don't want to be railroaded into using Unity.

---

### Post by Mr. Picklesworth on 2011-01-27
Okay, new stuff!
With the latest bunch of updates, the Gnome Panel problem is gone; it does not load in the Unity desktop session.

Gnome Settings Daemon is still having its problem. Seems to cooperate if I kill the existing process (it doesn't crash, it turns out; just malfunctions) and run it from a terminal. Just doesn't like to run at session start for some reason.
Does anyone know where / if it writes a log file?

---

### Post by pressureman on 2011-01-27
It should log to ~/.xsession-errors

---

### Post by Harry33 on 2011-01-28
> **Mr. Picklesworth said:**
> 
... 
Gnome Settings Daemon is still having its problem. Seems to cooperate if I kill the existing process (it doesn't crash, it turns out; just malfunctions) and run it from a terminal. Just doesn't like to run at session start for some reason.
Does anyone know where / if it writes a log file?

This is the bug #649809
[https://bugs.launchpad.net/ubuntu/+s...x?comments=all](https://bugs.launchpad.net/ubuntu/+s...x?comments=all)

After an unsuccessfull boot (ugly theme appears) you will find these warnings in the file .xsession-errors:

```
** (gnome-settings-daemon:1641): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:1641): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

```
and then selecting a theme only changes the titlebar, not icons nor window content.

It has been said this happens commonly on fast hardware and setups, like on SSD systems and powerfull processors. Also it seems to affect more systems with a fast NVidia graphics card with binary drivers (nvidia-current).
And yes, in Ubuntu.

**There is a good workaround:**
Change the following line in the file /etc/xdg/autostart/gnome-settings-daemon:
```

Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon

```
to this:
```

Exec=bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

```

You may also try the value "sleep 1; ..."
That means the system will wait 1 sec instead of 2 sec.

---

### Post by Mr. Picklesworth on 2011-01-28
Great! Thanks for the detailed post, Harry33 :)
Unfortunately, that workaround didn't seem to work. But it sounds like my problem, so I'll keep an eye on the bug report and see what happens…

Your link is broken, by the way, so for anyone else that's this bug here: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

---

