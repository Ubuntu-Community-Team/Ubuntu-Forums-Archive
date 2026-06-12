---
title: "Getting my nvidia driver working on Hardy"
date: 2008-10-07
forum: Multimedia Software
---

### Post by rplogue on 2008-10-07
Hello I am using Ubuntu hardy. I am trying to get my nvidia driver for my graphics card and I have no luck. 

my card is 

XFX GeForce 9500 GT 256MB PCI-E Graphics Card

In the system -> Administration -> Hardware Drivers there is nothing listed.

All the tutorials of sticky threads that I can find refer to older versions of Ubuntu or older graphics card.

I am very sorry if this is in the wrong place.

Any help would be greatly appreciated.

Thanks.

---

### Post by klikklak on 2008-10-07
start synaptic->install envyng .. then run it.  It'll install the binary drivers for you.

---

### Post by stromdal on 2008-10-07
This post([http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)) might also be helpful.

Regards
/stromdal

---

### Post by philidox on 2008-10-07
EnvyNG is the bomb!  Use it, use it, use it.  It will make your life a lot easier.  I ignored the use of envy for a year and just download the nvidia drivers from the website but then I tried envy and wanted to smack myself for not doing it sooner.

---

### Post by Teabicky on 2008-11-24
Have just brought a similar card "GeForce 9500 GT 256MB PCI-E Graphics Card" and was thinking of taking it back when I discovered this thread.  

I used EnvyNG and it works fine.  

\\:D/\\:D/\\:D/I did have to run a manual install of the driver "at my own risk" and now it works fine.

To do this install Envyng and then type the following command:

> envyng -t

Then select option 5 to manually install the driver.

Easy Peasy!!!  	:)

---

