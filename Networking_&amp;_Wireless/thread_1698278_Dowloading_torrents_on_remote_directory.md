---
title: "Dowloading torrents on remote directory"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by mer0090 on 2011-03-02
Hi,

I run Vuze on Ubuntu and I was wondering whether I can change the default directory for download in a network folder. I have a usb disk connected to my local network but when I try to browse it from the Vuze Options window I cannot see it (but I can see the disk from Nautilus).


I guess I have to mount on the filesystem the remote directory. I tried with sshfs but I did not manage.

Any idea?


Many thanks!

Sebastiano

---

### Post by mer0090 on 2011-03-02
I did find the solution here:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by ankith13 on 2011-03-02
Hi
  you can go through this link
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_113.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_113.html)

which tells you how to mount a network file in local and then you can browse to the mounted folder in vuze to give the default location....

I havent tried it yet ... be sure to take backup of /etc/fstab (as mentioned in the steps)....

Let me know if it worked...

Cheers
Ankith

---

### Post by ankith13 on 2011-03-02
your solution is probably better...:)

---

