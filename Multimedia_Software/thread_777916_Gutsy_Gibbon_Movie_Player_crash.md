---
title: "Gutsy Gibbon Movie Player crash"
date: 2008-05-01
forum: Multimedia Software
---

### Post by SubstanceDx99 on 2008-05-01
Hello there,

I just installed 7.10 Gutsy Gibbon about a week ago.

On my external hard drive, I have AVIs of several movies, which I have downloaded the Linux codecs for (DivX, etc.). When I open some of these files in Ubuntu Media Player, the player crashes after loading and resizing the window.

This only occurs with certain videos, and it does not matter if I open Movie Player first, or if I open the file itself.

I have also attempted to watch  these videos with VLC, and the same thing happens.

Please help, thank you so much!

---

### Post by pedja_portugalac on 2008-05-15
Same happened to me and I am writing this message from the live CD. I already have hardy heron installed. When I watch some movies, doesn't mater if it is with Totem or VLC, sometimes it freeze my desktop. I can't turn off player or doing anything then. The only way I know is to push the button to completely turn off computer. It happened few times to me and I was thinking that may-be my laptop ventilator is dirty warming processor or something. Every time I restart computer "hard way" I was able to continue using it normally till I watch next movie. This time, it happened to me again and I've turned it off "hard way" like before, but after rebooting the only thing I can see, after logging in was my wallpaper. No applications tray and no way to start anything. I had some things I needed to save and it's already done using live CD. I could reformat hdd again and again, every time I watch fk***** movie but it's not the way life should going. I presume the problem is with GNOME manager and I don't know if one can recover GNOME and how. I would be glad to hear you guys if somebody have solution to this problem, anything but stopping watching movies is welcome. :lol:

---

### Post by pedja_portugalac on 2008-05-15
OK. I was playing with booting kernel in recovery mode an I have tried all the options without success. I wasn't able to connect with ubuntu server witch recover broken packages. I've tried again to log on normally and it appears some folders on my desktop, wallpaper still in the background, but no applications tray and I wasn't able to do anything but moving around pointer. So I start to play with shortcuts, I remember ones I've learned to restart X in this way. :lol: When I used combination of Fn+F6 the desktop turns black and then same like before. I use that combination one more time but this time it turns black for a while, could be 20 secondes and my normal Desktop configuration have returned showing this two errors.

[img]http://img101.imageshack.us/img101/2686/ubuntucrashje7.jpg[/img]

Now I will investigate about this two errors and restart to see if it still comes back or it will fix on boot.

---

### Post by pedja_portugalac on 2008-05-15
Some people from the debian community on the internet says that can be provoked by gstreamer and propose to downgrade gstreamer to previous version, they say that solve the problem. If this problem comes back ones again I'll try to downgrade gstreamer till they make patch for that.
PS. I remember, one of the first updates on fresh hardy had something to do with gstreamer. So I presume they know about this problem.

---

