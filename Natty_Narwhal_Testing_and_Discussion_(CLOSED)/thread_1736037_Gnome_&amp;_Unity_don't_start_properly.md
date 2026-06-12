---
title: "Gnome &amp; Unity don't start properly"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lerrup on 2011-04-22
I have just installed ubuntu-desktop (and dependencies) on my kubuntu install. 

Unfortunately, neither login properly - there is a the desktop but no side bar on unity, no panel on gnome.  

I suspect that something is missing, anyone have an idea what I can do to jump start it being installed?  I have tried reinstalling ubuntu-desktop, but that doesn't seem to have done anything.

---

### Post by 23dornot23d on 2011-04-22
I actually did this from a Fresh Natty Gnome UNITY install .......

This is what I did ....... [COLOR=Red]**[LINK]("https://sites.google.com/site/000menu/home/gnome---3")**[/COLOR] ..... hope it works for you too .......
( if not do a fresh install - but instead of the KDE CD use UNITY and try again ) 

and I have UNITY - CLASSIC - KDE - GNOME SHELL and Enlightenment ....... 
all working well together.

I also upgraded the kernel too to ......

keith@keith-Aspire-7730ZG:~$ uname -a
Linux keith-Aspire-7730ZG 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 15:45:56 UTC 2011 i686 i686 i386 GNU/Linux

Its your choice if you go this way though ...... but keep an eye on your processes and temperatures ..... 
in each Desktop ..... once I found things were stable on my system.

I did notice a problem on Firefox not so long back .... that was why I upgraded the kernel ..... but I was running a daily build kernel
then though which was the 2.6.39.999 ...... it could have been the problem or it could have been something else as I also
re-installed Firefox 4 from the web not from the repositories ...... but as I say all seems well now .....

This then became my main Workspace with a choice of Desktops ..... and now I am quite happy. ;)

_______________________________________________________

If you are just after UNITY and KDE working together

do a fresh UNITY install from CD and then after that do .......

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude install kdm  (this is optional - but it does give you the kdm login  menu)
sudo aptitude install kde-full
sudo aptitude safe-upgrade

_______________________

---

### Post by lerrup on 2011-04-23
I've sold it now by the bizarre step of installing lubuntu-desktop. Unity now works (but don't ask me why....)

---

