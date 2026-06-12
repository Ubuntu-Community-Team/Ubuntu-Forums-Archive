---
title: "I think I accidentally deleted my sound driver and flash... help!"
date: 2008-09-03
forum: Multimedia Software
---

### Post by Dr.Suave on 2008-09-03
Hi there,

In an attempt to fix a problem I was having with Flash (no sound came from flash apps), I have managed to disable all sound and flash on my computer... I know, it's easy to laugh at people like me.

Basically, I was trying to upgrade to Flash 10, following the steps on [COLOR="Blue"][this tutorial (http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")[/COLOR], but only got half way, as the link to his flash installer file was invalid. I downloaded a different installer from the flash website, and tried following his instructions with my own installer. It didn't work...

Here is everything that happened in Terminal to lead to my sound and flash being wiped:

```
extramedium@extramedium:~$ sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
[sudo] password for extramedium: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package nspluginwrapper is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswfdec-0.6-90
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  libflashsupport* swfdec-mozilla*
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 262kB disk space will be freed.
(Reading database ... 104107 files and directories currently installed.)
Removing libflashsupport ...
Removing swfdec-mozilla ...
extramedium@extramedium:~$ sudo rm -f /usr/lib/mozilla/plugins/*flash*
extramedium@extramedium:~$ sudo rm -f ~/.mozilla/plugins/*flash*
extramedium@extramedium:~$ sudo rm -f /usr/lib/firefox/plugins/*flash*
extramedium@extramedium:~$ sudo rm -rfd /usr/lib/nspluginwrapper
extramedium@extramedium:~$ sudo apt-get install ia32-libs nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
The following packages were automatically installed and are no longer required:
  libswfdec-0.6-90
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  nspluginwrapper
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 113kB of archives.
After this operation, 381kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com hardy/multiverse nspluginwrapper 0.9.91.5-2ubuntu2 [113kB]
Fetched 113kB in 8s (13.4kB/s)                                                 
Selecting previously deselected package nspluginwrapper.
(Reading database ... 104083 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-2ubuntu2_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.5-2ubuntu2) ...
extramedium@extramedium:~$ cd /home/extramedium/Documents/Downloads
extramedium@extramedium:~/Documents/Downloads$ wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
--21:51:09--  http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
           => `flashplayer10_install_linux_051508.tar.gz'
Resolving download.macromedia.com... 88.221.203.191
Connecting to download.macromedia.com|88.221.203.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:51:10 ERROR 404: Not Found.

extramedium@extramedium:~/Documents/Downloads$ tar zxvf flashplayer10_install_linux_081108.tar.gz
install_flash_player_10_linux/
install_flash_player_10_linux/libflashplayer.so
install_flash_player_10_linux/flashplayer-installer
extramedium@extramedium:~/Documents/Downloads$ sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
extramedium@extramedium:~/Documents/Downloads$ rm -rf ~/install_flash_player_10_linux/
extramedium@extramedium:~/Documents/Downloads$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
*** NSPlugin Viewer  *** ERROR: libcurl.so.3: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
extramedium@extramedium:~/Documents/Downloads$ cd /home/extramedium/Documents/Downloads/install_flash_player_10_linux
extramedium@extramedium:~/Documents/Downloads/install_flash_player_10_linux$ ./configure
bash: ./configure: No such file or directory
extramedium@extramedium:~/Documents/Downloads/install_flash_player_10_linux$ /configure
bash: /configure: No such file or directory
extramedium@extramedium:~/Documents/Downloads/install_flash_player_10_linux$ 
```

So basically, I deleted a lot of stuff, without reinstalling anything.
[B]
Can someone help me get my sound and flash back (and maybe even get flash to play sound as an added bonus? :))[/B]

I have a Creative Sound Blaster Audigy 4 Soundcard, and am running Hardy Heron x64!

I think the steps of the tutorial that I successfully carried out are as follows (However, they might have failed, please have a little look at the Terminal dialogue above to see what really happened, as I am still a bit clueless about Linux, and don't really know what went on):

> 1. Make sure you don't have any other flash plugin installed on your system:
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper

1.1 To be sure we don't have any other old flash libs let's cleanup the folders where it usually resides:
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


2. Install ia32-libs and latest nspluginwrapper
sudo apt-get install ia32-libs nspluginwrapper

Cheers!

---

### Post by Dr.Suave on 2008-09-03
Also, is there anyway anything I did could have sped up my internet speed? As I noticed my downloads suddenly got a lot faster afterwards (which could have been a coincidence).

---

### Post by Dr.Suave on 2008-09-03
Actually I've managed to fix everything now - even the sound in flash!

---

