---
title: "[SOLVED] video help"
date: 2008-07-22
forum: Multimedia Software
---

### Post by mikedemario17 on 2008-07-22
im running Ubuntu 8.04 and when i went to watch the videos off my psp ...these errors popped up...
it said they arnt installed....what do i do?

MPEG-4 AAC decoder
MPEG-4 Video decoder

---

### Post by cozmicharlie on 2008-07-22
You need to install the codecs.  I assume you mean you want to play them from your psp through your computer (if that is not correct then this won't help).  All you need is ffmpeg and faac but you should install all the codecs so you can play dvd's or other types of video files also.  Follow these steps.

If you have not already done so then enable the medibuntu repository.  If you are using hardy the commands are as follows:

[LIST=1]
[*]Open a terminal.
[*]At the prompt, copy and paste the following:
[*]```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
[*]Then add the key and update - copy and paste the following in the terminal:
[*]```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
[*]The easiest way to get the codecs is to install the Ubuntu Restricted Extras.  ```
sudo apt-get install ubuntu-restricted-extras.
```
[/LIST]

Once you are finished you want to be sure that the following are installed.  You can check these in Synaptic (system>administration>synaptic
ffmpeg
faad
faac
libdvdcss2
libdvdnav
libdvdread3
w32 codecs 

I believe these should be installed when you install the ubuntu restricted extras but if not go ahead and install using Synaptic. 

This will help if you get stuck.
[HTML]https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3[/HTML]

If you are still having problems post back.

---

### Post by mikedemario17 on 2008-07-23
this happones all the time what do i do? -----> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

------------this is what i did and it poped up----------
mike@mike-desktop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
mike@mike-desktop:~$

---

### Post by overdrank on 2008-07-23
> **mikedemario17 said:**
> this happones all the time what do i do? -----> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

------------this is what i did and it poped up----------
mike@mike-desktop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
mike@mike-desktop:~$

Hi and have you run the command ```
sudo dpkg --configure -a
```

---

### Post by cozmicharlie on 2008-07-23
The message basically means you have a broken package somewhere.  As overdrank said - run the command in the terminal - that should fix it.  
$sudo dpkg --configure -a

---

### Post by mikedemario17 on 2008-07-23
i think it worked thanks....

---

### Post by cozmicharlie on 2008-07-23
Great - please mark the thread as solved.

---

### Post by overdrank on 2008-07-23
> **cozmicharlie said:**
> Great - please mark the thread as solved.

Glad you got it solved!!
I've marked it as solved for you - you can do the same by clicking thread tools at the top of the page and choosing "Mark Thread as Solved"

Also see [https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads](https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads) for graphical instructions.

---

### Post by mikedemario17 on 2008-07-24
yepp it works

---

