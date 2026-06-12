---
title: "eee 8.10 vlc and more video tearing!!!"
date: 2008-12-29
forum: Multimedia Software
---

### Post by mishkin on 2008-12-29
I'm running the unr eee 8.10 version of ubuntu and I'm using vlc (although the pre installed video player does the same) and I'm getting a lot of video tearing while watching standard def scene releases (movies and tv)

Someone at eee forums said to turn deinterlacing on but after reading what that does seems a silly suggestion...

anyone know how I might turn vertical sync on???

my laptop is a asus 1000H eee, is 1.6ghz atom proc, not sure if any video card or whatnot

any help appricated (as I was planning to watch a fair amount of tv on this laptop)

---

### Post by mishkin on 2008-12-29
I tried gstreamer-properties and tried X11/Xshim/xv AND no xv Seperatly and that had no effect on the tearing

Then I did sudo apt-get install driconf  And set it to always use vertical sync and this also had no effect (I read about this in a slideshow of all places)

anyone know another way of turning vsync on or getting rid of the tearing/??

linux isn't much use if it can't play a low def video :P

---

### Post by mishkin on 2009-01-01
i did gstreamer with this time x11/xv but I set device under it as intel video overal (sometimes this seccond box is ghosted)

this seems to clear up the tearing in totem, no idea how to clear it up in vlc which is my prefered client due to the easy 1 button changing of audio sync (helps when stuff is nuked for sync don't need to redownload)

---

