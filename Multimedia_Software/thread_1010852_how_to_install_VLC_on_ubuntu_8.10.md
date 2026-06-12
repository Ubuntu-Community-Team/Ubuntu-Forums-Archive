---
title: "how to install VLC on ubuntu 8.10"
date: 2008-12-14
forum: Multimedia Software
---

### Post by yinglcs2 on 2008-12-14
Hi,

I am trying to install VLC on ubuntu 8.10. But I get the following error:

Can you please help?

```


~> sudo apt-get install vlc vlc-nox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc-nox is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.9.4-1ubuntu3) but 0.9.4+x264snapshot20080928+faad2.6.1-1~ppa1 is to be installed
E: Broken packages
~> 



```

Thank you.

---

### Post by tuskenraider on 2008-12-14
you could always just go download the deb files. Thats what i did.

maybe im lame..but sometimes its fun to go find the files you want download em and install them.  even if they are in the repositories. :lolflag:

tusken

---

### Post by albinootje on 2008-12-14
Did you add some ppa repositories ?
It looks like you have some conflict in vlc versions.

And also your message shows that vlc-nox is already installed.

Can you show us your /etc/apt/sources.list ?

---

### Post by SuperSonic4 on 2008-12-14
Do you have medibuntu sources installed? Posting /etc/apt/sources.list as suggested in post 3 will be good

```
sudo nano -w /etc/apt/sources.list
``` or
```
gksu gedit /etc/apt/sources.list
```

---

