---
title: "troubles mounting DvD iso"
date: 2010-02-02
forum: Multimedia Software
---

### Post by Azerothsbest on 2010-02-02
I am trying to mount a DvD iso, so I can run the program without burning it to dvd. I have used 2 dvd's trying to burn it with K3B and both disks I put in, give me a bad medium error. So I have decided to try and mount it and play the software. I have gISOMount and clicked on the mount but nothing ever happened not really sure what to watch for either. When trying to mount in the terminal this is what I get.

Attempt 1
mongoose@mongoose-laptop:~$ sudo mount -o loop /mongoose/Desktop/rose.iso /media/iso
/mongoose/Desktop/rose.iso: No such file or directory
--------------------------------------------------------------------------------------------------

Attempt 2 (without loop)

mongoose@mongoose-laptop:~$ sudo mount -o /mongoose/Desktop/rose.iso /media/iso
mount: can't find /media/iso in /etc/fstab or /etc/mtab
--------------------------------------------------------------------------------------------------
Any help would be appreciated thanks :)

---

### Post by LuridCinema on 2010-02-02
If the ISO is a DVD movie you can open w/ VLC

---

### Post by Azerothsbest on 2010-02-02
It's not a movie, it's Rosetta Stone.

---

### Post by Azerothsbest on 2010-02-02
Ha ha I figured it out! I forgot to do the /home/mongoose/ect... Thanks for your help.

---

