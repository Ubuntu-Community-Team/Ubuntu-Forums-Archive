---
title: "rekonq/konqueror and 64-bit flash"
date: 2009-11-07
forum: Multimedia Software
---

### Post by anti-destin on 2009-11-07
i'm having some trouble getting 64-bit flash installed. i grabbed the tar.gz file and extracted the libflashplayer.so to ~/.netscape/plugins. flash didn't work even after i restarted my browser.

i then opened konqueror and tried to scan for the plugin, but pressing the 'scan for plugins' button does nothing.

any ideas?

---

### Post by anti-destin on 2009-11-10
ok, i've switched to arora, but i'm still having the same trouble. i've tried putting libflashplayer.so in various directories, e.g., ~/.mozilla/plugins, ~/.netscape/plugins, /usr/lib/browser/plugins, /usr/lib64/browser-plugins, etc. but arora won't load the plugin, even though it's located in the right directories.

am i doing something wrong?

---

### Post by anti-destin on 2009-11-11
i tried getting flash from the repository, but it looks like a lot of other packages are needed. is there a 64-bit version in the repository?

```
dreamz@ubuntu:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done                              
Building dependency tree                                   
Reading state information... Done                          
The following extra packages will be installed:            
  ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6
  lib32v4l-0 lib32z1 libatk1.0-0 libc6-i386 libgtk2.0-0 libgtk2.0-common  
  libv4l-0 nspluginwrapper                                                
Suggested packages:                                                       
  firefox xulrunner-1.9 firefox-3.0 msttcorefonts ttf-xfree86-nonfree xfs 
  lib32asound2-plugins librsvg2-common gvfs                               
Recommended packages:                                                     
  libasound2-plugins libatk1.0-data libgtk2.0-bin                         
The following NEW packages will be installed:                             
  flashplugin-installer ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1     
  lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libatk1.0-0 libc6-i386    
  libgtk2.0-0 libgtk2.0-common libv4l-0 nspluginwrapper                   
0 upgraded, 15 newly installed, 0 to remove and 2 not upgraded.           
Need to get 37.4MB of archives.                                           
After this operation, 173MB of additional disk space will be used.
```

---

### Post by benerivo on 2009-11-11
I think you will need to install the nspluginwrapper package before konq will be able to use the 64 flash plugin file.

---

### Post by anti-destin on 2009-11-12
thanks for the reply. why would i need nspluginwrapper if i'm on a 64-bit system and the plugin is 64-bit? i thought nspluginwrapper was for using the 32-bit version on a 64-bit system.

---

### Post by benerivo on 2009-11-12
You're right, that's the wrong package i was thinking of. I'm now going to say it's [konqueror-nsplugins]("http://packages.ubuntu.com/karmic/konqueror-nsplugins"). Also try putting it in /usr/lib/mozilla/plugins if it still fails.

---

### Post by anti-destin on 2009-11-12
i have konqueror-nsplugins installed, but flash doesn't work. a few questions.

1. i've created /usr/lib/mozilla/plugins by using 'sudo mkdir' and i copied libflashplayer.so to that directory, but the problem remains. do the permissions matter?
2. i'm not using konqueror, but arora. does that change anything?

---

### Post by benerivo on 2009-11-12
The permissions don't matter (all you need is read only permission, which you will have). The konqueror-nsplugins is only for konq, and won't affect arora. I'm assuming you have some sort of minimal installation, and that you have a package missing (which is the exact same problem i had once, and i'm sure i solved it by installing something, i just can't remember what). Are you also sure you downloaded the 64bit version?

---

### Post by anti-destin on 2009-11-12
i downloaded libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz from adobe.com.

and yes, i used the minimal installation image and i put kde-minimal on top. i may well be missing some important packages.

i'm assuming flash works on your system. is there any way to compare our systems and perhaps identify the packages required for flash?

---

### Post by benerivo on 2009-11-12
Unfortunately i'm no longer using the same system. The only thing i can suggest is trying to install firefox and gnash, and check what dependencies it wants to bring in.

---

### Post by anti-destin on 2009-11-12
thanks, benerivo.

here's the output:

```
dreamz@ubuntu:~$ sudo aptitude install gnash
[sudo] password for dreamz:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  gnash gnash-common{a} gstreamer0.10-alsa{a} gstreamer0.10-plugins-base{a}
  libatk1.0-0{a} libboost-date-time1.38.0{a} libboost-thread1.38.0{a}
  libcdparanoia0{a} libgstreamer-plugins-base0.10-0{a}
  libgstreamer0.10-0{a} libgtk2.0-0{a} libgtk2.0-common{a}
  libvisual-0.4-0{a}
The following packages are RECOMMENDED but will NOT be installed:
  gvfs libatk1.0-data libgtk2.0-bin libvisual-0.4-plugins
0 packages upgraded, 13 newly installed, 0 to remove and 14 not upgraded.
Need to get 7,216kB of archives. After unpacking 45.5MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
dreamz@ubuntu:~$ sudo aptitude install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  firefox firefox-3.5{a} firefox-3.5-branding{a} libatk1.0-0{a}
  libgtk2.0-0{a} libgtk2.0-common{a} libidl0{a} libstartup-notification0{a}
  libxcb-atom1{a} libxcb-aux0{a} libxcb-event1{a} xulrunner-1.9.1{a}
The following packages are RECOMMENDED but will NOT be installed:
  libatk1.0-data libcanberra0 libgtk2.0-bin ubufox
0 packages upgraded, 12 newly installed, 0 to remove and 14 not upgraded.
Need to get 13.6MB of archives. After unpacking 60.5MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
```

does anything stand out?

---

### Post by benerivo on 2009-11-12
Not really, but I do know flash will require gtk2 to be installed. If you have no gtk2 libraries on your kde minimal installation then i don't think flash will run in a web browser. I'm scraping the bottom of the barrel here, but try installing libgtk2.0.

---

### Post by Yellow Pasque on 2009-11-12
Try starting konq from the terminal. Do the "scan for plugins" thing again. See if konq outputs any errors.

---

### Post by anti-destin on 2009-11-12
success! i just did 'sudo aptitude install libgtk2.0-0', grabbed that and a couple of other packages, and now flash works in arora and konqueror. 64-bit flash, only 28mb for the libs and 9mb for the flash plugin itself, and no messing with symlinks or system directories. much better than the huge 173mb 32-bit package i had before.

i wish i had known earlier that flash required libgtk2.0, but i'm glad everything works now. i am marking this thread as [solved].

thanks for all the help, benerivo. and thanks for the input, temüjin.

---

