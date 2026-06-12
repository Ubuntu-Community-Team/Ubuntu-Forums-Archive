---
title: "Why is my flash not working..."
date: 2009-03-10
forum: Multimedia Software
---

### Post by hinge on 2009-03-10
Hi,

I have been running Ubuntu for some time now I have several computers with ubuntu. I have installed the system tons of times. I have never had problems with getting flash to work in firefox - until now!!! :(

I usually simply install the ubuntu-restricted-extras package which includes the flashplugin-nonfree. This usually works like a charm...

```

sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm running firefox 3.0.7

How can I troubleshoot this - what should I look for??

---

### Post by saxofoner on 2009-03-10
So what exactly is wrong?  Is it acting like flash is not installed at all?  I would sudo apt-get remove --purge flashplugin-nonfree and then reinstall it.

---

### Post by Jimmynemo2 on 2009-03-10
From your log posted there, it looks like it's already installed, so thats good.

What may be cuasing the issue, i recently went through as well, is go to synaptic, and type flash, remove all but one (probobly the one you are trying to install would be good to keep). 

Hopefully that helps, and for some reason it took care of the problem for me.

---

