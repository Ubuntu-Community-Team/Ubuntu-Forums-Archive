---
title: "need help with online videos"
date: 2012-03-08
forum: Multimedia Software
---

### Post by zaydius1729 on 2012-03-08
Hello,

I need help with online video players. I just installed ubuntu 11.10 about a week ago on my ASUS n50v. I updated everything and installed flash. everything was working fine. then the software center showed a few updates. I installed all of them. since then I cannot watch videos on some of the websites. Youtube works fine ... but videos on CNN, BBC, Facebook.... none of those work. when i click on videos on fb it says that i need to install adobe flash. when i check in the software center it says that it has already been installed.

I would really appreciate some help with this since i am a bit of a newbie when it comes to this. also i have been using mozilla and chrome and have the same problem in both. 

thank you!

---

### Post by shantiq on 2012-03-09
hi zaydius

maybr run this in terminal see it if fixed it  it is from [**here**]("http://www.futuredesktop.org/")   i too had problems on oneiric with flash at first   i think i probably did this 


> Install Flash plugin

Install Flash browser plugin. This will install either 32 or 64-bit Flash depending on your operating system. These packages come from Canonical`s Partner repository which you activated in the step 7a).

First, remove old, unnecessary packages.

```
sudo apt-get remove --purge adobe-flashplugin flashplugin* nspluginwrapper
```

Install 32 or 64-bit Flash. Answer "Y" to confirm this operation.

```
sudo apt-get install --reinstall adobe-flashplugin
```

---

### Post by winh8r on 2012-03-09
Click on the "Help with Flash" link in my sig below and run Flash Aid, it will ensure that your flash plugins and versions are optimised for your Ubuntu/Firefox combination.

Hope this helps

---

