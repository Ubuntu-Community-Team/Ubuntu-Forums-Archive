---
title: "Flashplugin-nonfree not found on FTP server?"
date: 2008-12-09
forum: Multimedia Software
---

### Post by pieisgood4589 on 2008-12-09
```
george@george-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 292 not upgraded.
Need to get 0B/18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 97035 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--18:11:26--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.17.194.70
Connecting to fpdownload.macromedia.com|96.17.194.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:11:27 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
```

That's the error message I get when I try to install the Flashplayer Plugin for Firefox in Ubuntu... What am I doing wrong? :confused:

---

### Post by wolfen69 on 2008-12-09
i have seen this happen before. don't worry, just go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu. then just click to install.

---

### Post by pieisgood4589 on 2008-12-09
Thanks, but I tried that already, it doesn't seem to work with my Firefox, Firefox doesn't show it in the about:plugins and it doesn't work when I try to, say, play a Youtube video.

---

### Post by pieisgood4589 on 2008-12-10
> **pieisgood4589 said:**
> Thanks, but I tried that already, it doesn't seem to work with my Firefox, Firefox doesn't show it in the about:plugins and it doesn't work when I try to, say, play a Youtube video.

BUMP
Cmon guys, since when has the community been this inactive? :mad:

---

### Post by pieisgood4589 on 2008-12-10
> **pieisgood4589 said:**
> BUMP
Cmon guys, since when has the community been this inactive? :mad:

I'm sorry, I'm going to have to bump this again, I just need to watch this one YouTube video! :lolflag:

---

### Post by albinootje on 2008-12-10
There are also different options to install flash-player, or to install the new flash-player 10 :
[http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/)

---

### Post by pieisgood4589 on 2008-12-10
> **albinootje said:**
> There are also different options to install flash-player, or to install the new flash-player 10 :
[http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/)

Tried that already, didn't work... *sigh* :confused:

---

### Post by gandaran on 2008-12-10
which version of ubuntu you running? 32-bits or 64-bits?
look, if you have ubuntu 7.10 32-bits, you have to install the .tar.gz package, get it here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
unpack the contents and just drop the libflashplayer.so file in /usr/lib/mozilla/plugins or /home/'user'/.mozilla/plugins (make the plugins folder)
it's simple and works!

---

### Post by pieisgood4589 on 2009-01-14
> **gandaran said:**
> which version of ubuntu you running? 32-bits or 64-bits?
look, if you have ubuntu 7.10 32-bits, you have to install the .tar.gz package, get it here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
unpack the contents and just drop the libflashplayer.so file in /usr/lib/mozilla/plugins or /home/'user'/.mozilla/plugins (make the plugins folder)
it's simple and works!

Thanks, that did it ;)

---

