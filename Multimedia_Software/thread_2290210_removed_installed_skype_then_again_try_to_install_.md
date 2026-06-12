---
title: "removed installed skype then again try to install it is not installable"
date: 2015-08-10
forum: Multimedia Software
---

### Post by mrityunjay23 on 2015-08-10
I had installed skype previously. But one day I have removed that from my system. Then i again try to install it is not getting installed. 
Showing 
> The following packages have unmet dependencies:
 skype : Depends: skype-bin
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to correct problems, you have held broken packages.
I have also run > dpkg -l |  grep skype-bin 
dpkg -l  | grep skype it is not showing any file.
After opening package manager I have also fixed Edit->Fix broken pacakge 
> apt-get autoclean apt-get update apt-get upgrade then  apt-get install skype It has not  worked for me.

---

### Post by ajgreeny on 2015-08-10
Enable the Canonical partner repositories which is where skype is now found and you should be able to install it easily in the usual manner.

---

### Post by mrityunjay23 on 2015-08-10
I have added canonical repositories. I have tried to install but it is giving same problem 
after typing > sudo ap-get purge skype*; sudo ap-get autoremove;rm -fr ~/.Skype;sudo apt-get update; sudo apt-get install skype
Error as shown below
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.




---

### Post by mrityunjay23 on 2015-08-11
>  sudo apt-get install skype pulseaudio:i386
following error
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pulseaudio:i386 : Depends: libasound2:i386 (>= 1.0.24.1) but it is not going to be installed
                   Depends: libdbus-1-3:i386 (>= 1.1.1) but it is not going to be installed
                   Depends: libpulse0:i386 (>= 1:1.1-0ubuntu15) but it is not going to be installed
                   Depends: libsndfile1:i386 (>= 1.0.20) but it is not going to be installed
                   Depends: libudev0:i386 (>= 147) but it is not going to be installed
                   Depends: libx11-6:i386 but it is not going to be installed
                   Depends: libx11-xcb1:i386 but it is not going to be installed
                   Depends: consolekit:i386 but it is not going to be installed
                   Depends: libasound2-plugins:i386 but it is not going to be installed
                   Recommends: pulseaudio-module-x11:i386 but it is not going to be installed
                   Recommends: gstreamer0.10-pulseaudio:i386 but it is not going to be installed
                   Recommends: rtkit:i386 but it is not going to be installed
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.


i am not able to correct this error.
I have opene package manager and Edit->Fix broken packages
After this, I have gain run above command same error comes.

---

