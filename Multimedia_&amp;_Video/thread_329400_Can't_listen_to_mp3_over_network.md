---
title: "Can't listen to mp3 over network"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by bowets on 2007-01-01
I have a problem with my audio players playing mp3's over the network. The problem is that most of my mp3's are on my other computer running winxp which is connected to my laptop running ubuntu through a home network. 
I can see all the files through nautilus, but when I try playing them in totem, vlc, beep or songbird, they won't start. I can only play the files if i copy them onto my machine and play them locally.
What might be the problem?

---

### Post by meng on 2007-01-01
VLC should be network aware. Otherwise try mounting the shares locally, e.g.
sudo mount -t smbfs -o username=[whatever],password=[whatever] //192.168.0.5/files /home/bowets/remote

---

### Post by bowets on 2007-01-01
i'd try the mounting, but how do i find out the ip address of my other computer? it's automatically selected so i don't know what it is exactly.

---

### Post by meng on 2007-01-01
You may be lucky and able to network by hostname rather than IP address. I was too lazy to work out how to enable this, so I just use the IP address as a matter of habit.

---

### Post by bowets on 2007-01-01
it seems that i still don't have the hang of the mounting. i tried what you told me in every way possible and i still can't get it to work. i used the hostname, i even put "smb://" in front of the hostname, and it still won't mount. i created the "remote" dir in /home and nothing... i'll keep trying.... 
i'd appreciate it if there was another (easier) way :)

---

### Post by meng on 2007-01-01
Try this for more details:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
Hope it works out for you. You seem to have the right attitude to solve these problems (i.e., give it a good try and be patient).

---

### Post by bowets on 2007-01-01
thank you for the support!  
it works :D

---

