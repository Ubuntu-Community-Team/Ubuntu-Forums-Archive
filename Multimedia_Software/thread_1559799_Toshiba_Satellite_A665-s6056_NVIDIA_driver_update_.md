---
title: "Toshiba Satellite A665-s6056 NVIDIA driver update problem, Ubuntu 10.04"
date: 2010-08-24
forum: Multimedia Software
---

### Post by Hallic7 on 2010-08-24
Hi!

I have a very annoying problem with my laptop and the video driver.

After a fresh install of Ubuntu 10.04 the system tells me that I can activate the "NVIDIA accelerated graphics driver". I want to install this driver because I had some issues with the default video driver from Ubuntu using the Compiz desktop 3d-cube and other desktop effects. 

After I activate the driver, they download and seem to install fine, but I reboot my laptop and after the Ubuntu load screen everything  becomes black and I can't do anything but restart the machine from my power button. This makes my Ubuntu useless :(

My laptop is a Toshiba Satellite A665-s6056 with an NVIDIA GeForce 310M card.

Help me please!

---

### Post by Hallic7 on 2010-08-27
Any ideas???

---

### Post by Linuxforall on 2010-08-27
You need to add xswat ppa to get the latest nvidia drivers which support your card, the ones in Lucid dont'

In terminal, copy paste sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
sudo apt-get upgrade

Then go enable the driver via hardware applet and reboot.

---

### Post by Hallic7 on 2010-08-28
Hi! Thanks for your reply!

I tried the solution but after running the commands, download/install the driver and restart the laptop,the same happens, my screen goes black after the Ubuntu loading screen. Now I can't enter the login screen and Ubuntu.

Any idea on how to recover the system and after that, install the nvidia drivers?

Thanks!!!

---

### Post by Hallic7 on 2010-08-28
Hi! I managed to fix the blank screen problem, this is what I did...

- From grub menu on the machine start I pressed the "e" key and changed the text 'quiet splash' to 'nomodeset'.

- With this change I can access Ubuntu with low graphical settings, and disable the NVIDIA driver from System -> Administration -> Hardware Drivers. After a reboot I'm back to the start with no NVIDIA driver installed :(

I wonder if this is a bug with my graphics card, [**this**]("http://newyork.ubuntuforums.org/showthread.php?p=9505323") thread shows the same error with the same card model, but the thread is marked as solved with no real solution.

Any more ideas?

---

### Post by gababagonist on 2010-09-04
I have this same computer and same problem as well. I did some research on custom EDID lines in xorg.conf and whatnot, still no results. This is very frustrating..

---

### Post by Hallic7 on 2010-10-01
I made an upgrade to Ubuntu 10.10 RC and the problem is still there :(

---

