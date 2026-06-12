---
title: "Nvidia Drv - Issues - Removal - Failed Reinstall"
date: 2010-02-16
forum: Multimedia Software
---

### Post by sandman3838 on 2010-02-16
Hello

Originally I had some strange issues with my desktop.
- Menus failed to activate when selected with Mouse Pointer
- X or - in the upper right corner of any window or program was not selective.
 Things just weren't working right.

To fix this I removed the NVIDIA material from Synaptic.

Completely removed the following packages:
dmraid
jockey-common
jockey-gtk
nvidia-173-modaliases
nvidia-185-modaliases
nvidia-96-modaliases
nvidia-common

Then I went a step further and I used this info here for a total removal.

*************
I have tried these so far:

[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)
and
[http://ubuntuforums.org/showthread.php?t=1408498&highlight=Remove+Nvidia](http://ubuntuforums.org/showthread.php?t=1408498&highlight=Remove+Nvidia)

Code:

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove

Right now, if you were to open Synaptic and select "Not Installed" and search NVIDIA nothing is installed!  

Once removed!  and I'm using the safe mode generic drivers I have no desktop issues.  My mouse, menus and desktop work just fine.

Now I can install the NVIDI 185ver but my issues with the desktop and menus comes back.  However there seems to be some driver updates 190v and 195v, but I can't get them to install.

Right now I don't care what Driver I use just as long as there are no desktop issues.  

Oh my Video card is a Geforce GT8900 256mb

Any suggestions?

If you need more into or need a script run to get more info please just let me know.

Thank you for your time and help.

---

### Post by sandman3838 on 2010-02-17
Now that everything is removed what do you think about running this script?  Does it look OK?  Something missing?

sudo apt-get install nvidia-common nvidia-glx-190 nvidia-190-modaliases nvidia-190-kernel-source

---

### Post by sandman3838 on 2010-02-17
Sorry but there is something else that I needed to bring up....

So far I have zeroed in on the removal and reinstall of the NVIDIA drivers but from my looking around there are also some other files that might be creating issues?  For example some of the Xconfig files?  Are there some other file that I should be removing and  reinstalling?

---

### Post by sandman3838 on 2010-02-17
UPDATE!!

When ever I try to install the 190 ver of the Nvidia drivers I get this:

E: /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa10_i386.deb: subprocess new pre-installation script returned error exit status 2

What is this?


**SOLVED DUE TO SOME OTHER ISSUES I DID A RE-INSTALL OF UBUNTU!**

---

