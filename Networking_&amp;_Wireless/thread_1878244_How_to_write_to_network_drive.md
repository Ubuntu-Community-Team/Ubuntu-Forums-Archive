---
title: "How to write to network drive"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by Snerler on 2011-11-09
I have a western digital live hub which has a shared network drive. I am trying to get ubuntu to mount this drive. 

I added the following to FSTAB:

//192.168.1.9/WDTVLiveHub  /home/server/Desktop/Live_Hub  cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Now I am able to see the contents of the drive but I cant write to it. When I right-click on the folder and go to Permissions it says that I am not the owner. What can I do to make the share writable?

---

### Post by josephmills on 2011-11-09
Hi there there is a handy command called chmod witch changes permissions you can read more about it here [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
hope this helps !

---

### Post by Morbius1 on 2011-11-09
Without knowing what a WDTV is or how it's configured my first question is does it allow a guest to write to it's share?

If it's acting like a samba server on top of a linux os you might want to add another option to you fstab entry:

//192.168.1.9/WDTVLiveHub  /home/server/Desktop/Live_Hub  cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,[COLOR=Blue]**nounix**[/COLOR] 0 0

You might also want to try to mount it the gvfs way through nautilus. In a Terminal:
```
nautilus smb://192.168.1.9/WDTVLiveHub
```

---

### Post by Snerler on 2011-11-09
What I ended up doing was this:


server@Home-Server:~$ sudo chown -hR server /home/server/Desktop/Hub

This gave me the ability to write to the folder and make new folders there. Now whenever I save a file in that network drive it becomes read only and I can't edit it again without using that same command again. Is this because I used chown instead of chmod?

---

