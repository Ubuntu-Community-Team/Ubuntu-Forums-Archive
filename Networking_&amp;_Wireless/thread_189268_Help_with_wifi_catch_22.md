---
title: "Help with wifi catch 22"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by infinitelink on 2006-06-05
I'm re-installing both Windows XP and Ubuntu on my laptop. I used automatrix to install ndisgtk before, but right now I'm using a city wifi connection to access the internet, nad when I do a complete re-install I won't be abe to access the internet using Ubuntu.

I tried downloading the .tar.gz of ndisgtk beforehand, but then discovered something I read about years ago: DEPENDENCY HELL. Seriously, Linux needs certain standards (maybe more than the LSB) and the ability to have everything a program will need in something like a .exe (but Linux version), that way, it can just install everything, and check to see what's already on the system, and also register thing with package managers. 

Enough ranting, though, does anyone know how I can install this manually? I also don't know about extracting these files manually. Isn't .deb the equivalent (or similar) to the Windows .exe (or .msi) installers in Ubuntu?

Is there one for this program with all the packages ready?

Any help is much appreciated and thank you for your time. I'm almost ready to go back exclusively to Windows when I figured out how bad dependency hell, packages for each other packages upon package, is, not to mention how much HD space it takes. I don't want to, though, I'm still trying to stick with it, so let's do this. : )

By the way I run a Dell Inspiron XPS with a Broadcom 1350 WLAN Mini-PCI Card. I know Broadcom has been hell in neglecting Linux communities, but I don't really care, I just want to not break my ability to go online with my computer while using linux once I do a fresh install of Ubuntu. (I don't blame them, actually, for the disorganization and unknowns with what is actually in the system and the speed it will change etc.) Again, thanks.


J

---

### Post by yatt on 2006-06-06
Independant debs would get extremely large, and would be quite redundant. Internet and harddrive speeds are much too slow for independant debs. Think, all those dependancies would be downloaded over and over (some of the more common being downloaded with nearly all packages), and then they have to be rewritten over and over. It would make installing packages slower for Ubuntu than installing the package on Gentoo.

---

### Post by az on 2006-06-06
Well, install using the Desktop cd (the live cd) and once you are installed and at the desktop, pop the cd back into the drive - there is a small repos with a bunch of packages there to avoid such a catch-22.  While ndisgtk is not there, ndiswrapper-utils is.  Just add that repos to your list (follow the dialogue box instructions) and install it using the package manager.

build-essential is also there, so if you want to install ndisgtk, you will be able to build it.

If you installed using the alternate cd, all those packages are already part of the package manager's repos.

---

### Post by infinitelink on 2006-06-07
Thanks man I appreciate it! I am using the alternate, since I don't want to kill the Windows install. Adios.

---

