---
title: "Need help accessing media from a Network Drive"
date: 2012-04-24
forum: Mythbuntu
---

### Post by zomgqwert on 2012-04-24
Hello fellow members, I am having a slight problem trying to figure out a way to use a network drive to stream the media into the Myth TV Frontend. The setup I am currently working with is two different machines; one is a Windows 7 Ultimate with all the media I need on it, and the other is the Mythbuntu machine, which is a fresh install. Now the thing is, the machine with the media has massive amounts of data on it (almost in the terabytes) and the Mythbuntu, frankly, does not have enough storage space to accommodate this amount. So what I though I would do was to create a network drive with the shared folders for the media file in it, and have that mounted on the Mythbuntu machine. 

So far, I have managed to mount the network drive succesfully onto the mythbuntu machine, and I am able to access the files perfectly using VLC. The problem comes when getting MythTV to read the files in the mounted location. I am not sure if this is the right location where you set this up, but when I put in the location where the network drive is mounted on in the General Settings section under Video Settings, I do not see any signs of media files, folders, or anything. What I am thinking is lack of permission for the location, but I am pretty sure that when installing mythTV it asked about giving it root access.

If it helps, here is the command that was used to mount the drive:
```
mount -t cifs //OMEGA-PC/Shows /mnt/ -o username=WORKGROUP/John,password=**********
```If someone has an idea of what I may be doing wrong, please respond with any advice. 
Thanks a bunch.

---

### Post by zomgqwert on 2012-04-25
Ok, guess I didn't really thoroughly check how Myth TV works. Apparently, all I had to do was scan for changes using the "m" key menu. #-o

---

### Post by itsrabie on 2012-07-30
> **zomgqwert said:**
> Ok, guess I didn't really thoroughly check how Myth TV works. Apparently, all I had to do was scan for changes using the "m" key menu. #-o

What do you do? I want to do the same thing and need some help. 

Thanks!

---

### Post by tgm4883 on 2012-07-30
> **itsrabie said:**
> What do you do? I want to do the same thing and need some help. 

Thanks!

You mount the network drive at a local directory. Then in mythtv-setup you add that directory to the correct storage group (videos for videos, etc). Then you go into the videos in the frontend and you hit m then scan for changes.

---

### Post by itsrabie on 2012-07-30
As I am new to this I understand what you are saying but not how to do it. Could you tell me what to do from top to bottom if i have media I would like to access on another network computer running Windows 7? 

Thanks again.

---

### Post by tgm4883 on 2012-07-30
[http://askubuntu.com/questions/101029/how-do-i-mount-a-cifs-share](http://askubuntu.com/questions/101029/how-do-i-mount-a-cifs-share)

---

