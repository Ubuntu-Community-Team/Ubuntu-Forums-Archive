---
title: "Install software installer"
date: 2017-09-15
forum: Multimedia Software
---

### Post by steveredshaw on 2017-09-15
I inadvertently removed the software installer program - I was tidying the installed programs list and there were 2 entries so I removed one of them, but now the software installer has disappeared from my menu!

Can I reinstall this from the terminal?

thanks...

---

### Post by wildmanne39 on 2017-09-15
What version of ubuntu are you using because the name changed of the package.

---

### Post by steveredshaw on 2017-09-15
ubuntu studio 17.04 zesty (x86-64)

I have tried tracking down the software center for zesty, but without success

thanks....

---

### Post by wildmanne39 on 2017-09-15
Sorry for the delay I had to install Ubuntu Studio to find the name of the software installer, please do:
```
sudo apt install --reinstall software-center
```

---

### Post by steveredshaw on 2017-09-15
Thanks, but that gives an error message;

> Package software-center is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'software-center' has no installation candidate

---

### Post by wildmanne39 on 2017-09-15
Did you just copy and paste the command because it worked perfectly on ubuntu studio that I installed.

Make sure your repositories are enabled. I do not know how to check that on this distro.

---

### Post by oldos2er on 2017-09-15
> **steveredshaw said:**
> Thanks, but that gives an error message;

You might just need to run  ```
sudo apt update
``` first.

---

### Post by steveredshaw on 2017-09-16
No, an 'update' does not enable software-center to be reinstalled

---

### Post by steveredshaw on 2017-09-16
[-X I've really messed this up by removing the original software center!!

I have found a .deb file software centre package, but trying to install it brings up a whole list of dependencies which are obviously missing from my computer.

Maybe just reinstalling Ubuntu would be easier? Fresh start....

---

### Post by wildmanne39 on 2017-09-16
I do not have any other recommendations, that command should have worked, like it did on mine when I installed ubuntu studio and tested it to make sure.

What is the the shame on you emoji?

---

### Post by steveredshaw on 2017-09-16
Well, tidying up - removing what I thought were duplicate installations. I did the same for Evince, but that was easy to get back!

---

### Post by wildmanne39 on 2017-09-16
One last thing to try, in the terminal install synaptic package manager then open it and reload the repositories by clicking on the reload  button then in the search field type softeware-center then right click on the box and choose to reinstall.

Run:
```
sudo apt install synaptic
```
you should not have to reboot before using synaptic.

---

### Post by oldos2er on 2017-09-16
> **steveredshaw said:**
> Well, tidying up - removing what I thought were duplicate installations. I did the same for Evince, but that was easy to get back!

Can we take a look at your sources? Please post all the output of these commands: ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/
``` Don't think you need to reinstall yet.

---

### Post by steveredshaw on 2017-09-16
Synaptic package manager looked promising but software center did not come up at all (I did get a Chinese version!). I did locate dependencies which I marked for installation, but then tried to install the .deb software-center package - again, just a list of unmet dependencies.

So next attempt;

```
cat /etc/apt/sources.list# deb cdrom:[Ubuntu-Studio 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main multiverse restricted universe 


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ zesty main restricted 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ zesty main restricted 


## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ zesty-updates main restricted 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ zesty-updates main restricted 


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ zesty universe 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ zesty universe 
deb http://gb.archive.ubuntu.com/ubuntu/ zesty-updates universe 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ zesty-updates universe 


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ zesty multiverse 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ zesty multiverse 
deb http://gb.archive.ubuntu.com/ubuntu/ zesty-updates multiverse 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ zesty-updates multiverse 


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse 


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu/ zesty partner 
# deb-src http://archive.canonical.com/ubuntu/ zesty partner 


deb http://security.ubuntu.com/ubuntu/ zesty-security main restricted 
# deb-src http://security.ubuntu.com/ubuntu/ zesty-security main restricted 
deb http://security.ubuntu.com/ubuntu/ zesty-security universe 
# deb-src http://security.ubuntu.com/ubuntu/ zesty-security universe 
deb http://security.ubuntu.com/ubuntu/ zesty-security multiverse 
# deb-src http://security.ubuntu.com/ubuntu/ zesty-security multiverse 
deb https://dl.winehq.org/wine-builds/ubuntu/ zesty main 
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ zesty main 
deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main 
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ xenial main 
```

```
ll /etc/apt/sources.list.d/total 64
drwxr-xr-x 2 root root 4096 Sep  7 18:15 ./
drwxr-xr-x 6 root root 4096 Sep  7 18:14 ../
-rw-r--r-- 1 root root  141 Sep 16 20:04 embrosyn-ubuntu-cinnamon-zesty.list
-rw-r--r-- 1 root root  136 Sep  7 18:15 embrosyn-ubuntu-cinnamon-zesty.list.save
-rw-r--r-- 1 root root  135 Sep 16 20:04 embrosyn-ubuntu-xapps-zesty.list
-rw-r--r-- 1 root root  130 Sep  7 18:15 embrosyn-ubuntu-xapps-zesty.list.save
-rw-r--r-- 1 root root   61 Sep 16 20:04 insync.list
-rw-r--r-- 1 root root   58 Sep  7 18:15 insync.list.save
-rw-r--r-- 1 root root   55 Sep 16 20:04 megasync.list
-rw-r--r-- 1 root root   53 Sep  7 18:15 megasync.list.save
-rw-r--r-- 1 root root  188 Sep 16 20:04 opera-stable.list
-rw-r--r-- 1 root root  187 Sep  7 18:15 opera-stable.list.save
-rw-r--r-- 1 root root  137 Sep 16 20:04 ricotz-ubuntu-unstable-zesty.list
-rw-r--r-- 1 root root  132 Sep  7 18:15 ricotz-ubuntu-unstable-zesty.list.save
-rw-r--r-- 1 root root  139 Sep 16 20:04 wine-ubuntu-wine-builds-zesty.list
-rw-r--r-- 1 root root  134 Sep  7 18:15 wine-ubuntu-wine-builds-zesty.list.save
```

---

### Post by wildmanne39 on 2017-09-16
Go into synaptic click settings>repositories and make sure under ubuntu software that the first four repositories are ckecked, I am including a screenshot then reload the list and look for software-center again.

Can you install any applications at all from the terminal or synaptic? I personally prefer synaptic over software center it is more powerful and dependable in my opinion.

---

### Post by steveredshaw on 2017-09-16
My Synaptic Package Manager looks like this - no extra software-center packages are showing up (image attached).

I can install software via the terminal.

---

### Post by deadflowr on 2017-09-16
software-center is dead.
long live ubuntu-software or gnome-software!
try installing either one of those.
Preferably ubuntu-software
```
sudo apt install ubuntu-software
```
as it's gnome-software with tweaks for Ubuntu

---

### Post by wildmanne39 on 2017-09-16
This is the one for ubuntu studio of mine 17.04 please notice when the repositories open it is under the first tab ubuntu software, I believe that is the difference. Once they are all checked you have to click the reload button so it will download the new repositories just added, if that does not do it I have no more ideas.

You did not answer my question can you install any software at all?

---

### Post by wildmanne39 on 2017-09-16
> **deadflowr said:**
> software-center is dead.
long live ubuntu-software or gnome-software!
try installing either one of those.
Preferably ubuntu-software
```
sudo apt install ubuntu-software
```
as it's gnome-software with tweaks for Ubuntu
That is what I thought as well but software-center is in ubuntu studio, I installed ubuntu studio just to find out.

---

### Post by deadflowr on 2017-09-16
> **wildmanne39 said:**
> That is what I thought as well but software-center is in ubuntu studio, I installed ubuntu studio just to find out.

Not from Ubuntu's repos, not in zesty.
[https://packages.ubuntu.com/search?suite=zesty&arch=any&searchon=names&keywords=software-center]("https://packages.ubuntu.com/search?suite=zesty&arch=any&searchon=names&keywords=software-center")

Though I think ubuntu-software will show in the menu as software center...

---

### Post by steveredshaw on 2017-09-16
:) OK, got it - searched for 'software' rather than 'software-center' and now have the software prog back on my computer and back in my menu. ubuntu-software seems to be the same as I've got from Synaptics Package Manager. However no content is showing up on it!!


PS - It's useful to know also that the Synaptics Package Manager can be used to install software. Thanks for all the help and advice...

---

### Post by oldos2er on 2017-09-16
> deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main You need to disable anything not "zesty," like the above source, or there are going to be problems. You should be able to do this in Synaptic, Settings, Repositories. If you need further help, please ask.

---

### Post by wildmanne39 on 2017-09-16
Glad it is working again, The first thing I do is install synaptic when I do a fresh install because it comes in handy though I use the terminal most of the time these days though.

---

### Post by deadflowr on 2017-09-16
> **steveredshaw said:**
> :) OK, got it - searched for 'software' rather than 'software-center' and now have the software prog back on my computer and back in my menu. ubuntu-software seems to be the same as I've got from Synaptics Package Manager. However no content is showing up on it!!

ubuntu-software can take a very long time to load.
Which is why it's set to auto start at login, normally.
(In /etc/xdg/autostart there should be a file marked gnome-software-service.desktop.
This file sets it to start in the background so it loads quicker when you actually click to launch it, since it's already running.
Though, I am not sure it loads quicker than synaptic, even with the  head start.)

---

### Post by steveredshaw on 2017-09-17
All up and running now.

---

