---
title: "Stupid Video Card!!"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by pentium on 2006-10-12
I had my nvidia running fine on the legacy driver for two weeks and suddenly it can't even run GDM. I tried using the old drivers and even tried a reinstall of the legacy drivers but all I get is the welcoming of being dumped into command-line logon.
What is going on?

---

### Post by encompass on 2006-10-12
Did you have a kernel upgrade?
If so you have to reinstall the driver... it could be many things from there... if you have actually reinstalled the drivers.  I had some errors in the way the xorg.conf was setup.
For now, can you goto the nv driver and see if that helps.
```
sudo dpkg-reconfigure xserver-xorg
```
PRess enter for the default until you hit the driver and try the nv driver.

---

### Post by pentium on 2006-10-12
Well that got video back.
Now do I have to reinstall the legacy driver again?

---

### Post by encompass on 2006-10-12
If you want 3d support, then yes... you want to do that. Otherwise, don't worry about it and support the open source drivers.

---

### Post by pentium on 2006-10-12
is it normal for the system to no lnoger allow the download of the legacy Driver or pretty much anything required ti load the legacy driver? god ubuntu is annoying me right now.

edit

I got this when I tried the other driver:
```
$sudo aptitude install nvidia-glx nvidia-kernel-common linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  nvidia-glx-legacy
The following packages will be automatically REMOVED:
  nvidia-xconfig
The following NEW packages will be installed:
  nvidia-glx
The following packages will be REMOVED:
  nvidia-xconfig
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/4059kB of archives. After unpacking 12.3MB will be used.
The following packages have unmet dependencies:
  nvidia-glx-legacy: Conflicts: nvidia-glx but 1.0.8762+2.6.15.11-5 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
nvidia-glx [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?]

```

---

### Post by encompass on 2006-10-12
No idea why it would stop you know... Please don't get upset at ubuntu.  Nvidia is the one making the driver closed source so everyone has to install and setup the driver instead of having it built into the system like the nv driver is.  What post are you following for the nvidia driver install?

---

### Post by encompass on 2006-10-12
Weird it would cause you problems... try doing the install with synaptic.  it may fix your erros.  You could try uninstalling all the nvidia packages and then reinstalling them.
Looks like someone has been playing a little too deep. :)  Linux will let you go as deep into the system you want.

---

### Post by pentium on 2006-10-12
> What post are you following for the nvidia driver install?
there is a stickied thread on this page that talks about installing the legacy driver for nidia cards.
I used root terminal to install it and it worked flawlessly.
I also doubt it was me who trashed the package. the only real thing i did today was change my password and install bindings so I could see my mac (appletalk) on ubuntu. Brfore that,everything was fine.

---

### Post by encompass on 2006-10-12
Did you try it with synaptic?

---

### Post by pentium on 2006-10-12
How?

---

### Post by encompass on 2006-10-12
System...Administration...Synaptic Package manager...
Like this...
[[IMG]http://img208.imageshack.us/img208/8241/synapticlo3.th.gif[/IMG]](http://img208.imageshack.us/my.php?image=synapticlo3.gif)

---

### Post by pentium on 2006-10-12
it says that the legacy driver is already installed.
Should I remove it anyways?

---

### Post by pentium on 2006-10-12
I did it anyways.
I'm off to bed.

---

### Post by tseliot on 2006-10-12
try with:
```
sudo aptitude purge nvidia-glx-legacy nvidia-glx
```

```
sudo aptitude install nvidia-glx-legacy linux-386 nvidia-xconfig
```

and, if everything goes fine, type:
```
sudo nvidia-xconfig
```

log out and press CTRL+ALT+Backspace

---

### Post by pentium on 2006-10-12
That fixed it.
Thanks.

---

### Post by encompass on 2006-10-12
Thanks tseliot... you know your stuff... I am still learning.
Adn yippee you got it working!

---

### Post by pentium on 2006-10-12
AAAAARG!!!!
I boot the system up after a short time offline and once again the driver fails!
I didn't even touch the settings this time and it went nuts after a shutdown!
Now I gotta try again!

---

### Post by tseliot on 2006-10-13
> **pentium said:**
> AAAAARG!!!!
I boot the system up after a short time offline and once again the driver fails!
I didn't even touch the settings this time and it went nuts after a shutdown!
Now I gotta try again!

If you DON'T use a wireless card to connect to the Internet you can try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by pentium on 2006-10-13
ooooh.
That will do.

---

