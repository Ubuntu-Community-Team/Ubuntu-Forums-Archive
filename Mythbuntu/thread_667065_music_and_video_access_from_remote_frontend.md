---
title: "music and video access from remote frontend"
date: 2008-01-14
forum: Mythbuntu
---

### Post by dragoster on 2008-01-14
I have a 100% healthy running Mythbuntu backend/frontend and a newer frontend only machine. 

As far as I can the remote frontend connect correctly to the mysql database. On the remote frontend I can watch live TV, watch TV recordings, and see the list of videos (can't see the video covers). The problem is that on the remote frontend I can't play the videos, and can't see the music. 

I have NFS and Samba enabled on the backend. I was reading that Mythbuntu should automatically be set up to do the necessary mounting so the remote frontend can access the shared backend. 

Is there indeed an automatic way to have Mythbuntu do this?

If not, can somebody spare 5c to help me mount the NFS shares on the frontend. My exports file on the backend reads something like:

/var/lib/mythtv/recordings    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/music    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/pictures    *(ro,async,no_root_squash,no_subtree_check)

I tried to do a simple mount on the frontend but it didn't work:

sudo mount backend_IP:/var/lib/mythtv/videos /mnt/videos

where /mnt/videos is an empty folder. 

Thanks,
-D

---

### Post by n00b@linux on 2008-01-14
[Section 23.10 of the MythTV documentation]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.10") might help.  Note the parameters passed in the example /etc/fstab line.

---

### Post by dragoster on 2008-01-15
What is the difference between Recordings and Videos / Music? Do I really have to setup the remote frontend to connect via NFS or Samba? Why do the recordings work, but not the music and videos?

Thanks,
-D

---

### Post by Weidbrewer on 2008-03-03
The problem I'm having on my front end is that, when I go to the media library, the only option that is listed there is "Watch Recordings."   There is no option for videos, pictures, music, etc.   It's all there on the back end, however.  Any suggestions?

---

### Post by Weidbrewer on 2008-03-03
I'm realizing that I might be an idiot.   I had assumed that the plugins I needed where installed by default on the front end...they might not have been.  D'oh.


When all else fails, read the instructions...if that doesn't work, *follow* them.

---

### Post by volkswagner on 2008-03-03
> **dragoster said:**
> What is the difference between Recordings and Videos / Music? Do I really have to setup the remote frontend to connect via NFS or Samba? Why do the recordings work, but not the music and videos?

Thanks,
-D

I was told this is the default setup.  I guess some people would prefer to have music and video local to each frontend.

---

### Post by newlinux on 2008-03-03
The recordings are streamed via Myth's own streaming protocol, whereas Videos/Music are not. My guess is because mythvideo allows you to use an external program for playing videos, but I don't know.

---

### Post by Weidbrewer on 2008-03-03
> **newlinux said:**
> The recordings are streamed via Myth's own streaming protocol, whereas Videos/Music are not. My guess is because mythvideo allows you to use an external program for playing videos, but I don't know.

Is there any way around this?  I've got the plugins installed for video, images and music, but I can't access them, as covered above.   Video and images just show blank files.   Music show up as being there, but I get the error message, "FlacDecoder: Failed to open input" when I try to play any of the files.

I would very much like to work this out as part of the reason that I built the myth box was to have a central location to store all of these files and access remotely.

---

### Post by newlinux on 2008-03-03
You can do a central location, you just have to mount that location to each frontend. The mounts can happen automatically at boot. That's how I have mine setup. I have all my music and mythvideo media stored on my fileserver and mounted on each frontend. If you have them mounted then their may be some other problem. You'll want to make sure you've entered the proper directories for myth to scan.

---

### Post by Weidbrewer on 2008-03-03
The big question is "how"?  Like I said, the music files are showing up on the list, but I can't play them.   (see above error.)

The other files, I can see when I look the storage computer up on the network.  How do I mount them?   How to I fix the other error.

(Please assume n00b, and in this area, I certainly seem to be.)

---

### Post by Weidbrewer on 2008-03-05
Okay, I had some time to play with it last night, and didn't quite get it to work...but here's what I did, and hopefully someone can tell me where I went wrong:

On the Frontend, I went to network, found the Video, Music and Picture Folders on the back end, and connected to them.   (Right-click, connect to, sent to my desktop)

I found the path for the picture folder and copied it  (It was something along the lines of smb://backend/pictures.)   From the myth media set up, I replaced the link (default was something like /var/lib/mythtv/pictures) with the networked one.   It reject the link as not being workable.


Any ideas/solutions/other?

---

### Post by newlinux on 2008-03-05
I understood your error and read it.

Where you went wrong is that doing what you did  doesn't actually mount the shares. Unfortunately myth won't understand the smb protocol. There was a link already in this thread with information about mounting. Have you looked through any documentation on mounting?

Are you multimedia files stored on a windows machine or a linux machine?

There are plenty of threads and how-tos on mounting. 
I'm guessing from what you wrote your multimedia is on Windows -  then you will probably want to use SAMBA/CIFS
[http://ubuntuforums.org/showthread.php?t=667580](http://ubuntuforums.org/showthread.php?t=667580)
[https://help.ubuntu.com/community/SettingUpSamba#head-d0cf07ad854d6a463aa1ba9345600732832d47ef](https://help.ubuntu.com/community/SettingUpSamba#head-d0cf07ad854d6a463aa1ba9345600732832d47ef)


If you are mounting linux to linux, you probably want to use NFS mounting:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server)
or
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by Weidbrewer on 2008-03-05
I guess where my confusion came in is that those files on the desktop now have the option to *unmount* them....leading me to believe that they were mounted.


Both machines involved are Ubuntu, though there are also two windows machines on the network, which is why I've been using Samba.

---

### Post by newlinux on 2008-03-05
Yeah, that way of "mounting" only works with some applications. The ways in the links I showed you work with all applications. I wish they wouldn't call that mounting unless it is going to work with all applications...

---

### Post by Weidbrewer on 2008-03-05
Yeah, that would be nice.


I looked through the NFS stuff, and it looked very doable.  Probably won't get time tonight, but I should this weekend.   Question:   Can I make use of both Samba and NFS so that some of the folders can still be used on my windows machine?

---

### Post by newlinux on 2008-03-05
Yes you can. I actually just use CIFS (SAMBA) for everything so that windows computers on my network can see everything. I actually don't use NFS. I use SAMBA to share everything.

---

### Post by Weidbrewer on 2008-05-12
**newlinux**:  I just wanted to come in here and post an update.  Your guides you linked for NFS shares has been invaluable.  I have it bookmarked on every machine at home for quick reference.  Thanks for the suggestion.

---

### Post by oobe-feisty on 2009-03-01
> **Weidbrewer said:**
> The big question is "how"?  Like I said, the music files are showing up on the list, but I can't play them.   (see above error.)

The other files, I can see when I look the storage computer up on the network.  How do I mount them?   How to I fix the other error.

(Please assume n00b, and in this area, I certainly seem to be.)



ok the reason why the music files show up is cause they exist in the remote backends database you need to mount the nfs share to a folder structure identical to the remote backend i.e 

if you have all you mp3's in a folder called /data/media/mp3z on your remote backend 

and you share it via NFS but you mount that share as /mnt/mp3s 

it will not work you need to recreate the same folder structure 

mkdir /data/
mkdir /data/media/
mkdir /data/media/mp3z 

then mount 192.168.0.12:/data/media/mp3z


here is an example of my remote frontends mounts


mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
box:/data/Documents/media/vids on /data/Documents/media/vids type nfs (rw,rsize=8192,wsize=8192,intr,tcp,addr=192.168.1.10)
box:/data/Documents/media/mp3z on /data/Documents/media/mp3z type nfs (rw,rsize=8192,wsize=8192,timeo=14,intr,nfsvers=3,bg,actimeo=0,tcp,addr=192.168.1.10)
box:/home/oobe/.shepherd/icons on /home/oobe/.shepherd/icons type nfs (rw,rsize=8192,wsize=8192,timeo=14,intr,nfsvers=3,bg,actimeo=0,tcp,addr=192.168.1.10)
box:/home/oobe/.mythtv/MythVideo on /home/oobe/.mythtv/Videoremote type nfs (rw,rsize=8192,wsize=8192,timeo=14,intr,nfsvers=3,bg,actimeo=0,tcp,addr=192.168.1.10)
oobe@frontend:~$ exit

---

