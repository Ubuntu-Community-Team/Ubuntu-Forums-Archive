---
title: "Difference between feisty and UbuntuStudio"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by js72 on 2007-05-11
Before i start to download this new release, i had to ask is there really difference between feisty and studio.  I have installed feisty and apt-get kernel low latency and ubuntustudio audio packages.

---

### Post by aysiu on 2007-05-11
Studio has programs in by default that are focused on multimedia and graphics. It also has different artwork.

---

### Post by tyler22 on 2007-05-11
Is the sutdio theme available anywhere? looks nice.

---

### Post by BoredOutOfMyMind on 2007-05-12
> **tyler22 said:**
> Is the sutdio theme available anywhere? looks nice.

Here's how to get access to our repo.

From a terminal run these 2 commands:
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Packages in our repo:

    * ardour - Digital audio workstation (graphical gtk2 interface) (This is Ardour 2)
    * ardour-i686 - Digital audio workstation (graphical gtk2 interface) [i686] (This is Ardour 2)
    * ubuntustudio-desktop - Makes up our base desktop install.
    * ubuntustudio-audio - Ubuntu Studio audio package
    * ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
    * ubuntustudio-graphics - Ubuntu Studio graphics package
    * ubuntustudio-video - Ubuntu Studio video package
    * ubuntustudio-artwork - UbuntuStudio themes and artwork
    * ubuntustudio-gdm-theme - Ubuntu Studio GDM theme
    * ubuntustudio-icon-theme - UbuntuStudio Icon theme
    * ubuntustudio-look - Ubuntustudio look (metapackage)
    * ubuntustudio-session-splashes - Ubuntu Studio Session splashes
    * ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
    * ubuntustudio-screensaver - Ubuntu Studio's floating logo screensaver
    * ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
    * ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
    * usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
    * wired - Audio creation free software for Linux

---

### Post by BoredOutOfMyMind on 2007-05-12
[Here is another way to install the Theme from Planet Ubuntu]("http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/")

---

### Post by HeavyAl on 2007-06-22
Hey, I see this post is a month old, but I used the package info above to try out some of the media stuff and ended up installing the optimized kernel for low latency audio - well, the kernel works great, it's awesome, but unfortunately wifi support doesn't appear to be wrapped into it so even though I can whip out some great tunes I can't surf the net with this kernel! Not cool.

I know I can just switch the kernel at boot time with grub, but I was wondering how you can actually get rid of this new kernel altogether if you wanted to - and do so safely. As it is, this was just a test and I'll be running Ubuntu Studio on another machine dedicated to gigging (I dj for the family at get togethers, weddings, anniversaries, crap like that), but I'd like to be able to revert my old system back to how it was before.

Can I just do apt-get remove ubuntustudio-audio?

---

