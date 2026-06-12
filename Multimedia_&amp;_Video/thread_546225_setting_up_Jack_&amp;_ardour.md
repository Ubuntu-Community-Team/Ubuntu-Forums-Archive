---
title: "setting up Jack &amp; ardour ?"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by garyed on 2007-09-08
I can't get Ardour  to play back right.
Its all broken up even at  latency set at 1024 in ardour.
Audacity seems to work fine. 
The only thing is in Audacity I have to set " edit>preferences>audio IO"  to stereo in order to hear one track while recording another. 
Since Audacity doesn't use jack & ardour does I assume there's something not set up right in one of them.
I'n running Ubuntu studio with an old Turle Beach sound card.
Any ideas welcome.

---

### Post by Richard Kut on 2007-09-08
Jack needs a low-latency kernel. Ubuntu Studio provides such a kernel, as well as jackd and ardour pre-configured for you. You can access the Ubuntu Studio repositories by following the instructions from their web site. An excerpt is here:

> 
Ubuntu Studio Repo

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

### Post by Richard Kut on 2007-09-08
I just found this great tutorial that might also help:

[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

---

### Post by garyed on 2007-09-08
Thanks for the help,
I'm reading through the tutorial now. 
But I thought when I upgraded from Feisty to Ubuntu Studio that all the repos I needed should have been installed. 
Am I wrong about that?

---

### Post by garyed on 2007-09-08
I followed the tutorial but still the same problem.
I can record & playback fine in Audacity but not in Ardour.
I can honestl say  " I don't know JACK"

---

