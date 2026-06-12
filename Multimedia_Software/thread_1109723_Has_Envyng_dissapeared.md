---
title: "Has Envyng dissapeared?"
date: 2009-03-29
forum: Multimedia Software
---

### Post by Garratt on 2009-03-29
I'm doing a fresh install and just tried to install envyng after doing updates, then enabling restricted, universe, and multiverse repos, then doing another install update. That seemed to work fine however when i typed:

```
gunit@gunit-Pc:~$ sudo apt-get install envyng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng
gunit@gunit-Pc:~$ 

```

I went to the website to check if any info has changed etc.. but nothing seems to have.
[http://albertomilone.com/envyngfaq.html#A]("http://albertomilone.com/envyngfaq.html#A")

Has anyone used this lately or have any idea if there is currently a better way to install geforce drivers?? From memory this was the best and easiest way simply install -> run -> perfect graphics fix every time.

---

### Post by Garratt on 2009-03-29
nevermind I just broke ubuntu can't even use synaptic anymore

```
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


```

time to download intrepid and do another reinstall >.<

---

### Post by overdrank on 2009-03-29
There is a error in that line of the  /etc/apt/sources.list. Find it a correct it not need to reinstall.

---

### Post by Garratt on 2009-03-30
Yea I found that and fixed it and then decided to install intrepid anyway.

Intrepid came up with a restricted driver list which is a first for ubuntu, that has never happened before, so i installed the 177 nvidia driver and now i AM STUCK in  1024x768

I have tried the screen resolution settings it does absolutely nothing, even the help button on the settings window does not work, so I used the Nvidia X Server Settings to change resolution but the highest i can go is: 1360x768 and it looks very lop sided the only resolution that looks good is---->

The resolution I should be running at 1400x900 and prior to reformat Ubuntu was running this.

---

