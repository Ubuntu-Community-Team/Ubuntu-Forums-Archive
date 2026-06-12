---
title: "iTunes style SMB media player"
date: 2010-04-07
forum: Multimedia Software
---

### Post by Alan James on 2010-04-07
I have an SMB service in my apartment that has all of my media files on it. When I am on Windows and OS X I use iTunes to play my music straight off of my server, no need to copy files over to a local directory. But I have been unable to do this on Kubuntu. Every media player I have used will not add the songs from the server.
 

 What iTunes style media player will play songs via an SMB server? Rythmbox, Banshee, Amarok, Juk?

---

### Post by Alan James on 2010-04-08
Does anyone know how I can start looking for this?

---

### Post by Garthhh on 2010-04-08
> **Alan James said:**
> Does anyone know how I can start looking for this?

Hi Alan,
could you please expand on the technical details of the smb system you are accessing?
you might have a look in the servers or networking sections.
or [https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)
or [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Alan James on 2010-04-08
I have a [D-Link DNS-321]("http://www.dlink.com/products/?pid=666") elsewhere in my apartment that I store all of my files on. I am able to access all the files with no problem through Dolphin, however when I try to drag and drop those files into Rythmbox, Banshee, Amarok, Juk they will not add to the library.  
 

 On Windows and OS X I can drag and drop files into iTunes to add them to its library and play them without the need to copy them to a local directory, but on Linux there is no iTunes and the other players don't SEEM to support this feature.
 

 How can I store files in my SMB server but still play them through one of the media players like  Rythmbox, Banshee, Amarok or Juk?

---

### Post by Alan James on 2010-04-08
Does anyone know of a player that will stream files via a DNS-321?

---

### Post by Alan James on 2010-04-09
This will be my last bump for this thread because I assume either no one understands what I am asking or there is no solution.

---

### Post by happymellon on 2010-04-09
> **Alan James said:**
> This will be my last bump for this thread because I assume either no one understands what I am asking or there is no solution.

Don't be quite so hasty, not everyone checks out the forums every day :)

Do you have local music and videos? This will assume that you don't, hence why you are attempting to get it to work over the network.

A quick way would be just to mount your network media folders over the top of you local media folders.

For example if your DNS-321 is at 192.168.0.1 and you have your music under \media\music

then Alt-F2 and run:

gksudo mount -t smbfs //192.168.0.1/media/music/
  ~/Music -o username=Guest,password=

You have not deleted any music that was already in music, it is just now hidden, but the media players should point to those locations and pick it up automatically.

running `gksudo umount ~/Music` should restore you back if you don't want it.

To make it happen automatically add it to your fstab (file system table), Alt-F2 again and run:

gksudo gedit /etc/fstab

and add at the bottom

//192.168.0.1/media/music /home/Alan/Music smbfs rw,_netdev,user=,password=,uid=1000,gid=100 0 0

then try `mount -a`

one last thing, if this is all too complicated, have a look at one of the applications in the Ubuntu Software Center such as "MountManager", I haven't tried it yet, but in the tool bar there is a plug in to manage Samba shares and it seems pretty straight forward.

Let us know if it answers your question.

---

### Post by Alan James on 2010-04-09
Thank you for your reply. I just tried MountManager and it doesn't seem to work (most likely due to user error). I will keep playing with it though.
 

 I think I understand that the basic idea is that I will have to mount the server to a local directory so that I can navigate to it and so that my whichever media play I use will be tricked into thinking that the files are saved locally when they are actually saved on the server. Am I correct?

---

### Post by happymellon on 2010-04-09
> **Alan James said:**
> Thank you for your reply. I just tried MountManager and it doesn't seem to work (most likely due to user error). I will keep playing with it though.
 

 I think I understand that the basic idea is that I will have to mount the server to a local directory so that I can navigate to it and so that my whichever media play I use will be tricked into thinking that the files are saved locally when they are actually saved on the server. Am I correct?

Pretty much. Although I noticed that there is a bug filed on this with a lot of debate around it:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/273294](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/273294)

I personally have had issues with media players and SMB shares on Ubuntu, although it does sound like not everyone has.

---

### Post by virtue-all on 2010-07-09
I do this every day, so it is certainly possible.  I have not found a media player yet that does not work.  I have used Amarok, Totem, Rhythmbox, Banshee, VLC.  One of the previous posters was correct, mount the SMB share using a credentials file.  However, I had a lot of trouble with the smbfs filesystem type.  I recommend you use cifs instead.  For example:

//spaceball1/Video /media/video cifs credentials=/etc/cred.rw,gid=users,uid=ferreter

---

