---
title: "trouble with gnome-user-share"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by juliank on 2010-10-05
hey guys,

I've some troubles with **gnome-user-share**. It seems to work only partially:

The plan is to share my mp3-files with my netbook.
Therefore I added following line to my /etc/fstab: 
> /media/MUSIK /home/user/Öffentlich/musik	none	bind	0	0
"Öffentlich" means the public folder for gnome-user-share (don't know the precisely term in english).

It works fine so far (I can navigate through all public folders), but it is getting a bit strange now:
[COLOR="Green"]Copying _files_ directly works fine[/COLOR], too. [COLOR="Red"]Copying _folders_ with/without files causes an error:[/COLOR]
"Fehler beim Kopieren von <Folder>." (failed to copy from <folder>) details say: **not found**. I can copy files from this folder, as I mentioned above. Thus the error message is a little bit inconsistent. :(

Any ideas?

Julian

edit:
I forgot to mention: Ubuntu 10.04.1

---

