---
title: "KDE killed my DVI?"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by agamonD on 2007-07-08
I hope someone can at least point me in the right direction here, this one has me completely baffled.

I recently wanted to try out KDE, after using Gnome, and Twinview, for months without issue.  At first all was good, but strange things began to happen when I tried logging in my wife at the same time as myself.  For some reason, her desktop would only show up on one monitor, my CRT, while my flat panel hooked up via DVI-I would go black.  I could even switch between our logins, and mine would show up on both, hers still only on one.   In a lazy attempt to fix this, I clicked default settings in the KDE "Monitor and Display" window.   In an even lazier attempt I decided to reboot.  That's when things got really strange.

Upon reboot, my flat panel was completely dead.  Nothing on the screen at all, no memcheck, no grub menu, nothing.  Apparently now my CRT was the only monitor my card (nVidia EVGA GeForce 6200TC) was seeing.  What happen?  How could KDE affect things even before any OS loaded?   Is it possible the video card's BIOS was changed?  Did I inadvertently kill my flat panel?  Any help, even bad  news, would be greatly appreciated.

---

### Post by guitard00d on 2007-07-09
KDE cannot overwrite your BIOS, it's just a window manager. The same would apply to Gnome, Xfce, you name it, they're all just window managers and have no ability to tamper with your BIOS settings. Double check your xorg configuration file, especially the time and date stamp on in. If it shows a time and date that is the same as the time that you installed KDE, then that's definitely your problem. If KDE modified the xorg configuration, it should have created a backup copy of the original configuration file. In which case, try copying your old one over top of xorg.conf and restart xorg with ctrl-alt-backspace, or just reboot the computer.

---

### Post by agamonD on 2007-07-09
Sorry all, I didn't mean to post here.  Can't I delete posts? ...

---

### Post by agamonD on 2007-07-09
Thanks, and that's pretty much what I thought.  The only reason I began to even think such a thing (window managers overwriting hardware BIOS) is, like I said, now my flat panel doesn't work at all, ever.  Even as I boot up (before any OS gets a hold of anything), and even when I boot into Windows (sorry, I didn't mean to bring that trash in here ;) ).   Xorg.conf wouldn't affect my display in these situations, and yet *something* must have changed.  

Nonetheless, I did already try reverting to an old xorg.conf, and even making a new one from dpkg-reconfigure and nvidia-xconfig, but to no avail.  I am at a loss.

---

