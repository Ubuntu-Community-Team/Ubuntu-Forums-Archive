---
title: "Connecting To (Windows) Network Drives"
date: 2008-02-24
forum: Mythbuntu
---

### Post by dsbw on 2008-02-24
I have a network that usually consists of 4-5 Windows machines and 3-4 Linux machines. One of the Linux machines is running Mythbuntu.

Without having done anything, the Mythbuntu advertised its music, pictures, recordings and video folders to the network and I can get to those. And read and write to all except recordings, which I can only read from, which makes sense (I think?).

(Though I haven't figured out how to make a video dropped into the video folder viewable through the MythTV front-end.)

Anyway, my question/problem is this: The Mythbuntu machine doesn't see anything on the network. I installed nautilus just to see whether anything would come up under Network and it doesn't. But I'd like to have libraries pointing to other areas of the network (for videos, games, pics and music).

I'm not sure the problem is any different for Linux drives/networks. By a coincidence my other two Linux machines are both down. :(

TiA!

---

### Post by Tr1p on 2008-02-24
//192.168.21.10/films /home/user/server/films smbfs uid=1000,password=passw,username=user 0 0
//192.168.21.10/muziek /home/user/server/muziek smbfs uid=1000,password=passw,username=user0 0
//192.168.21.10/fotos /home/user/server/fotos smbfs uid=1000,password=passw,username=user 0 0

@ fstab
u can change smbfs in to cifs
Then it mounts automatic when your mythbuntu boots
so u dont have to drop files anymore in your myth-folder

just set the mythmovie path @ /home/user/server/films 

etc etc

greets i hope it works , it works perfectly by me

---

### Post by dsbw on 2008-02-24
Thanks, I'll give it a try.

---

