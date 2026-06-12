---
title: "Can I use Unity2D instead of 3D?"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by t1497f35 on 2011-04-24
Hi,
I installed Nvidia binary drivers and it defaulted to Unity3D, but after a day of using it I found out that despite it looking cool etc I have to cope with too many bad trade-offs, so I wonder if I can use Unity2D instead?
Today I logged out and chose "classic" but this imo isn't Unity2D.

---

### Post by Elfy on 2011-04-24
It's not.
[https://wiki.edubuntu.org/Unity2D](https://wiki.edubuntu.org/Unity2D)

---

### Post by Hreinsi on 2011-04-24
> **t1497f35 said:**
> Hi,
I installed Nvidia binary drivers and it defaulted to Unity3D, but after a day of using it I found out that despite it looking cool etc I have to cope with too many bad trade-offs, so I wonder if I can use Unity2D instead?
Today I logged out and chose "classic" but this imo isn't Unity2D.

one of my computers dont support 3d so i did  sudo apt-get install unity-2d 

works fine

---

### Post by t1497f35 on 2011-04-24
Thanks, so I wonder if I can use Unity2D with Nvidia proprietary drivers (GeForce 9600gt).

---

### Post by t1497f35 on 2011-04-24
> **Hreinsi said:**
> one of my computers dont support 3d so i did  sudo apt-get install unity-2d 

works fine
Thanks a lot, installing..

EDIT: tried out 2D looks and behaves a lot like 3D so I'll stick with classic.

---

### Post by Hreinsi on 2011-04-24
im running GeForce 8400 GS works like great but my old fx 5200 dont run whith 173 driver i used in 10.10

there are some discussions here about nvidia just look for it og google it

---

### Post by Elfy on 2011-04-24
> **t1497f35 said:**
> Thanks a lot, installing..

EDIT: tried out 2D looks and behaves a lot like 3D so I'll stick with classic.

If you dislike it that much try a different environment.

---

### Post by terry_gardener on 2011-04-24
> **t1497f35 said:**
> Hi,
I have to cope with too many bad trade-offs, 

out of interest what are the trade offs

---

### Post by t1497f35 on 2011-04-24
> **terry_gardener said:**
> out of interest what are the trade offs
I'd only say in private cause I'm trying this not to evolve into a Unity3D rant, I'm pretty sure the Unity devs are aware of them (all) and I expect them to fix them by 11.10.

---

### Post by FootySr on 2011-04-24
> **t1497f35 said:**
> I'd only say in private cause I'm trying this not to evolve into a Unity3D rant, 
I'm with Terry, I'd love to hear what you have to say as part of a mature conversation. Let the mods deal with the negative ninnies. ;)

---

### Post by Elfy on 2011-04-24
Thanks ... ;)

---

### Post by t1497f35 on 2011-04-24
Well.. here are a few issues, remember I'm not the type of guy who's eager spending hours on google trying out hit and miss solutions so I didn't bother much trying to fix them myself.
1) The launchers and currently running apps are on one pane (left vertical one) so I have to do issue extra brain cycles to sort out which ones are launchers and which ones are running apps, plus launching a new app is tricky when same instance of app already runs, sometimes it doesn't work, not gonna issue examples. That also means I have to do more clicks and mouse moves.
2) The left panel once refused to hide at all so I had to log out/in, not sure if it's by design, a bug or my fault.
3) Dropping something on the left vertical panel only works for .desktop files, dropping a location (file/folder) doesn't seem to work, nor an executable file (in win7 and old Gnome it does work though)
4) Rearranging icons (by mouse drag-n-drop) doesn't work (but, for example, it does work in Win7 and in classic Gnome panels).
5) There might be more issues but sorry I'm just too lazy to do a deep analysis since I'm pretty sure it's redundant, plus there are extra annoyances introduced by Canonical, i.e. I don't like the new system tray cause it's yet another (bad) trade-off where, for example, to make Transmission show up I now have to do 4 moves instead of 2, that is, instead of moving the mouse to the tray icon and clicking it as in the "good old days", I now have to move the mouse over it, click it, choose the "show app or so" and click again - not a big deal but these extra moves become an annoyance and waste of time, no matter how cute they might look. Plus I can't close notifications to get rid of them before they time out, keeping the mouse over them is to me a lame solution, and other stuff.. 

I'd like to repeat this isn't a rant and I'm sure they all somehow can be fixed I'm just not eager to keep googlinga around and trying out hit and miss solutions.

I'm sure many of the Unity issues will be fixed by 11.10

---

### Post by r-senior on 2011-04-24
These answers aren't intended to persuade you to use Unity, just to provide information ...

> **t1497f35 said:**
> 1) The launchers and currently running apps are on one pane (left vertical one) so I have to do issue extra brain cycles to sort out which ones are launchers and which ones are running apps,
The running apps have a little arrow to the left. In the settings for the Unity plugin in CCSM, you can also set active applications to have a backlight and not others.

> plus launching a new app is tricky when same instance of app already runs, sometimes it doesn't work
This is true.

> 3) Dropping something on the left vertical panel only works for .desktop files, dropping a location (file/folder) doesn't seem to work, nor an executable file (in win7 and old Gnome it does work though)
This works for a lot of applications for me (e.g. images to Gimp, .doc/.xls to LibreOffice, .txt to Gedit), but maybe not all. Hopefully support will improve. The way it does work is quite nice, highlighting apps that will support that file type.

> 4) Rearranging icons (by mouse drag-n-drop) doesn't work (but, for example, it does work in Win7 and in classic Gnome panels).
This does work but you need to bring the icon out away from the launcher, then back in at the point you want it to appear.

EDIT: Using Unity-2D won't help with these things, by the way. Switching back to Classic may be what you prefer.

---

### Post by t1497f35 on 2011-04-24
> **r-senior said:**
> 
This does work but you need to bring the icon out away from the launcher, then back in at the point you want it to appear.

It's both a weird and funny requirement. Again, pretty sure this will be fixed by 11.10 too. And yes, I'm using classic desktop.

---

### Post by t1497f35 on 2011-04-24
> **r-senior said:**
> 
This works for a lot of applications for me (e.g. images to Gimp, .doc/.xls to LibreOffice, .txt to Gedit), but maybe not all. Hopefully support will improve. The way it does work is quite nice, highlighting apps that will support that file type.
I mean a little different issue - that it should create a new icon/launcher on the left vertical pane when I drop something onto its empty space.
By analogy, when i drop a folder onto the upper Gnome 2.x pane (to an empty place) it creates an icon which if clicked will launch Nautilus showing the contents of that folder (listing its files).
Another example, if I drop onto that pane an executable (to an empty space), Gnome creates an icon for it (also asking me what kind of app that is) and next time I click on that icon it runs that executable. Win7 works this way too. Not sure about XP.

---

### Post by r-senior on 2011-04-24
> **t1497f35 said:**
> It's both a weird and funny requirement. Again, pretty sure this will be fixed by 11.10 too. And yes, I'm using classic desktop.
I understand your point, but remember that the launcher scrolls by dragging up and down, so the way to indicate an icon should move is to drag it out of the launcher and back in somewhere else.

> mean a little different issue - that it should create a new icon/launcher on the left vertical pane when I drop something onto its empty space.
By analogy, when i drop a folder onto the upper Gnome 2.x pane (to an empty place) it creates an icon which if clicked will launch Nautilus showing the contents of that folder (listing its files).
Ah, I see what you mean. I suppose the thinking with the files is that there is already a Files & Folders lens that works with Nautilus bookmarks.

---

### Post by t1497f35 on 2011-04-24
> **r-senior said:**
> I understand your point, but remember that the launcher scrolls by dragging up and down, so the way to indicate an icon should move is to drag it out of the launcher and back in somewhere else.


Ah, I see what you mean. I suppose the thinking with the files is that there is already a Files & Folders lens that works with Nautilus bookmarks.
#1 I'd like moving an icon by just dragging it where I need, like anywhere else in the world, like in win7, Gnome, you name it. When one needs scrolling the pane itself there are lots of other options, like putting an arrow down there, or dragging the borders of the pane, a shortcut key (holding WinKey pressed to "scroll" the pane down) or whatnot. No need to break existing user expectations regarding typical drag-n-drop behavior.

#2 That's an excuse to me rather than a feature. They should just allow for files/folders to be dropped, Ubuntu is about being intuitive and almost all new folks come from windows where that's how it works, and that's how it works in Gnome and other places too. So putting restrictions and requiring users they bookmark their stuff instead - (btw, how do you bookmark an executable?) isn't the smartest idea in the world imho.

---

### Post by cariboo on 2011-04-25
> **t1497f35 said:**
> #1 I'd like moving an icon by just dragging it where I need, like anywhere else in the world, like in win7, Gnome, you name it. When one needs scrolling the pane itself there are lots of other options, like putting an arrow down there, or dragging the borders of the pane, a shortcut key (holding WinKey pressed to "scroll" the pane down) or whatnot. No need to break existing user expectations regarding typical drag-n-drop behavior.

#2 That's an excuse to me rather than a feature. They should just allow for files/folders to be dropped, Ubuntu is about being intuitive and almost all new folks come from windows where that's how it works, and that's how it works in Gnome and other places too. So putting restrictions and requiring users they bookmark their stuff instead - (btw, how do you bookmark an executable?) isn't the smartest idea in the world imho.

If you click and hold on the icon you want to move you don't have to drag it out to the desktop. It takes a bit of time to learn how to use Unity, you may want to have a look at Jorge's [Power User’s Guide to Unity]("http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity").

As to point #2 if you find it's a problem, why not create a bug report.

---

### Post by frank604 on 2011-04-25
> **cariboo907 said:**
> If you click and hold on the icon you want to move you don't have to drag it out to the desktop. It takes a bit of time to learn how to use Unity, you may want to have a look at Jorge's [Power User’s Guide to Unity]("http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity").

As to point #2 if you find it's a problem, why not create a bug report.

Wow, that guide is awesome.  Thanks for the link.  I see a lot of people who have issues about unity can resolve them by reading that guide.

---

### Post by FootySr on 2011-04-25
> **forestpiskie said:**
> Thanks ... ;)
lol... that's funny! :D

We both knew the odds were 50/50 at best but it turned out well. :)

---

### Post by Elfy on 2011-04-25
This time :)

---

