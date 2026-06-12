---
title: "Nvidai driver 195 for Karmic and EN62000"
date: 2010-01-20
forum: Multimedia Software
---

### Post by Ron Porter on 2010-01-20
:o    I have recently installed an Asus EN6200LE in my system specifically to get the  tv out working. I originally installed the 185 Nvidia driver only to find it didn't support the card for tv out although it appeared to function in all other aspects. I have now tried to install the 195 driver only to discover that I cannot get it to load I keep getting "system errors: installed archives() failed". I have searched many web sites and bug reports to no avail can anybody please tell me what i am doing wrong when trying to install this driver. 
How do I set up 195 to run??

---

### Post by wojox on 2010-01-20
Try this HowTo [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) . You downloaded the driver from nvidia?

---

### Post by Ron Porter on 2010-01-20
I used the Synaptic Package manager to try and install the driver and also the Hardware Manager

---

### Post by Ron Porter on 2010-01-21
I have read the link given in the reply and wonder if it's relevant to my problem?? I am trying to install the Nvidia 195 driver into ubuntu 9l10 (Karmic) with Kernel 2.6.31-18-generic.
 I am sorry if this going to be long winded but I though a resume of what has happened may help.
I have tried to activate/install Nvidia-195 using Hardware drivers and EnvyNG both give me the option of activating nvidia drivers 96, 173, 185, 190 and 195, with 195 being the recommended driver. In both cases I get the message "systemerror: installArchives() failed"

I have tried to search my system for Nvidia-xconfig file but get the message that nvidia-xconfig can only be found in nvidia 96, 173, and 185.

I have tried using synaptic package manager to install all nvidia 195 drivers with the exception of the dev ones. Trying to install the glx package returns the following " E: /var/cache/apt/archives/nvidia-glx-195_195.30-0ubuntu1~karmic~nvidiavdpauppa5_i386.deb: subprocess new pre-installation script returned error exit status 2"

Can anyone help or give me any further guidance as to where I am going wrong.
I had assumed that this would be a straightforward operation as the required drivers appeared to be listed in Hardware drivers but obviously this is not the case, or maybe its just me.

---

### Post by w00d1 on 2010-01-21
I'm seeing the exact same problems. I'm really at a loss for what to do.

---

### Post by Sutur on 2010-01-21
Did any of you guys also upgrade to the 17 kernel?
I noticed my nvidia driver wouldn't build. I believe my problem stems from the fact that I'd forgotten I was downloading a PPA version of the driver.
I removed the PPA repository, updated/reloaded, and then installed 185 instead of 195. nvidia-xconfig just to put 'nvidia' as the driver again in xorg.conf.

Will post back what happens after a boot.

---

### Post by Sutur on 2010-01-21
Yep, that's fixed it. Here's how if you have the same issues, and you just need nvidia support in the short-term, troubleshoot the PPA's later:

```
#1 Remove any PPA repositories from your sources list.
```

```
#2 Do an sources update/reload with the PPA's omitted.
```

```
#3 Install nvidia glx & kernel version 185 (I noticed 195 glx wasn't available after I removed the PPA repositories).
```

```
#4 Issue the command nvidia-xconfig as root.
```

```
#5 And finally just reboot.
```

Hope this helps someone else...

---

### Post by Ron Porter on 2010-01-22
Thanks for the help I can get 185 running easily but it does not support my graphics card and I really need either 190 or 195 to allow me full use of the card.

Any further help would be much appreciated.

---

### Post by Ron Porter on 2010-01-22
:popcorn: Problem solved the link [http://www.ubuntugeek.com/how-to-install-nvidia-graphics-drivers-195-22-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-install-nvidia-graphics-drivers-195-22-in-ubuntu-karmicjauntyintrepidhardy.html) works provided you also carry out the comment posted by SAMD (note you have to correct each of the lines by using -- for the instructions instead of the symbols shown eg.

    sudo dpkg-divert -&#8211;remove -&#8211;rename -&#8211;package nvidia-glx-185 -&#8211;divert /usr/lib/nvidia/libGL.so.1.xlibmesa /usr/lib/libGL.so.1

to

sudo dpkg-divert --remove --rename --package nvidia-glx-185 --divert /usr/lib/nvidia/libGL.so.1.xlibmesa /usr/lib/libGL.so.1

---

