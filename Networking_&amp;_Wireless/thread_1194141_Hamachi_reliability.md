---
title: "Hamachi reliability"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by l3iodeez on 2009-06-22
I have set up Hamachi on my FTP server, it starts on boot, logs in, and goes online in my network, but after a while it fails, and I no longer see the server as online in my windows hamachi GUI. If I log into the server using SSH and reboot it or log hamachi out and back in then its right back up and working again. I am thinking that if I can't figure this out I will write a script to check if Hamachi is working and log out and back in if necessary, but that seems like an inelegant solution. Anybody else experience this issue? I am using Ubuntu desktop 64-bit 9.04.

---

### Post by hornetcoach on 2009-06-24
I know I am probably posting the wrong way, but I can never find the "new post" button on this dang forum site.  I guess I don't post enough.
My issue:
Hamachi downloads and appears to install but won't do 
hamachi-init nor will it run tuncfg.  All the files appear to be in the correct directories, but I get the following errors:

coach@coach:~$ cd hamachi-0.9.9.9-20-lnx
coach@coach:~/hamachi-0.9.9.9-20-lnx$
coach@coach:~/hamachi-0.9.9.9-20-lnx$ sudo make install

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..

Hamachi is installed. See README for what to do next.
coach@coach:~/hamachi-0.9.9.9-20-lnx$ sudo tuncfg
[COLOR="Red"]sudo: unable to execute /sbin/tuncfg: No such file or directory[/COLOR]
coach@coach:~/hamachi-0.9.9.9-20-lnx$

Anybody a Hamachi guru?:)

---

### Post by Beacon11 on 2009-06-25
Hornetcoach, if you're running 64-bit Ubuntu, try installing ia32-libs.

```

sudo apt-get install ia32-libs

```

---

### Post by l3iodeez on 2009-07-09
You have to install ia32-libs to make it work in 64-bit linux. It works, but is not reliable. It gets knocked offline and does not automatically reconnect. If I ssh into my box and logout and back in to hamachi it is right back up. Does it work any better in 32-bit?

---

