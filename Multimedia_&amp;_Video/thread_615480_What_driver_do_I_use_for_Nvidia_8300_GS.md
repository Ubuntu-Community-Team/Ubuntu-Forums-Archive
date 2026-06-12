---
title: "What driver do I use for Nvidia 8300 GS?"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by GoJa on 2007-11-17
I have a new dell box with Ubuntu 7.04.  I have a Nvidia GeForce 8300GS (pci ID 0423).

I was reading the info at this URL:
[http://www.albertomilone.com/latest_...sf_feisty.html](http://www.albertomilone.com/latest_...sf_feisty.html)

In step 3 there are references to loading different versions of the driver depending on your video card model, and links to a document to check if your card is supported. I search by both model number (8300) and pci ID (0423). I couldn't find either listed

What version of the driver do I use??

---

### Post by Qwerty_ on 2007-11-18
The simplest way is to install the restricted driver.

System>Administration>Restricted Drivers manager.

---

### Post by GoJa on 2007-11-18
I've seen a number of posts mentioning the same technique, but my system wouldn't let me.  I have another post open in this forum asking how to "fix" the restricted devices manager.  When I try to use it all it does is tell me that my hardware doesn't need any restricted drivers.  I've even updated the package but I still get the same message.  It gives me no options to enable any drivers or do anything else.

Any ideas or hints on how to get the restricted devices manager to work?

---

### Post by steved on 2007-11-24
I am having precisely the same problem. No way to use the restricted drivers.

---

### Post by steved on 2007-11-25
Figured it all out after (finally) getting someone knowledgeable at Dell.

1. Run sudo dpkg-reconfigure xserver-xorg from a terminal
2. Accept all the defaults EXCEPT:
3. When you come to the part about screen res, check off ALL of them. This is the part that got me. I was just checking off the 1440x900 and the 1024x768 and below and I could never get gnome back up.
4. Restart gnome with sudo /etc/init.d/gdm restart

Once I did that, I was able to select higher resolutions from the "screen resolution" settings in the menu. I did notice something strange. Even after selecting 1440x990, the built-in monitor menu reported that it was only displaying at 1152xXXX. I forget how I fixed that but I did. It could have been after I installed envy (read on).

OK, then, to get the 3d drivers working, go to [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and look for envy_0.9.9-0ubuntu1_all.deb on the front page about half way down. Click it. The package will install itself for you. I think at this point I restarted gdm again and all was right with the world.

Hope this helps. Good luck!

---

