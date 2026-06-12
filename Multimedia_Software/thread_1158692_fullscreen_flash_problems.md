---
title: "fullscreen flash problems"
date: 2009-05-13
forum: Multimedia Software
---

### Post by rock4christ on 2009-05-13
whenever I try to make hulu go full screen, firefox(3.5b4) crashes. also, flash is a little choppy(not awful, but not up to the smoothness on windows, or even the performance I got from a dell inspiron 5100 running 8.04 a while back)

---

### Post by sirgimp on 2009-05-13
I have not been able to view any fullscreen flash since upgrading to Jaunty. The fullscreen video is very choppy and out of sync, way behind the audio.

This is with Flash player 10.

---

### Post by rock4christ on 2009-05-13
the choppiness I was refering to was just a regular vid playing nonfullscreen.

---

### Post by psyke83 on 2009-05-13
Using Jaunty? Got Intel integrated graphics? There are some problems that can reduce performance, especially with video playback. See my sticky guide from this forum (the Safe configuration).

---

### Post by rock4christ on 2009-05-13
on jaunty. not intel. Nvidia Geforce 8400M, amd turion x2 processor

---

### Post by rock4christ on 2009-05-14
I read something about it being a nvidia problem with libGL not loading. it suggested  LD_PRELOAD=/usr/lib/libGL.so firefox-3.5 as a solution, but that command gives an error

---

### Post by rock4christ on 2009-05-14
it seems to work if i put sudo in front of the command.(will this give firefox sudo privilages?)

when I start i get a error loading some config files thing with the following under details.

> Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: EOF in dbus-launch reading address from bus daemon
)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: EOF in dbus-launch reading address from bus daemon
)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: EOF in dbus-launch reading address from bus daemon
)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: EOF in dbus-launch reading address from bus daemon
)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: EOF in dbus-launch reading address from bus daemon
)


---

### Post by sirgimp on 2009-05-14
This works on my system (Dell 530s desktop with Flash 10).

In CompizConfig Settings Manager, under General section, double-click the General Options icon. In the General tab, uncheck the option *Unredirect Fullscreen Windows*. Now click the Back arrow in the bottom left. At the main sceen of the dialog click the Close button. Flash fullsceen should work now.

---

### Post by VCoolio on 2009-06-19
Read the solution I found for my flash fullscreen problem with NVidia card [here]("http://ubuntuforums.org/showpost.php?p=7487421&postcount=14"). Works at least for firefox 3.6 (Minefield) and swiftfox 3.5b99.

---

### Post by Rizlaw on 2009-07-12
> **sirgimp said:**
> This works on my system (Dell 530s desktop with Flash 10).

In CompizConfig Settings Manager, under General section, double-click the General Options icon. In the General tab, uncheck the option *Unredirect Fullscreen Windows*. Now click the Back arrow in the bottom left. At the main sceen of the dialog click the Close button. Flash fullsceen should work now.

I can confirm this works for Ubuntu 9.04 64bit. Pretty good HD playback.

---

