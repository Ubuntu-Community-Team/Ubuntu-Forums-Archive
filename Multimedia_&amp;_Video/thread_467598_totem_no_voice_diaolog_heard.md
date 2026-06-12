---
title: "totem no voice diaolog heard"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by tribeone on 2007-06-07
OK, installed ubuntu and all dvd/video players work (gxine, kaffine) except totem. Totem plays the dvd and you can here all the music and sound, but you can't hear the voice diaolog. You can her the diaolog in the previews but the main movie you don't hear any voice diaolog at all. Can anyone help.

---

### Post by benanzo on 2007-06-07
That is a new one to me.  Have you tried messing around with the options in the **Sound** menu item?  It probably has to do with the different audio channels in use.

---

### Post by RomeReactor on 2007-06-08
Hi. I had that problem when using totem-gstreamer to watch DVDs; switching to totem-xine solved it (plus with totem-gstreamer the DVD menus didn't work. If you're using it, you could change it and see if that solves it:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by tribeone on 2007-06-09
Benanzo, yes I have tried messing with all the sound controls on totem. Even looked to if there was any differences in setting. Couldn't find any.

Rome, I am using totem xine. This is really bugging me out. I can hear evrything except the voice dialog in the movie. The voice diaolog in the previews commentaries evrything works fine just not in the dang movie. When I put in the command you gave me I get back this:

 [PHP]sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree... Done
totem-xine is already the newest version.
Package libxine1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine-main1
E: Package libxine1 has no installation candidate
faruq@faruq-desktop:~$[/PHP]

---

### Post by tribeone on 2007-06-09
When I use (sudo apt-get install libxine-main1) I get back this:

[PHP]Reading package lists... Done
Building dependency tree... Done
libxine-main1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/PHP]

---

