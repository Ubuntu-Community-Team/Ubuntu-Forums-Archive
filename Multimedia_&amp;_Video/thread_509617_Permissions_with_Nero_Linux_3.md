---
title: "Permissions with Nero Linux 3"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by Steven Weidman on 2007-07-25
I have downloaded Nero Linux 3.  When I start the program I get the following message:
One of your devices is not accessible.
Please, check that you have the correct permissions on the correspoding device file.  Nero Linux cannot get access to the following device:  /dev/sg0 (SCSI Generic Device)

I have two CD drives:
TOSHIBA DVD-ROM SD-M1612 (ID:0 - HA:0) - read only
QPS CRD-BP1500P (ID:1 - HA:0) - read/write

It would appear that the device that needs the permissions would be the QPS.

What do I do to fix this problem?

---

### Post by Steven Weidman on 2007-08-06
Anybody?

---

### Post by DeusEx on 2007-08-06
what are the mounting permissions in your /etc/fstab file? I'd guess the user running Nero Linux isn't allowed to access the drive

---

### Post by stinger30au on 2007-08-06
from terminal type in 
sudo nero

see how you fare

---

### Post by Tiggzz on 2007-08-09
I to have this issue. I am VERY noob, andhaveing a few headaches to start!!!

I have tried with sudo nero, and it starts it ok, but when I go back to the launcher on the applications / sound & video menu, it still comes up with the error.  Can I edit the launcher to start with the sudo command ( what ever this is!!!

I appreciate that I might be trying to run before I can walk, but this is my first time with any linux. I just need to be able to complete the essentials that the PC doen before I installed ubuntu on it, then I can learn about it whilst maintaining its functionality.

Thanks

Tiggzz :)

---

### Post by DeusEx on 2007-08-12
try:

system - preferences - main menu  (in GNOME)

rightclick - properties of nero, and type
```

gksu

```
in front of the command (with a space seperating gksu and the command)

gksu will launch a program in SuperUser mode.

---

### Post by kelvin spratt on 2007-08-12
This seems very strange as I use Nero3  and it has never asked for permissions on any of the distros i have used.

---

### Post by bricksen on 2007-08-12
Nero Linux 3 .... GPL? :)

---

