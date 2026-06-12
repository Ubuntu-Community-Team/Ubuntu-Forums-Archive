---
title: "youtube and flash player"
date: 2008-08-11
forum: Multimedia Software
---

### Post by Howitzer777 on 2008-08-11
so i'm trying to get my ubuntu to install flashplayer, when i download the tar.gz file and extract it with the archiver to my documents i get this [IMG]http://i35.tinypic.com/2vhyasp.jpg[/IMG]

i try running the install file but nothing happens. i chose all the options (run interminal, run, display)

my youtube videos look like [IMG]http://i33.tinypic.com/2lvlpmw.jpg[/IMG]


helP?

---

### Post by tuxxy on 2008-08-11
To install flash just do the following commands to install,

```
sudo apt-get install ubuntu-restricted-extras
```

If you already installed the restriced package you could try this to install the plugin for your browser

```
sudo apt-get install flashplugin-nonfree*

```

Now retry youtube, this link should also be of use

[https://help.ubuntu.com/8.04/internet/C/web-browsing.html](https://help.ubuntu.com/8.04/internet/C/web-browsing.html)

---

### Post by Howitzer777 on 2008-08-11
no dice


```
jack@jack-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for jack: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jack@jack-desktop:~$ sudo apt-get install flashplugin-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jack@jack-desktop:~$ 


```

---

### Post by tuxxy on 2008-08-11
Have you any other synaptics or adept running?, close all package managers before running the commands

---

### Post by Howitzer777 on 2008-08-11
ok, i did get to install all those things, but now it just says "hello, you either have a javascript turned off (i don't) or an old version of flash player, click here to get the latest flash player

---

### Post by timcredible on 2008-08-11
you have to restart firefox after installing flash

---

