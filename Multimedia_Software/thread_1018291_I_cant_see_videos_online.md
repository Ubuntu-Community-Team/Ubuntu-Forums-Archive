---
title: "I cant see videos online?"
date: 2008-12-21
forum: Multimedia Software
---

### Post by douggiephresh on 2008-12-21
I tried to uninstall and reinstall flashplugin-nonfree as that usually fixes the problem, but now i get this message when i try to install it.



doug@doug-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 142 not upgraded.
Need to get 0B/18.9kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 122964 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--23:41:27--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.7.50.70
Connecting to fpdownload.macromedia.com|96.7.50.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:41:28 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

doug@doug-laptop:~$

---

### Post by 2hot6ft2 on 2008-12-22
> **douggiephresh said:**
> I tried to uninstall and reinstall flashplugin-nonfree as that usually fixes the problem, but now i get this message when i try to install it.



doug@doug-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and [COLOR="DarkRed"]142 not upgraded[/COLOR].
Need to get 0B/18.9kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 122964 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--23:41:27--  [url]http://fpdownload.macromedia.com/get/flashplayer/current/[COLOR="DarkRed"]install_flash_player_9_linux.tar.gz[[/COLOR]/url]
           => `./[COLOR="DarkRed"]install_flash_player_9_linux.tar.gz[/COLOR]'
Resolving fpdownload.macromedia.com... 96.7.50.70
Connecting to fpdownload.macromedia.com|96.7.50.70|:80... connected.
HTTP request sent, awaiting response... [COLOR="DarkRed"]404 Not Found[/COLOR]
23:41:28 [COLOR="DarkRed"]ERROR 404: Not Found.[/COLOR]

download failed
The Flash plugin is NOT installed.

doug@doug-laptop:~$
Let me see here. You have 142 updates that you haven't installed and are trying to install flash player 9 while flash is up to version 10.? now. Perhaps if you ran
```
sudo apt-get update
```
it might help since I would have to assume from that info that your source lists must also be out of date as well. Then maybe it wouldn't keep trying to get a plugin that has been replaced with a newer version which would explain the 404 ERROR as they have replaced that page and it no longer exists.

---

### Post by douggiephresh on 2008-12-22
i ran all the updates, tried again to install flash-plugin non free and i get this message .. (also, when i go to youtube, it tells me that i either have flash turned off or have an old version of adobe)






doug@doug-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
doug@doug-laptop:~$




just to see what it would do I "autoremoved" whatever that did

---

### Post by nordmichael29 on 2008-12-22
try going to the adobe website downloading the flash player for your os (assuming ubuntu considering the forum we're on) and then installing that while FF is closed? that's how I had to do it on an older satellite laptop.

---

### Post by wolfen69 on 2008-12-22
go to synaptic or adept if you are using kubuntu and completely remove flashplugin-nonfree if it is installed. next do: ```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") and download the .deb flash file for ubuntu. put it in your home folder. then do ```
sudo dpkg -i install_flash_player_10_linux.deb
``` restart firefox if open.

---

### Post by douggiephresh on 2008-12-22
Everything works until the last step. I have amd 64 and it says the architecture is wrong.

And when i do sudo apt-get install flashplugin-nonfree it still trys to install version 9, which you can see from my previous post.

---

### Post by douggiephresh on 2008-12-22
bump

---

### Post by douggiephresh on 2008-12-23
bump

---

### Post by Amy| on 2008-12-26
> **douggiephresh said:**
> bump


I'm having the same problem you may still be having.  I followed all of the steps in the above posts and youtube is still giving me this message:Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 

I'm new to Linux, so I'm relying on Google (which leads here 90% of the time) and it's slow going.  Anybody have any new fixes for this?

---

