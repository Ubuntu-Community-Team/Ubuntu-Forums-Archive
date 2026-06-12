---
title: "Using 2 drives"
date: 2008-02-16
forum: Mythbuntu
---

### Post by ghostwalker50 on 2008-02-16
Hi want  use an 40 GB Drive for the OS/logs and other stuff, and a 400GB drive for VIDEOS, TV SHOW, PICS , MUSIC. 

how do i redirect myth tv to us ethe other drive. this change will be when i reinstall to 8.04. is that make a difference.

---

### Post by newlinux on 2008-02-16
In the backend setup select a directory that is on your 400GB drive for your recordings. And in the frontend setup select  directories on your frontend drive for mythgallery, mythmusic, and mythvideo. I haven't used mythbuntu, but you can do this in the regular setup screens (setup in mythfrontend, and mythv-setup). I use separate drives for all my media too...

---

### Post by ghostwalker50 on 2008-02-17
Ok how will this redo the shair points on the system? or do i have to shair them my self.

thanks
Fernando

---

### Post by Levander on 2008-02-18
Videos are stored in /var/lib/mythtv/recordings by default.  But, there's some menu where you can change this directory.  You can use /etc/fstab to auto-mount the 400GB drive on that directory every time you reboot.

Make sure the permissions are correct on the /var/lib/mythtv/recordings directory.  If you don't, mythbackend (I think it's the backend and not the frontend) fails with a pretty vague error message.

I actually have a very similar setup to yours and newlinux has a genericly terrible nick, but a great suggestion.  I'm gonna do that because my smaller drive that has the operating system on it has quite a bit of space at the end where I can keep all my music.

---

### Post by newlinux on 2008-02-18
> **Levander said:**
> Videos are stored in /var/lib/mythtv/recordings by 
I actually have a very similar setup to yours and newlinux has a genericly terrible nick, but a great suggestion....

Hey, you raggin' my nickname? Wassup with that? :) What can I say, when I picked it I was devoid of creativity and now I use it in other forums.

---

### Post by ubnewbie2 on 2008-02-18
> **newlinux said:**
> Hey, you raggin' my nickname? Wassup with that? :) What can I say, when I picked it I was devoid of creativity and now I use it in other forums.

He must hate mine too then  :)

---

