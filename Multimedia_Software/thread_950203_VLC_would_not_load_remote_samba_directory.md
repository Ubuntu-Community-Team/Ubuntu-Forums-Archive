---
title: "VLC would not load remote samba directory"
date: 2008-10-16
forum: Multimedia Software
---

### Post by zaarch on 2008-10-16
So here is the issue, i have a machine running ubuntu server which host all my files via samba share.

now i have installed ubuntu on my laptop, and using ssh via connect to server application, i am able to mount the samba folder onto my laptop

I can read, view and change all files.

If i use totem, i can play files directly of the samba folder...that is fine..

except when i try the same thing in vlc..it does not even register that there is a folder mounted...it just sees the other hard drives..and folders...but not the samba mounted folder...(totem does though)...

any thought, ideas or suggestions ?

thanks,
avaneesh

i really want to use vlc..as it better than totem in almost all respects.

---

### Post by cariboo on 2008-10-16
Just out of curiosity have you navigated to your mounted share and right clicked on the file and chosen open with vlc media player?

Jim

---

### Post by zaarch on 2008-10-17
yep sure..i get this error ..

"Unable to open 'sftp://****@XXX.XXX.XXX.XXX:XXXX/mnt/data/XXXXXXXXX/videos/Tv%20Shows/Planet%20Earth/Episode%201%20-%20From%20Pole%20To%20Pole.mkv'
"

and its not because its an mkv file, its for every file ..no matter what the container.

from what i researched its a nautilus issue and not a VLC one.

however i have three machines running the same ubuntu kernel...into of the machines ..the vlc is able to list the remote directories..

and one cannot and i just cannot figure out why!

so..jim..any ideas mate?

avaneesh

---

### Post by wmatthews on 2009-01-04
It is the way that it is mounted that cause the problem.  the way that you mounted the volume is from going to places and connect to server.  The way that you should mount the share is using the mount command from the command line.  I don't really understand how Ubuntu mounts the shares using the "connect to server way.

---

