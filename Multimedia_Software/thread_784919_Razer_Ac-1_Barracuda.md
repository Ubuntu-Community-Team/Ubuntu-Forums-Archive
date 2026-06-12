---
title: "Razer Ac-1 Barracuda"
date: 2008-05-06
forum: Multimedia Software
---

### Post by charlesbw on 2008-05-06
Is it possible to get the Razer Ac-1 Barracuda sound card to work with Ubuntu 7.10

I am completely new to ubuntu and want to see what the buzz is all about, but I grew up on windows...so this is rough for me at the moment.

Also how do I install a flash plugin for firefox?

---

### Post by MaindotC on 2008-05-06
Hi, Charles, and welcome to Ubuntu! I along with other contributors to the site will help you as much as we can to embrace the full range of features of Ubuntu and help you experience the benefits of Ubuntu and all of its software which is mostly free, open source and widely supported.

Anytime you want to see if any hardware, such as the Razer Ac-1 Barracuda, is compatibile with Ubuntu, you can check the Hardware Compatibility List at [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport).  Typically what I do is type in google "ubuntu hardware compatibility list" or for a specific device I'll type "Razer Ac-1 Barracuda Ubuntu".  In fact, if you don't see anything related to it, you can test out the hardware yourself and add your results to the wiki and perhaps return the item if it doesn't earn a good rating.

The flash plugin for firefox can be installed individually but is also part of a package of software that contains proprietary code and although it can be installed on your system, the source code is not available or is not allowed to be changed.  This probably won't be an issue for you.

The flash plugin is part of a package called ubuntu-restricted-extras.  You can install it by opening a command prompt and typing the following:

```

#The following two lines are to ensure your system has the most current list of repository sources and #updates

sudo apt-get update
sudo apt-get upgrade

#This installs the flash plugin as well as other restricted packages
sudo apt-get install ubuntu-restricted-extras

```

You can also view the contents of what is being installed on your system by typing:

```


sudo apt-cache show ubuntu-restricted-extras

```

You can also browse a graphical list of packages, including the one you are installing, by selecting from the Ubuntu menu: Applications -> Add/Remove and then typing in the search box "restricted" or "flash plugin".

Hope this helps and post if you have any questions :)  Welcome to Ubuntu!

---

### Post by charlesbw on 2008-05-07
Thank you very much, I have spent a couple of hours reading through the forum trying to learn how to install applications and it seemed so irritating.  Thanks for making it simple.

---

