---
title: "How to install flash player"
date: 2009-04-06
forum: Multimedia Software
---

### Post by shariefbe on 2009-04-06
Hi,
 I am using UBUNTU 8.04...I downloaded the flash player from internet...but i am trying to install...but i cant...Can anyone help me?

---

### Post by dk92123 on 2009-04-06
google "adobe flash" and download the .deb or .tar.gz for linux (pretty sure they have a .deb -fyi: .deb is for debian and ubuntu is debian based.-> .rpms are for red hat based like fedora, centos and suse

after download close firefox and right-click the package you downloaded
-open w/package installer
-done-

---

### Post by eyefragment on 2009-04-06
You should be able to install the flash player directly through firefox.  If you go to a page where flash is required, firefox should tell you you are missing plugins.  At that point, select one of the three flash plugins, and install.  If this does not work, you can install flash through the package manager with the terminal (found under applications > accessories > terminal) command

```

sudo apt-get install flashplugin-nonfree

```

for Adobe's closed source version or 

```

sudo apt-get install gnash

```

for a community supported flash player.

---

### Post by shariefbe on 2009-04-08
I am getting this error
```


sharief@sharief-desktop:~/Desktop/softwares$ sudo apt-get install gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  adobe-flashplugin: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
  gnash: Depends: gnash-common (= 0.8.2-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
```

sharief@sharief-desktop:~/Desktop/softwares$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  adobe-flashplugin: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
sharief@sharief-desktop:~/Desktop/softwares$
```

I dont know what to do?

---

### Post by acimmarusti on 2009-04-08
why don't you just try:

```

sudo apt-get install ubuntu-restricted-extras

```

This installs flash player as well as several codecs for mp3 playback, dvd playback and certain video formats.

You won't run into dependency problems with this one, I guarantee that

---

### Post by SuperSonic4 on 2009-04-08
```
sudo apt-get -f install
```

Are you running 64 bit or 32 bit system, you can find out by typing ```
uname -m
```

---

