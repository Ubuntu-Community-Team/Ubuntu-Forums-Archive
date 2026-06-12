---
title: "Is there DRM package on Ubuntu? How to uninstall it?"
date: 2008-06-30
forum: Multimedia Software
---

### Post by Odrodzona-Sarmacja on 2008-06-30
Is there DRM package on Ubuntu? How to uninstall it?
I just got last two months horrific issues with freezes.
[http://ubuntuforums.org/showthread.php?t=840686](http://ubuntuforums.org/showthread.php?t=840686)
I just succeeded removing them. Everything points me to something alike DRM. I wonder therefore if there is on Ubuntu 8.04 any DRM present? If so, then how I uninstall this "windows vista"-virus package/module from my Xubuntu?

---

### Post by Trollslayer on 2008-06-30
There would have to be DRM in a specific application, it's not build into Ubuntu.
Most likely you have another problem.

---

### Post by Odrodzona-Sarmacja on 2008-06-30
Until I did an update on my software on my Xubuntu 7.04 last april I had no issues with freezes on my Xubuntu 7.04. After freezes started occurring on my Xubuntu 7.04 starting from may I switched to Xubuntu 8.04 and discovered I still have these freezes on Hardy. I did many re-installations and only on Xubuntu 7.04 without software update I had no freezes. I didn't use any other repositories then Ubuntu ones, medibuntu one and moblock one.

I have following applications installed from medibuntu:
Skype
Kaffeine
W32codecs
I have also installed from moblock:
Moblock
Mobloquer

I doubt any of these packages holds something causing these horrible freezes on my Xubuntu. Few days ago, when I had still these freezes I removed Skype, as it was internet application, just to see if it makes any difference. No difference occurred in freezes.

Also I use ALSA sound driver on all my applications and after removing totem player and gstreamer codecs I don't think I have any codec based issues on my Xubuntu.

The rest of my packages are from Ubuntu repositories. Also I have installed "KDE-base" for my KDE applications.

I removed freezes from now from my computer, but I still didn't found what was causing them. I am happy however I can use all my graphic apps and games again and browse internet when listening to internet radio without my Xubuntu freezing on me unexpectedly.

DRM is only one of working theories I have.
The other theory is that network-manager have a hidden rootkit of some kind (after all images taken with network-manager installed on system are entire 3Gb bigger then usual and I have /tmp and /home on other partitions).
The third theory is that Ubuntu have in repository (or medibuntu or moblock repositories) virus infected files and a virus is causing all these freezes.

However connection between existing internet connection and rendering using applications seemed to me pointing at DRM like program working silently and deadly on my Xubuntu. I would like to get rid off the problem entirely. Right now a software update can cause the freezes to return to my Xubuntu 8.04 again exactly as it did happen on my old Xubuntu 7.04 last april. And I have no idea which of the 100 updated software packages from medibuntu, ubuntu and moblock did it on my fiesty last april.

---

### Post by Odrodzona-Sarmacja on 2008-07-09
Ok. Here is an update. I had installed on Xubuntu 8.04.1 only these applications:
vlc
firefox
openarena
I removed every other application and most of system packages.
I had still freezes with networking on. So it is nothing to do with medibuntu repository and moblock repository. The freeze come from ubuntu repository and it is ubuntu os bound error.

Removing vbetool seemed to crash sometimes openarena to desktop instead of freezing computer and i could also watch vids for longer time, when connected to itnernet. Dunno why. When internet connected the freezes were still there though.

I found out that there is an issue with Simple DirectMedia Layer and libpng. It is SDML which is freezing computer. Upgrading libpng to version 1.2.27 removed one serious bug also causing freezes on ubuntu, but didn't remove the freezes from ubuntu.

---

