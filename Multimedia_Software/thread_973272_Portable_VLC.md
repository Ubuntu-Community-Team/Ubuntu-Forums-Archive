---
title: "Portable VLC ?"
date: 2008-11-06
forum: Multimedia Software
---

### Post by dementic on 2008-11-06
Hello!

I use VLC 0.86 on ubuntu 8.10 because I need it to read some streams that don't work with 0.94. So I want to use 0.94 with the 0.86 installed. As I can't install both I want to use a "portable" version of VLC 0.94 (because it has a video sharpening option) without installing it.

I don't want to compile the whole thing because it's really complicated, you need a lot of heavy dependancies like wxwidgets, and so on.

So if someone knows how to do it? 

Thank you

---

### Post by lovinglinux on 2008-11-06
You could use the Windows version of the newest release with Wine. I don't know if VLC works with Wine, but this would be a way of running two different versions of the same application without messing your Ubuntu installation.

---

### Post by dementic on 2008-11-07
Hello! 

Thank you for your answer but neither 0.86 or 0.94 works correctly on wine, video is very laggy and sound too.

---

### Post by stinger30au on 2008-11-07
why not run xp inside virtual box and run portable vlc inside xp

then add the guest additions and share some directorys between ubuntu and xp and view your data like this


works for me and has done for some time

---

### Post by dementic on 2008-11-08
I already have vista on dual boot. My goal is to be almost independant from windows. But I know that VLC can be run as portable (you just do "./configure" then "make" and not "make install") then you can use VLC from the directory where it has been compiled. The problem is that to compile it you need to install a lots of thing which I will never use after that (I try to keep my system as light as possible). So if someone has a compiled version not in deb package I would be happy to get it :)

---

