---
title: "How do I prevent MusicPlayer from opening automatically when I insert a CD?"
date: 2008-04-23
forum: Multimedia Software
---

### Post by tubegeek on 2008-04-23
I usually insert CDs to rip them to my hard drive and I use Rubyripper to do this. How do I turn off the default behavior of opening MusicPlayer whenever an audio CD is inserted?

I'm on 8.04 LTS, all updates as of this AM are installed.

Thanks!

---

### Post by gg234 on 2008-04-23
try this [http://www.ubuntugeek.com/howto-turn-off-auto-play-of-cdsdvds-and-ipods-in-ubuntu.html](http://www.ubuntugeek.com/howto-turn-off-auto-play-of-cdsdvds-and-ipods-in-ubuntu.html)

---

### Post by tubegeek on 2008-04-23
I wish!

The new control panel in 8.04 has ONLY these tabs: Cameras, PDAs, Printers & Scanners, Input devices. There is no tab (or entry on one of those tabs) for CDs!

Thanks for trying, though!

---

### Post by angol on 2008-04-23
I second that question - I would really love to know how to have gtkpod open automatically instead of rhythm box but now I have upgraded to hardy (perhaps too soon?) - no multimedia tab in 'removable devices' ...if anyone knows how please put us out of our misery! :-)

---

### Post by tubegeek on 2008-04-25
Found it!

From the Places menu item, select any choice. This will open a Nautilus file browser. Next select Edit>Preferences. A popup window titled File Management Preferences will open. Click the Media tab. For CD Audio you will have a drop-down box with some choices of behaviors. Select the one you want. (Mine was "Do nothing."

Done!

Maybe you will have to configure your media player as a Preferred Application from that other tool, (System>Preferences>Preferred Applications, select Multimedia tab, set Multimedia Player to Custom and add the terminal command for gtkpod) before it will become one of the drop-down choices, I dunno. I didn't bother, I just made a desktop launcher for Rubyripper.

---

