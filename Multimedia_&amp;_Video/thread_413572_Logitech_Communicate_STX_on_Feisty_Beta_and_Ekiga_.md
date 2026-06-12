---
title: "Logitech Communicate STX on Feisty Beta and Ekiga Working!"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by dansweat on 2007-04-19
Ok hey guys I am just putting this out there in the hope that It may even help 1 person.

I have upgraded from Edgy to Feisty and realised my webcam was not working in ekiga.
By not working i mean that ekiga was telling me that there were no detected devices.

**********Kernel***********
dannies@ubuntu:~$ uname -r
2.6.20-15-generic
dannies@ubuntu:~$ 
*****************************

I followed these steps from various forum posts.

Added the ekiga repository for feisty

deb [http://www.ekiga.org/admin/downloads/latest/ubuntu/feisty_x86/](http://www.ekiga.org/admin/downloads/latest/ubuntu/feisty_x86/) ./

selected update all packages and clicked ok.
This upgraded Ekiga to 2.0.9

I followed a forum post that said to make sure that the links

dannies@ubuntu:/dev$ ls -la *video*
lrwxrwxrwx 1 root root     11 2007-04-19 23:42 video -> /dev/video0
crwxrwxrwx 1 root video 81, 0 2007-04-19 23:37 video0

existed.  I was surprised to find that only 
crwxrwxrwx 1 root video 81, 0 2007-04-19 23:37 video0
existed. I then created the other link with

sudo ln -s /dev/video0 /dev/video

Checked out Ekiga agin and it was working!
The upgrade of Ekiga probably had nothing to do with getting this to work, but hey, its a newer version!

Could maybe anyone else who had the same problem confirm they followed the same steps to get theirs working?

---

### Post by dansweat on 2007-04-22
Ok, I have seemed to notice that at every reboot the /dev/video symlink that I have created gets deleted, requireing me to go over the process again.

Does anyone know a way to have this symlink done permanently?

---

### Post by dansweat on 2007-04-22
I think I may have found a nother problem.
Looks like my user does not have the group "video" attached.
When i looked in user manager i could not see the group "video" in the list of available groups.

This would explain why /dev/video0 is not being read by ekiga as the properties are 
crw-rw----  1 root video    81,   0 2007-04-22 17:32 video0

next reboot i will see if just being in group video as well shall rend the making a symlink unneccesary

---

