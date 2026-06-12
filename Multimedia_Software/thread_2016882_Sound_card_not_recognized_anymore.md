---
title: "Sound card not recognized anymore"
date: 2012-07-04
forum: Multimedia Software
---

### Post by anarvoshir on 2012-07-04
Hello to everyone,

I have a HP Mini and I have installed Ubuntu 10.04 LTS. When these has been installed, the sound card was recognised but I had no sound. I've checked some forums and found out that installing Alsa 1.0.23 will be the solution. I've done this following the information on this website : [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) and it worked. 
However this morning the kernel has been updated through the Update Manager and the sound is not working anymore; the sound card is not even recognized anymore.
I've tried to check if I could find a solution on line but seems quite confusing.
So could someone helps me?

Thanks,
Michaël

---

### Post by cipherboy_loc on 2012-07-04
Run the following commands in a terminal, please, and report the output (in code tags):
```

lspci | grep Audio

```
This will tell us what audio card you have.

```

uname -a

```
This will tell us which kernel version you have.

```

alsactl --version

```
This will tell us what alsa version you have.

---

### Post by Yellow Pasque on 2012-07-04
You need to run make install for each of those three directories again (and every time you install a new kernel).

---

### Post by anarvoshir on 2012-07-05
To cipherboy

Here the results of the commands :


michael@ubuntu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

michael@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-41-generic #91-Ubuntu SMP Wed Jun 13 11:43:55 UTC 2012 x86_64 GNU/Linux

michael@ubuntu:~$ alsactl --version
alsactl version 1.0.23

I should maybe also mention that when I go to sound preferences it says that i have a 'Dummy output' instead of the soundcard.

Hope you'll be able to help me :)
Thanks,
Michaël

---

### Post by anarvoshir on 2012-07-05
Hello me again

I've run a make install as advised by Temüjin and it worked.... I have the sound again.... Yeaaaaaah

thanks to all
Michaël

---

### Post by anarvoshir on 2012-07-05
Me again....

The sound did actually come back in every programs but VLC. Would you have an idea of how to fix that?

Thanks,
Mick

---

### Post by Olmen on 2013-03-01
> **Temüjin said:**
> You need to run make install for each of those three directories again (and every time you install a new kernel).

I have this same problem. To which three folders are you referring?

---

### Post by Yellow Pasque on 2013-03-01
You have to see the OP's link in the first post to understand. That probably doesn't apply to you anyway (unless you're running Lucid). It's best to start your own thread and give: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

