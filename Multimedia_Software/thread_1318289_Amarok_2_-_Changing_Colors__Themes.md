---
title: "Amarok 2 - Changing Colors / Themes"
date: 2009-11-07
forum: Multimedia Software
---

### Post by Stingxgl on 2009-11-07
Hello, I have been trying to build my own custom version of Linux (Mint 7) and have started downloading media software to better suit my needs. After a long testing period I decided that Amarok 2 was the music player for me. However I quickly discovered that Amarok 2 doesn't have a built in "appearance" tab to allow changing the softwares color scheme. Amarok has being going though changes and has not (yet?) allowed UBuntu/Mint/Gnome users to change the schemes in their KDE based software. I want to make it match my Linux theme!

I searched outdated forum posts and quickly discovered that because Amarok was written for KDE it required it's proprietary "Kcontrol" settings software to make appearance adjustments. However Kcontrol is obsolete. Kcontrol was replaced with "systemsettings". I installed that and discovered that it doesn't include the necessary packages to allow the appearance changes to KDE software (Amarok in my case). I was unable to easily find documentation that gave a "how to" install systemsettings to in Gnome to make these types of changes.

So after a long winded intro, I decided to post the "how to" myself. 

_HOW TO INSTALL KDE SYSTEMSETTINGS TO ALLOW CHANGES TO AMAROK_

1. Open a Terminal

2. Paste the following line into the terminal:
> sudo apt-get install systemsettings kdebase-workspace-bin
3. To be sure all your KDE packages are compiled paste the following into a terminal:
> kbuildsycoca4 --noincremental
***There will be errors - Ignore them unless they prevent you from finishing.***

4. Start the system settings software by typing the following into the terminal:
> systemsettings
5. Under "look & Feel" double click "Appearance."

6. From within the "Style" tab you can change the "Widget Style" to reflect what you want Amarok (or your KDE program of choice) to look like.


If you are confident that you have set the settings for good and want to clear up the installed packages you can remove what we installed without loosing the new color scheme. Remove them by typing the following into a terminal window:
> sudo apt-get remove systemsettings kdebase-workspace-bin

Please note I'm an average/novice Linux user and have only posted the minimal steps that worked for me. I hope someone finds this guide useful. 

STiNG

---

### Post by isaac wilson on 2010-07-07
This works great, but for me this somehow messed up Firefox's fonts, they are all jaggy, and I don't know how to fix it... I made a topic if anyone can help [http://ubuntuforums.org/showthread.php?p=9561750#post9561750](http://ubuntuforums.org/showthread.php?p=9561750#post9561750)

---

### Post by aticodejon on 2010-10-15
I posted a possible solution on the thread indicated above. It also happened to me on Chrome under Linux Mint.

By the way, I found no need to install kdebase-workspace-bin, just systemsettings.

---

