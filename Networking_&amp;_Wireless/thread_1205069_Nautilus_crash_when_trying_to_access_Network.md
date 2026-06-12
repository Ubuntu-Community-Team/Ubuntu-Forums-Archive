---
title: "Nautilus crash when trying to access Network"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Tictoon on 2009-07-05
Today, my Ubuntu machine is really pissing me off. First the desktop affects in my sister's account aren't working, and now when I try to access a smb share, Nautilus crashes when I try to click on "Network". 

Terminal output:
```
gagan@gagan-desktop:~$ nautilus

(nautilus:5833): UbuntuOne-Nautilus-WARNING **: ERROR: The name com.ubuntuone.SyncDaemon was not provided by any .service files

(nautilus:5833): UbuntuOne-Nautilus-WARNING **: ERROR: The name com.ubuntuone.SyncDaemon was not provided by any .service files

** (nautilus:5833): WARNING **: Unable to add monitor: Not supported

** (nautilus:5833): WARNING **: Cannot extract frame (0, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (36, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (72, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (108, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (144, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (180, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (216, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (252, 0) from the grid

Segmentation fault

```

What do you guys make of it?

---

### Post by exutable on 2009-07-06
I wish I could help but all I can say is that i have the exact same problem.

I get:


** (nautilus:4151): WARNING **: Unable to add monitor: Not supported
Segmentation fault


Fully updated Ubuntu Jaunty, fresh install on an HP HDX16 1370US

---

### Post by superprash2003 on 2009-07-07
nautilus has those issues , i access my shared folders this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by jimmah6786 on 2009-07-07
> **Tictoon said:**
> Today, my Ubuntu machine is really pissing me off. First the desktop affects in my sister's account aren't working, and now when I try to access a smb share, Nautilus crashes when I try to click on "Network". 

Terminal output:
```
gagan@gagan-desktop:~$ nautilus

(nautilus:5833): UbuntuOne-Nautilus-WARNING **: ERROR: The name com.ubuntuone.SyncDaemon was not provided by any .service files

(nautilus:5833): UbuntuOne-Nautilus-WARNING **: ERROR: The name com.ubuntuone.SyncDaemon was not provided by any .service files

** (nautilus:5833): WARNING **: Unable to add monitor: Not supported

** (nautilus:5833): WARNING **: Cannot extract frame (0, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (36, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (72, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (108, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (144, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (180, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (216, 0) from the grid


** (nautilus:5833): WARNING **: Cannot extract frame (252, 0) from the grid

Segmentation fault

```

What do you guys make of it?

Same thing here gagan, this is only recently. I have been able to use the network short-cut or manually type in a network address resource with no problems. It is recently that it is now causing Nautilus to crash..I wonder if it is an update that went out this week?

Please help Ubuntu team!!

Nautilus version 2.26.2

-Jim

---

### Post by solitaire on 2009-07-07
I was getting the same error.

Looks like it's a fault with Ubuntuone software!!

Once I did a complete removal of all the Ubuntuone files the error was gone..

Try removing Ubuntuone and see if the error happens.

Someone might need to file a Bug report for Ubuntuone and nautilus integration problems..

---

### Post by pyjamashark on 2009-07-08
Solitaire, you rock....had the same issue and ubuntuone was the culprit. Removed all related packages completely, restarted and was back to normal.
Will be using Dropbox for now.

---

