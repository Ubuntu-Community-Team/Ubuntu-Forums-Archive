---
title: "Survey about your music - where do you keep it?"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by PCFascist on 2007-06-27
I have a large number of live recordings I've made myself. I used to in windows keep it under another drive such as D:
That worked well for me and it felt logical. In linux however, I am worried about placing them all under the root in something like /music
At the same time I am worried about keeping them under /home/musicuser/  because then most users on my network wouldn't be able to listen to my files if they wanted.

Well, that explains my ideas... please let me know what you do with your own.

---

### Post by Jose Catre-Vandis on 2007-06-27
Create a separate partition on your drive - call it music

create mount points to it from your OS

pop the required line in fstab so it comes up on boot

Sharing the music:
Web interface? - GNUMP3D
Install nfs server on the PC where your music is, and get all users to install the client
Samba (if you must)

---

### Post by PCFascist on 2007-06-27
> **Jose Catre-Vandis said:**
> Create a separate partition on your drive - call it music

create mount points to it from your OS

pop the required line in fstab so it comes up on boot

Sharing the music:
Web interface? - GNUMP3D
Install nfs server on the PC where your music is, and get all users to install the client
Samba (if you must)

Yeah, I have no choice but to make another drive hold the music. I wasn't really worried about how to share the music. More interested in what mount point to use, because of permissions issues. I understand I could change those, but something bothers me about having it listed off the root none the less.

---

### Post by elcasey on 2007-06-27
I use an external HDD for all my music, but it really is just a matter of creating a new partition and mounting it. Permissions won't be a huge issue if you take ownership of that partition with your regular user account, i.e. *sudo chmod user:user /media/music*. 

I don't even have my external HDD connected to my PC anymore, it's connected to my file server. On some occasions I find myself getting permission denied errors when I try to copy music to the drive, but a simple "chmod -R 777 /media/music" solves that quickly (and I always do it via ssh, my file server is headless and has no input devices). But even on my PC, I just use smbmount to mount it as a regular drive.

It's pretty straightforward once you get used to it, although I need to learn more about NFS and switch to it from Samba.

---

### Post by reclusivemonkey on 2007-06-27
All my media goes in /home/ftp/media then music/movies/photos etc. all have their own directory. Its a throwback to my slackware days.

---

### Post by PCFascist on 2007-06-27
> **reclusivemonkey said:**
> All my media goes in /home/ftp/media then music/movies/photos etc. all have their own directory. Its a throwback to my slackware days.

Yeah, but that makes good sense... thanks for the idea.. this is exactly the feed back I am looking for.

---

### Post by Jose Catre-Vandis on 2007-06-28
> **PCFascist said:**
> Yeah, but that makes good sense... thanks for the idea.. this is exactly the feed back I am looking for.


But isn't this **precisely** what you asked to avoid? ;)

> "I am worried about keeping them under /home/musicuser/ because then most users on my network wouldn't be able to listen to my files if they wanted"

Sorry my attempt at help didn't help :)

---

### Post by paulg on 2007-06-28
/usr/local/music/lossy [oggs and other less superior codecs]
/usr/local/music/lossless [FLAC etc.]

I use symbolic links to my (and others) home directories for convenient access. I remove FLACs as my drive gets filled up (once every year or so) and haven't needed to span disks yet.

---

