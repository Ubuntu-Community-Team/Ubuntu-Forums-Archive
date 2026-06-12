---
title: "VLC ctrl+H minimal view shortcut is not working"
date: 2009-08-10
forum: Multimedia Software
---

### Post by Wanas on 2009-08-10
I am using VLC on my windows xp, When I press ctrl+H it it change the view from the normal view to the minimal view, but on ubuntu this shortcut isnt working :s

I am using ubuntu 9.04 and the latest VLC from the ppa from the lauchpad [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

---

### Post by arky on 2009-08-10
Tried with VLC media player 1.0.1 Goldeneye on Karmic and the shortcut works.

---

### Post by Wanas on 2009-08-10
> **arky said:**
> Tried with VLC media player 1.0.1 Goldeneye on Karmic and the shortcut works.

Thanks arky 
I have the same vlc version but on jaunty not karmic 
is there a way to change this shortcut 
I tried the hotkeys option on the preferences but I didnt find this shortcut on it to change :(

---

### Post by Wanas on 2009-08-14
any other suggestions 
can I install the karmic VLC on jaunty ? if yes was the best way to do that ?

---

### Post by arky on 2009-08-15
sudo apt-get install vlc

---

### Post by Wanas on 2009-08-15
> **arky said:**
> sudo apt-get install vlc

But this will install the same VLC that I already have

---

### Post by arky on 2009-08-15
You can download the package for karmic manually.

[http://packages.ubuntu.com/search?keywords=vlc](http://packages.ubuntu.com/search?keywords=vlc)


Or add the karmic deb entries in /etc/apt/sources.list and override version for vlc by using apt-pinnning. 

[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

---

### Post by Wanas on 2009-08-15
> **arky said:**
> You can download the package for karmic manually.

[http://packages.ubuntu.com/search?keywords=vlc](http://packages.ubuntu.com/search?keywords=vlc)


Or add the karmic deb entries in /etc/apt/sources.list and override version for vlc by using apt-pinnning. 

[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

thanks for this helpful replay
I have read the wiki but things is different in unbuntu in ubuntu there is no /etc/apt/preferences 
I will add the source list of karmic but I want jaunty to be my default repository for updates and such unless I choose karmic for some packages, how to make this ?

---

### Post by arky on 2009-08-15
sudo apt-get install vlc=<target-version-number> would do the trick

---

### Post by Wanas on 2009-08-15
> **arky said:**
> sudo apt-get install vlc=<target-version-number> would do the trick

yeah but I want when I install applications from the synaptic manager will be from the jaunty repos as the default
I there a way to do this ?

---

### Post by andrew.46 on 2009-08-15
Hi Wanas,

> **Wanas said:**
> I am using VLC on my windows xp, When I press ctrl+H it it change the view from the normal view to the minimal view, but on ubuntu this shortcut isnt working :s

Seems a little odd, what key combination is given on the menu from: 

*View ---> Minimal View* ??

Andrew

---

### Post by Wanas on 2009-08-15
> **andrew.46 said:**
> Hi Wanas,



Seems a little odd, what key combination is given on the menu from: 

*View ---> Minimal View* ??

Andrew

It says Ctrl + H
I have recognized after that when the cursor is on the video screen (not on the menus or the status bar) the shortcut dont work
Is there a way to make the shortcut works always ?

---

### Post by arky on 2009-08-15
Don't about synaptics but your specify the version of package with apt-get 

sudo apt-get install vlc=1.0.1-1ubuntu1 

would install the karmic version of vlc on your machine.


[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-install](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-install)

---

### Post by arky on 2009-08-15
I don't think it will effect others as synapatics will install rest of packages from jaunty repos if you using the apt-get install vlc=<target version> trick.

---

### Post by mc4man on 2009-08-15
There would be no real advantage to using karmic's vlc vs korn's in jaunty. 
Same source, korn's may have a few additional things enabled, karmic would pull in a newer libx264 (67 from 05/02 vs 65 
(( you may also pull in a few other updates of no real consequence or harm

If you wanted a **slightly** better ppa version  than both korn and karmic use this ppa (using the more recent 1.0.2 and newer libx264

[https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

(if you switch ppa's that have same packages, disable old one first and while not 100% needed here it's better to totally remove vlc and it's core packages (libvlc2, libvlccore2, vlc-data, vlc-nox and any installed plugins

---

