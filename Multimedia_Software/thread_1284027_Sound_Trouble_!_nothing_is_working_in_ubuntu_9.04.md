---
title: "Sound Trouble ! nothing is working in ubuntu 9.04"
date: 2009-10-06
forum: Multimedia Software
---

### Post by prasad.bh1 on 2009-10-06
Having tried all the options to make my microphone work, I finally thought to install alternate sound system OSS..


I used this link to set-up OSS

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

But after that nothing worked

so, I uninstalled it using
cd /var/lib/dpkg/info
sudo rm oss-linux*

and again tried to install alsa, according to prcedure given at 

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

Now, I am in mess and nothing ( sound as well as microphone ) is working now.

see here,

#cat /proc/asound/version
cat: /proc/asound/version: No such file or directory


Before that I had opened question for microphone not working...

83988       Microphone is not working on Acer 4736G Laptop in Ubuntu 9.04

But could not get the solution :(

can you please help !


wr,
prasad

---

