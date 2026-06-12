---
title: "Samba error: Invalid argument"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by rang501 on 2008-12-11
I have a problem with samba. While copying lots of files, samba gives (only some files are copied) suddenly a error:
**Invalid argument.**

If I try again to copy these files, I got same error again but it will not copy any of files. Using refresh button gives me same error: 
[B]Could not display "smb://192.168.0.1/c"
Error: Invalid argument.
Please select another viewer and try again.[/B]

This problem shows up frequently, usually when trying to copy  one <2GB file and few smaller files.

I tried to search (google, this forum) solutions for this problem but I didn't find any.

Thank you for any help!

Ubuntu 8.10
System is up-to-date. Quite fresh install also (second install).

My english is a bit bad, sorry about that.

---

### Post by albinootje on 2008-12-11
Are you using Nautilus to copy those files ?
I suggest to install konqueror. and test copying with that, to see whether 
Nautilus is the app giving the problems.

In that case you need to copy from one konqueror-window to another konqueror-window (Because konqueror is meant for KDE, not Gnome).

I like konqueror much better for connecting to samba-share,
just try smb://username@file-server/sambe-share/ in the url-field.
Last time i used it, konqueror even showed the possible shares to use (as in name-completion), before i could finish typing.

(Using konqueror for ssh access is also nice, just type :
fish://username@ssh-server/home/username in the url-field)

---

### Post by rang501 on 2008-12-12
Ok, I'll try that.

Thanks!

---

### Post by glockworkorange on 2008-12-14
I am having the same error. Invalid parameters when copying files between a Gutsy laptop and an Intrepid box. It happens in Nautilus as well as Gnome Commander. Seems to effect files between 2 and 3 Megs as all the other files in the dir copied ok. Files in other dirs in that size range did copy ok however.Permissions are Identical on all files and all files are the same type "ogg".

---

