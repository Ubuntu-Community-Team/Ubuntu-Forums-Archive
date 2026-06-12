---
title: "Notify-send in 11.04"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-04-18
I just read an interesting article in linux format magazine (uk) about how easy it is to have notifications pop up from a simple bash script and couldnt wait to get cracking and make some of my home made scripts a tad more impressive and aesthetically pleasing. The article used the command notify-send but ive just found out the hard way this doesnt work on 11.04, it uses libnotify which i believe has been phased out of the default install, can anyone suggest a command to use that is as simple and beginner friendly that i can still use, i dont want to use additional software as i like my scripts to work from an unmodified install if possible.

Thanks 
Mark

---

### Post by jon4248 on 2011-04-18
Try this in a terminal;
```
 sudo apt-get install libnotify-bin
```and then...

```
notify-send testing,1,2,3
```

worked for me..but don't you just hate where the notify icons go?!? the bottom would be soooooo much better IMHO.

---

### Post by kerry_s on 2011-04-18
Zenity is also a nice app for info & input.

---

### Post by Mr. Picklesworth on 2011-04-19
> **CaptainMark said:**
> The article used the command notify-send but ive just found out the hard way this doesnt work on 11.04, it uses libnotify which i believe has been phased out of the default install, can anyone suggest a command to use that is as simple and beginner friendly that i can still use, i dont want to use additional software as i like my scripts to work from an unmodified install if possible.

Just to clarify, libnotify is about desktop notification bubbles (presented through something like notification-daemon, notify-osd or Gnome Shell's messaging tray). Those aren't going anywhere.

The thing that _is_ being phased out is the system tray, which doesn't really run through a specific library but is a (very simple) protocol implemented through X11. It'll be staying around for a while (Gtk+ still has explicit support for system tray icons), but there just isn't anything that likes to present them in the newer shells.


Oh, by the way, if you type the command in the terminal (assuming you're running Bash) it will tell you what package to install if the command isn't available. You can also use dpkg --search usr/bin/notify-send for the same sort of effect.

---

### Post by Krytarik on 2011-04-19
> **jon4248 said:**
> but don't you just hate where the notify icons go?!? the bottom would be soooooo much better IMHO.
Please see my earlier post about how to modify its position:
[http://ubuntuforums.org/showthread.php?p=10115367#post10115367](http://ubuntuforums.org/showthread.php?p=10115367#post10115367)

It refers to this article: [http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

Greetings.

---

