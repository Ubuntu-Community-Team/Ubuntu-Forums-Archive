---
title: "PVR-350 install issues...."
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by RichJacot on 2007-07-26
Hello All

I just installed a PVR-350 card in my Dapper system.  I'm only wanting to convert older home movies on VHS tape and on 8mm camcorder tapes to DVD.  Some of my tapes are many years old and I don't want to loose them.  At this point I do not need the tv out working as I'm not building a mythTV box.

I physically installed the card, booted up and started following this thread:

[https://help.ubuntu.com/community/Install_IVTV_Dapper]("https://help.ubuntu.com/community/Install_IVTV_Dapper")

It appears I need to do some upgrades to some packages and I can't seem to find a link on how to do it.

```
user@defiant:~$ DEBIAN_FRONTEND=gnome sudo apt-get install ivtv-source devscripts ivtv-utils ivtv-firmware mplayer
Password:
Reading package lists... Done
Building dependency tree... Done
ivtv-firmware is already the newest version.
mplayer is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ivtv-source: Depends: debhelper (>= 5.0.37) but 5.0.7ubuntu13 is to be installed
  ivtv-utils: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
              Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
              Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
E: Broken packages

```

Does anyone know of another HowTo for Dapper and the PVR350? or how I can resolve the above?

Any help is greatly appreciated!

---

### Post by dabl on 2007-07-26
Yep -- just happen to know of one -- this should help:

[http://kubuntuforums.net/forums/index.php?topic=3085164.0](http://kubuntuforums.net/forums/index.php?topic=3085164.0)

I'm running Feisty, but I don't think it's different for Dapper.

:popcorn:

---

### Post by RichJacot on 2007-07-26
Thank you, that looks like a much cleaner HowTo.

However, I still have the same issue with dependencies for:

```
ivtv-source: Depends: debhelper (>= 5.0.37) but 5.0.7ubuntu13 is to be installed
  ivtv-utils: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
              Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
              Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed

```

When I open Synaptic it appears that I am on the latest version.  Is there another repos. I need to add to my source list to see newer versions than what I'm currently seeing via Synaptic?

---

### Post by dabl on 2007-07-26
Hmmmm -- my ivtv stuff was the ONE item that wasn't a problem.  I'm running Ubuntu Feisty 64-bit.  I have the Medibuntu repository enabled, along with universe and multiverse.  You might want to take a look at your sources and see if it needs to be expanded.

---

### Post by RichJacot on 2007-07-26
I'm still having unmet dependencies:
  ivtv-source: Depends: debhelper (>= 5.0.37) but 5.0.7ubuntu13 is to be installed
  ivtv-utils: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.5 is to be installed
              Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
              Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
E: Broken packages


Here is my sud apt-get update.  I have added medibutu.  Universe and multiverse were already in my source list.

```
defiant:~$ sudo apt-get update
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release                                                                                                                                                            
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]                                                                                                            
Get:3 http://archive.ubuntu.com dapper-backports Release.gpg [191B]                        
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [191B]                          
Hit http://www.getautomatix.com dapper/main Packages                                                             
Get:5 http://dl.ivtvdriver.org edgy Release.gpg [189B]                                                           
Get:6 http://packages.medibuntu.org dapper Release.gpg [189B]                                      
Hit http://archive.canonical.com dapper-commercial Release                                         
Get:7 http://archive.ubuntu.com dapper-security Release.gpg [191B]                       
Get:8 http://archive.ubuntu.com dapper Release.gpg [189B]                                          
Hit http://archive.ubuntu.com dapper-backports Release                                             
Hit http://dl.ivtvdriver.org edgy Release                                                                       
Hit http://packages.medibuntu.org dapper Release                                           
Hit http://archive.canonical.com dapper-commercial/main Packages                         
Hit http://archive.ubuntu.com dapper-updates Release                                     
Hit http://archive.ubuntu.com dapper-security Release
Hit http://dl.ivtvdriver.org edgy/all Packages                                            
Ign http://packages.medibuntu.org dapper/free Packages               
Hit http://archive.ubuntu.com dapper Release   
Hit http://archive.ubuntu.com dapper-backports/main Packages        
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://packages.medibuntu.org dapper/non-free Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://packages.medibuntu.org dapper/free Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://packages.medibuntu.org dapper/non-free Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Fetched 196B in 1s (166B/s)
Reading package lists... Done

```

Anyone have any ideas of how I can get my dapper box past these dependencies?  :confused:

---

