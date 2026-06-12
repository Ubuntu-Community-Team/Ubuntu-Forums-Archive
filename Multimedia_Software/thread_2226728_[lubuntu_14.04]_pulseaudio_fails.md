---
title: "[lubuntu 14.04] pulseaudio fails"
date: 2014-05-28
forum: Multimedia Software
---

### Post by Kifferand on 2014-05-28
Hello,
I installed pulseaudio and pavucontrol on lubuntu 14.04, and when I launch pulseaudio, I get :
"Connection to Pulseaudio failed." (se the attached file)
I tried to launch it manually, and I get :
[HTML]~$ pulseaudio
W: [pulseaudio] core-util.c: Failed to open configuration file '/home/franck/.config/pulse//daemon.conf': Permission non accordée
W: [pulseaudio] daemon-conf.c: Échec lors de l'ouverture du fichier de configuration : Permission non accordée
[/HTML]
-> permission denied
I saw that emptying the ~/.pulse folder could help. It did not work in my case.
Any idea of what I could do ?

---

### Post by stealz on 2014-06-04
I am running Lubuntu 14.04 amd64 with pulse with success

Several ideas come to mind:

first of all check if you have thaf folder and file in your userfolder (I only have /etc/pulse/daemon.conf, no file in my userfolder) and if you have the required permissions.
you could try:

```
ls -l ~/.config/pulse
```

that should print out something like

```
-rw-r--r-- 1 yourusername yourusergroup 20480 Mai 27 15:22 somenumber-card-database.tdb
-rw-r--r-- 1 yourusername  yourusergroup    9 Mai 28 00:44 daemon.conf
```

and so on...

check if the folder exists, and if not create it with
```
mkdir ~/.config/pulse
```

if it does exist, check if it has the right permissions, i.e. it should be owned by your username and your group, in the above example yourusername and yourusergroup.

if it says something else (for example root root) you might have to change those permissions with chown:

```
sudo chown yourusername:yourusergroup ~/.config/pulse/daemon.conf
```

if you are not sure about your username and group, type

```
id
```
your username will be in brackets after uid=1000(yourusername), the groupname will be in gid=1000(yourgroupname)
mind you your id numbers my vary depending on distro and amount of users on your system, but thats not important here.

I hope this will help with your problem.

---

### Post by Bucky Ball on 2014-06-04
*Thread moved to **Multimedia & Video**.*

---

### Post by computermed3111 on 2015-05-12
Thanks to stealz above. I was having the same issue. But my error came when I tried to power on a virtual machine through Webmin commands. I received the exact error. Stealz, The recommended step worked for me! Thanks again you guys on here are very helpful.

---

### Post by Bucky Ball on 2015-05-13
*Thread closed.*

Necromancy. Welcome. Please don't wake the dead. ;)

---

