---
title: "Installer crash"
date: 2011-03-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by thewolfman on 2011-03-17
Hi chaps,

I tried twice to install 11.04  but it got almost through the install and at the end it crashed saying the installer had a problem and it could not continue.

Anyone else had that?.

AMD Athlon(tm) II X3 425 Processor

GeForce 6150SE nForce 430

4 GB DDR3 RAM

thewolfman:D

---

### Post by r-senior on 2011-03-17
Did it crash, or ask you to insert a CDROM?

[https://bugs.launchpad.net/ubuntu/natty/+source/casper/+bug/727783]("https://bugs.launchpad.net/ubuntu/natty/+source/casper/+bug/727783")

I had to 'ln -s /cdrom /media/cdrom' in a terminal before kicking off the install.

---

### Post by WeeDavey on 2011-03-17
Are you including updates as you install ? I had to say NO to the include updates question before I had a successful install. Ran update manager after install.

---

### Post by VastOne on 2011-03-17
> **thewolfman said:**
> Hi chaps,

I tried twice to install 11.04  but it got almost through the install and at the end it crashed saying the installer had a problem and it could not continue.

Anyone else had that?.

AMD Athlon(tm) II X3 425 Processor

GeForce 6150SE nForce 430

4 GB DDR3 RAM

thewolfman:D

Yes... I have never been able to get a clean install

I had to install a clean Maverick and then update from it just to test.

Even though Natty Xubuntu installed just fine

Every other day I am wasting a DVD to try a new daily to see if it is resolved and with a stack of 15 or so, it is just a tad bit frustrating....More so because this has affected many but I have not seen much traction on it...

---

### Post by VastOne on 2011-03-17
> **WeeDavey said:**
> Are you including updates as you install ? I had to say NO to the include updates question before I had a successful install. Ran update manager after install.

I have tried all the solutions.. Yours, to unplug from the internet and try, even to unplug the power, but alas that failed too... :confused:

---

### Post by jerrylamos on 2011-03-17
Some people resort to using the alternate image which is text based, then loading in the rest of Natty.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

That gets you onto Natty hopefully without the Unity & Compiz & ubiquity problems.  

You could try the Natty Alpha 3 iso then update, or maybe that's what you tried already:

[http://www.ubuntu.com/testing/natty/alpha3](http://www.ubuntu.com/testing/natty/alpha3)

Early March there were a couple days where Natty Alpha 3 install worked.  I quick put it in my 4 test machines and have been doing updates since.

Achtung!  I've tried several daily builds since early March - install fails and screws up Grub on the hard drive even though install never even got to the "change" menu.  I thought Ubuntu wasn't supposed to change the hard drive unless you deliberately used partman....

Good luck, Jerry

---

### Post by VMC on 2011-03-17
Even todays[MAR17] livecd iso uses the older error prone ubiquity. 
After the livecd bootup, type ```
sudo apt-get update
```, then ```
sudo apt-get install ubiquity
```. It should update ubiquity to .27, the latest.

---

