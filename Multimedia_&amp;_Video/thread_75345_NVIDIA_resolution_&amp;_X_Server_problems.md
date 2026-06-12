---
title: "NVIDIA resolution &amp; X Server problems"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by SeanCallan on 2005-10-13
Hey Guys!

I went to Nvidia and downloaded the .run drivers for linux. I tried to run it in the terminal but it keeps telling me there's an X Server running. This is exactly what I did:

alt+ctrl+f2
Logged in
sudo killall X
sudo sh NVIDIA... .run

ERROR X Server still running

Then I tried:
alt+ctrl+f2
Logged in
sudo init 3
sudo sh NVIDIA... .run

ERROR X Server still running

Can someone point me in the right direction?

---

### Post by bhagabhi on 2005-10-13
alt + ctrl + f1
log in
sudo /etc/init.d/gdm stop

- then you are ready to go. ;) 

have done it lots trying to get my nvidia-card correct. :???:

---

### Post by tomriddle on 2007-10-09
alt + ctrl + f1
log in
sudo /etc/init.d/gdm stop

or install the NVIDIA last service pack

---

### Post by martin8768 on 2007-10-18
hey guys im new here and im still sorta a beginners, maybe a bit more and i did all that and it worked until it asked for a kernel or something? and thats were i got lost, then it went to find the kernel on nvidia's ftp site and couldn't (i have a wifi) so should i move my desktop to a wired connection with DHCP or should i download this kernel before hand? im really lost now.

---

### Post by RomuleGL on 2008-03-09
> **SeanCallan said:**
> Hey Guys!

I went to Nvidia and downloaded the .run drivers for linux. I tried to run it in the terminal but it keeps telling me there's an X Server running. This is exactly what I did:

alt+ctrl+f2
Logged in
sudo killall X
sudo sh NVIDIA... .run

ERROR X Server still running

Then I tried:
alt+ctrl+f2
Logged in
sudo init 3
sudo sh NVIDIA... .run

ERROR X Server still running

Can someone point me in the right direction?
Hi all! I had this problem, and i know how to install. So....

alt+ctrl+f2
Logged in
sudo killall (X - this is don't correctly, should be..) gdm
sudo sh NVIDIA... .run

if at the process installation you have the problem with "libc", be fore installation type - sudo apt-get install build-essential

Good luck,
see you soon.

---

