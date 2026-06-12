---
title: "k9copy crashs when I run it"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by dskyracer on 2008-03-30
After fooling around with k9 copy I must have done something in it's settings that makes it crash every time I try to open it now.. I've uninstalled it completely and reinstalled it to find it still crashes when I try to run it. I just tried to run it using the shell terminal and got some information as to what is happening.. any one who can decipher what the terminal says here? Is there something that I can do to correct this problem? Thanks ahead of time.. here is what the terminal displayed. 

:~$ k9copy
kbuildsycoca running...
DCOP Cleaning up dead connections.
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
KCrash: Application 'k9copy' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

---

### Post by xc3RnbFO8P on 2008-03-30
Install this in Synaptic Package Manager:

libmad0
libmad0-dev
python-pymad

k3b
k3b-i18n
libk3b2
libk3b2-extracodecs
libk3b2-mp3
libk3b-dev

dvd95
dvdauthor
liba52
liba52 dev
libdvdnav4
mkisofs
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
> sudo apt-get install w32codecs
> sudo apt-get install libdvdcss2
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by dskyracer on 2008-03-30
So Ringi if I end up doing all this will my k9copy work? Also I don't understand the quotes with the web urls in them.. here is a my list of what I have installed and what I don't have at present. 

libmad0...is installed
libmad0-dev.... not installed
python-pymad.... not installed

k3b...not installed
k3b-i18n...not installed and not sure why I should install this
libk3b2...installed
libk3b2-extracodecs...installed
libk3b2-mp3...installed
libk3b-dev..not installed and I  question need for dev files

dvd95... not installed
dvdauthor...installed
liba52...installed
liba52 dev...not installed and I question need for dev files
libdvdnav4...installed
mkisofs...not installed

I wonder why I need all this now to correct an apparent change in k9copy's program files.. which is causing it to crash now. k9copy was apparently working before I started to mess with it's program settings in it's tools menus. I just wonder how  by my doing what you list  will make my k9copy working again. Thanks for the info..

---

### Post by xc3RnbFO8P on 2008-03-30
mistake

---

### Post by xc3RnbFO8P on 2008-03-30
I am so wrong,
[https://answers.launchpad.net/ubuntu/+question/22646]("https://answers.launchpad.net/ubuntu/+question/22646")

---

### Post by dskyracer on 2008-04-01
Ok, another help site..It's great to find more help out there for Linux.but  it's not that big a deal for me to get k9copy going again because I can just do what I need to do using a laptop I have that has XP and  dvd shrink installed on it.. my  question now is ... I have a system which ran k9copy before.. I tried to adjust it's settings to reduce the size of the files it was creating.. and now when I try to open it it flashes on the screen then disappears.. I did a complete uninstall and then reinstall of the program which you would think would let me  start afresh with no memories of the other settings from the previous install. But for some strange reason the brand new install repeats the disappearing act of the one I got rid of. What would cause that? Is there some secret program cache in Gutsy or something which retains settings from previous programs? Again I am very pleased with what I have been able to do with Gutsy on my computer.. this is just a little glitch which I thought the many experts in Ubuntu Linux could help me address..one has tried..  if no one else can it's fine.. life goes on..I will too in the pursuit of Linux..  Peace

---

### Post by stchman on 2008-04-01
> **dskyracer said:**
> After fooling around with k9 copy I must have done something in it's settings that makes it crash every time I try to open it now.. I've uninstalled it completely and reinstalled it to find it still crashes when I try to run it. I just tried to run it using the shell terminal and got some information as to what is happening.. any one who can decipher what the terminal says here? Is there something that I can do to correct this problem? Thanks ahead of time.. here is what the terminal displayed. 

:~$ k9copy
kbuildsycoca running...
DCOP Cleaning up dead connections.
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
libGL.so: cannot open shared object file: No such file or directory
KCrash: Application 'k9copy' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

This is a more drastic measure.  Delete the .kde folder in your home.

```
rm -rf ~/.kde
```

This will reset k9copy (and all KDE apps installed on your system) back to default.

Remember the rm command is powerful and if misused you can mess things up terribly.

You could rename the .kde folder as well.

```
mv ~/.kde ~/.kde_old
```

---

### Post by dskyracer on 2008-04-03
Stchman you be the man!!! well at least in getting my k9copy back from the disappearing act it was into because of my changing it's settings.. I did the 2nd command you listed to rename it using the terminal and when I opened K9copy it was like you said.. back to it's default settings.. this solves my problem.. I will be ever thankful.. I need to bone up on how to configure the program better.. I also need to learn how to mark this thread solved and give you an official thank you.. I am so clueless here.. but with folks out there like you I will no doubt learn..

---

