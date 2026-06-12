---
title: "Both Fre:ac and soundKonverter Don't Open The CD"
date: 2020-03-23
forum: Multimedia Software
---

### Post by ron-kellis on 2020-03-23
Tried every search option I could think of, sorry if I've missed an obvious answer. VLC will play a CD, but when trying to add files in either fre:ac or soundKonverter neither will list the media and if I try to access the media through the file manager I'm told I, the owner, don't have permission to access. Both apps have the option to pick the location to save to, how can I select the "from" location?

Thanks

Ron

---

### Post by Holger_Gehrke on 2020-03-24
The device file for the cd-drive (usually /dev/sr0, check the symbolic links /dev/cdrom or /dev/cdrw) should be owned by root and the group 'cdrom'. If you're a member of the 'cdrom'-group things should just work. In freac there's a menu-item 'Options'->'active CD-Drive' that should allow you to select a drive if you have more than one (or have something like CDEmu running).

Holger

---

### Post by ron-kellis on 2020-03-24
Thanks for the help, it's appreciated. I saw some other references to the name of the media, but I can't change it.  The active drive is shown as: HL-DT-ST DVDRAM GUALON LZ20 and I'm not able to change that. even by trying to create a new configuration.

Any idea how it's supposed to be edited?

Again, 

Thanks!

Ron

---

### Post by Holger_Gehrke on 2020-03-24
> **ron-kellis said:**
> The active drive is shown as: HL-DT-ST DVDRAM GUALON LZ20 and I'm not able to change that. even by trying to create a new configuration.

Any idea how it's supposed to be edited?


It's not supposed to be edited. That's (part of) the name of the drive as shown in /dev/disk/by-id/ and these names are provided by the devices themselves. If you open a terminal and enter 'ls -l /dev/disk/by-id/'  you'll get a listing of the disk-drive-like devices in your system and one of them will be named like that (well, there will be something in front of that name to show the way it's connected and all the spaces will be substituted with '_'). At the end of the line there will be a '->' followed by '../../' and the name of the device-file for the drive.

Check whether you are a member of the 'cdrom' group using the command 'groups' in a terminal. It will give you a list of all the groups you are a member of. If 'cdrom' is in the list, then I don't know how to help. If you're not a member of the group 'cdrom' then you need to change that. 

There probably is a graphical way to do this, but unless you're using XUbuntu or Ubuntu Studio (which both use XFCE) I can't talk you through how to do it that way because I haven't used another desktop than XFCE in years.  The command to add you to the group in the terminal is 'sudo usermod --append --groups cdrom $USER'. The sudo at the beginning of that command temporarily gives you administrative privileges, the rest of the command appends 'cdrom' to the list of groups that you're a member of ($USER at the end of that command is a shell variable that contains the name of the current user; the shell substitutes that automatically before executing the command; you could save it the trouble by putting your user name there, but why bother ...). After entering that command you will be asked for your password. Enter it and don't be surprised if nothing gets shown while you type. It's a security measure to stop 'shoulder-surfers' from finding out the length of your password. As is typical of the command line you'll get no feedback if the command succeeded ('no news is good news'). After logging out and back in, 'groups' in a terminal should show you as a member of the 'cdrom' group and reading audio from a CD should work .

Holger

---

### Post by ron-kellis on 2020-03-24
Thanks for offering what you could.
ron adm cdrom sudo dip plugdev lpadmin sambashare

So I'm an admin, but still can't pull anything off the cdrom . . . If I go through files, I can access everything on the CD. But if I try to go there through Fre:ac, |File | Add| Audio Files |  then the cd player isn't shown and anything I try to access in "Computer" renders "Permission Denied" 

Go figure. Vanilla Ubuntu load, I have to follow the directions for anything complicated LOL, can't keep this stuff memorized. Nothing out of the ordinary.

Ron

---

