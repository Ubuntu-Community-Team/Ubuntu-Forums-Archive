---
title: "hostname problem"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by emkay84 on 2006-05-10
Hi,
I hope someone can help me.
I faced a problem as after I edited the Network Setting
I leave the hostname and domain name blank on General Tab
After that when I want to use Terminal and Sudo this message appear:
> unable to lookup via gethostbyname
and I also cant access the network setup to fix the problem.

I've tried this solution that I get from other forum, but the problem still occured

> Recovery mode
Open a shell

   1. log in with root or sudo -s
   2. ifconfig eth0 down
   3. nano /etc/hosts
   4. edit the hostname on the line starting with 127.0.0.1 make sure you put the original "localhost" hostname
      and put your LAN ip like 192.168.*.* with an hostname like "ubuntubox"
   5. hostname "ubuntubox"
   6. ifconfig eth0 up
   7. done and then reboot to normal mode

I dont know how to edit this:
127.0.0.1 localhost.localdomain localhost 

FYI my username'login is khalidah
I hope someone can help me.

---

### Post by Sendervictorius on 2006-05-10
This just happened on a recent ubuntu forum. You cannot login as root, and you cannot use sudo. What to do?

Check out this thread: [http://ubuntuforums.org/showthread.php?t=171665](http://ubuntuforums.org/showthread.php?t=171665)

---

### Post by emkay84 on 2006-05-10
I've tried and the problem still occured

IS there posssible if i want to repair/reinstall  ubuntu and at the same time keep all the update and ubuntu software that have been install on my hard disk.](*,)

---

### Post by Freddox on 2006-05-10
If I understood your problem right, you havent tested the method about editing /etc/hosts because you dont know how do edit it?
Well, you erase things with backspace, and write with keys on the keyboard.. When you are done, you type CTRL + O, press enter because you want to save, then you press CTRL + X to exit. Type "reboot".

If this is NOT your problem Im assume that you have tried to enter recovery mode and type
```
hostname mynewhostname
```

If not, try that. (Or did you do any changes with /bin/hostname lately?)

And on a sidenote - if changing /etc/hosts dont help, try to edit /etc/hostname to reflect the /hosts/ file (Name your computer the same both places)

---

