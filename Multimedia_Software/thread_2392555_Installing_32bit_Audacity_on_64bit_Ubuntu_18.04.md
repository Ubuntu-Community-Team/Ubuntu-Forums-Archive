---
title: "Installing 32bit Audacity on 64bit Ubuntu 18.04"
date: 2018-05-22
forum: Multimedia Software
---

### Post by G_M_Slater on 2018-05-22
I recently set up a new music production computer running Ubuntu 18.04, which is 64bit. There are several LADSPA plugins I regularly use with Audacity, which are only available in 32bit builds, so they do not show up as available. Is there any way to install the 32bit version of Audacity on a 64bit build of Ubuntu? If so, how? If not, is there any way to get the 64bit build to utilize 32bit LADSPA plugins?

---

### Post by kostkon on 2018-05-22
You could try this:
```
sudo apt-get install audacity:i386
```

---

