---
title: "No alsamixer?"
date: 2008-05-25
forum: Multimedia Software
---

### Post by wormeyman on 2008-05-25
After tinkering a lot trying to get my sound working i followed the sticky guide at the top of the forum inlucding purging and re-installing alsa now i get:

```
eric@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
eric@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
eric@ubuntu:~$ sudo apt-get install alsamixer
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixer
eric@ubuntu:~$ grep 'audio' /etc/group
audio:x:29:eric,guest,pulse,wormeyman
eric@ubuntu:~$ 

```

It worked when i first installed hardy and now it doesn't i even got another sound card thinking it was an audio issue and things still do not work :(

Audio doesn't work on the hardy live cd either.

---

### Post by wormeyman on 2008-05-26
bump

---

### Post by juicyoner on 2011-01-12
help!

same damn problem.

---

