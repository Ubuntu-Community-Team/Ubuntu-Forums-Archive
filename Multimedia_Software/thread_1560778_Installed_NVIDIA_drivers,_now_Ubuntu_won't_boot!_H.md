---
title: "Installed NVIDIA drivers, now Ubuntu won't boot! HELP!"
date: 2010-08-25
forum: Multimedia Software
---

### Post by squidpotion on 2010-08-25
A little background info. - I was fiddling with Ubuntu to get my  graphics card to work (NVIDIA GeForce 8200), trying to enable  compositing for Docky and Compiz, and I was having a REALLY hard time  trying to get it to work. I tried installing from Synaptic, from the  terminal, from outside the GUI... Everytime I installed the drivers, the  resolution would be HUGE and I couldn't change it from Ubuntu or from  NVIDIA. If I uninstalled everything NVIDIA and restarted, it would run  in low graphics mode and the resolution would be back to normal, but  Docky would be kind of laggy. The desktop effects part of Appearance  would be grayed out too, so I couldn't select it at all. 

So I tried installing the drivers again (ver. 256.44) and restarted, and  now Ubuntu freezes at the splash screen. If I press alt+ctrl+del, it  restarts, but that's it. I tried alt+ctrl+F1, to maybe start the GUI,  but that doesn't work either. 

Can someone PLEASSSEEE help me fix this mess? Much thanks in advance!

---

### Post by ratcheer on 2010-08-25
Most of us have gotten into that situation several times. Boot to the grub prompt (hold the shift key) and select recovery mode startup. It will give you a menu of choices. If you select root login with network support (something like that), you should be able to fix it.

My suggestion is to add x-swat ppa to your software sources, update your package manager, and use jockey to install nvidia-current (recommended) driver. If nvidia is already installed, remove it and reboot again, first. This is the only way I could get the latest nvidia drivers to install cleanly in Lucid and Maverick.

Tim

---

### Post by realzippy on 2010-08-25
+1 for xswat ppa

If you can boot recovery mode,use this to uninstall the nvidia driver,then reboot.

To add xswat driver,run:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
```
```
sudo apt-get update
```

The available"current driver" in Administration/HardwareDrivers then will be from xswat.Install it (nvidia-current),reboot.
Probably you will have the old resolution problem again,but we might fix it then;most important now is to get a driver running somehow.

---

### Post by squidpotion on 2010-08-25
Ok. I booted to recovery mode, tried uninstalling the driver and when I did I got this:

You appear to be running runlevel1; this may cause problems. For example: some distributions that use devfs do not run the devfs daemon in runlevel 1, making it difficult for 'nvidia-installer' to correctly setup the kernel module configuration files. It is recommended that you quit installation now and switch to runlevel 3 ('telnit 3') before installing.

The first time I got that, I just said "eff it" and uninstalled anyway and then rebooted. Still stuck at the splash screen. Rebooted again, and then tried purging nvidia by entering 

```
sudo apt-get remove --purge nvidia*
```Got some text like it was working, which ended in "could not find file 'nvidia*'. Hmph.

I also don't have "Hardware Drivers" under Administration, for whatever reason. I remember looking for that when I was trying to get it working right the first time.

Anything else I can do?

---

### Post by ratcheer on 2010-08-25
Is it too late for you to reinstall Ubuntu? If jockey (Hardware Drivers applet) is missing, you have a bit of a mess. You could possibly reinstall it, but I would be wondering what else is missing?

Tim

---

### Post by realzippy on 2010-08-25
I don't understand....can you boot to Desktop (low graphics mode) or can't you???????

If you can,what happens when you type in terminal:

```
jockey-gtk
```

---

### Post by squidpotion on 2010-08-25
No, I still can't boot to desktop/low graphics mode. It still freezes at the splash screen. 

I think I might have some of you confused, I meant that when I COULD boot up and was looking around for work-arounds for the driver, I never found Hardware Drivers under administration. I figured maybe it was under something else and that I was reading something for an older version of Ubuntu and maybe they changed it in Lucid.

---

### Post by realzippy on 2010-08-25
O.k.
So boot recovery mode,drop to root shell and delete the xorg.conf file,
so it should boot in low graphics mode afterwards.

At root shell type:

```
rm /etc/X11/xorg.conf
```

---

### Post by squidpotion on 2010-08-26
> **realzippy said:**
> O.k.
So boot recovery mode,drop to root shell and delete the xorg.conf file,
so it should boot in low graphics mode afterwards.

At root shell type:

```
rm /etc/X11/xorg.conf
```

Tried that. Got "rm: cannot remove '/etc/X11/xorg.conf': No such file or directory.

---

### Post by Linuxforall on 2010-08-26
> **squidpotion said:**
> Tried that. Got "rm: cannot remove '/etc/X11/xorg.conf': No such file or directory.

add sudo

---

### Post by squidpotion on 2010-08-26
> **Linuxforall said:**
> add sudo

Tried that too. Got the same thing.

---

### Post by realzippy on 2010-08-26
*/etc/X11/xorg.conf': No such file or directory*


Since he is at **root** shell,*sudo* is not necessary.Xorg.conf does not exist,what is strange after installing the nvidia-driver.   ;-)

     ------------------------------------------------------

What happens when running

```
nvidia-xconfig
```

instead of removing non-existing xorg.conf?

---

### Post by squidpotion on 2010-08-26
> **realzippy said:**
> */etc/X11/xorg.conf': No such file or directory*


Since he is at **root** shell,*sudo* is not necessary.Xorg.conf does not exist,what is strange after installing the nvidia-driver.   ;-)

     ------------------------------------------------------

What happens when running

```
nvidia-xconfig
```instead of removing non-existing xorg.conf?
 
"command not found"

---

### Post by realzippy on 2010-08-26
Bad.That means your nvidia driver installation failed.
Anyway the nouveau driver should run instead *or* have you formerly blacklisted it to try a manually nvidia-driver install?

---

### Post by squidpotion on 2010-08-26
> **realzippy said:**
> Bad.That means your nvidia driver installation failed.
Anyway the nouveau driver should run instead *or* have you formerly blacklisted it to try a manually nvidia-driver install?

Pretty sure I blacklisted it during a manual install.

---

### Post by realzippy on 2010-08-27
So I suggest to unblacklist/reinstall nouveau to have a running Desktop;
then creating a nvidia error log file which to post here...of course this could be done also from
the shell -if you are familiar with it...  !?

---

### Post by Linuxforall on 2010-08-27
If installing via xswat ppa, you don't need to do anything like blackisting, editing grub etc. That would create huge list of issues. Just enable the ppa, then install drivers via hardware drivers and reboot.

---

### Post by squidpotion on 2010-08-27
> **realzippy said:**
> So I suggest to unblacklist/reinstall nouveau to have a running Desktop;
then creating a nvidia error log file which to post here...of course this could be done also from
the shell -if you are familiar with it...  !?
 
Hah, yea I'm not all that familiar with how to do all that, so how would I go about doing it?

---

### Post by realzippy on 2010-08-27
> **squidpotion said:**
> Hah, yea I'm not all that familiar with how to do all that, so how would I go about doing it?


Run this:

```
sudo nvidia-settings --uninstall
      sudo apt-get remove --purge nvidia*
      sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
      sudo apt-get install nvidia-common
      sudo apt-get install xserver-xorg-video-nouveau
      sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
      sudo dpkg-reconfigure xserver-xorg
      sudo reboot
```



Some commands might be obsolete;but don't know your exactly system status....
and if on root shell,you do not need the "sudo"...
from:
[https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching)

---

### Post by squidpotion on 2010-08-27
> **realzippy said:**
> Run this:

```
sudo nvidia-settings --uninstall
      sudo apt-get remove --purge nvidia*
      sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
      sudo apt-get install nvidia-common
      sudo apt-get install xserver-xorg-video-nouveau
      sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
      sudo dpkg-reconfigure xserver-xorg
      sudo reboot
```

Some commands might be obsolete;but don't know your exactly system status....
and if on root shell,you do not need the "sudo"...
from:
[https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching)

Everything went smoothly until I got to

```
dpkg-reconfigure xserver-xorg
```

then it said "xserver-xorg is broken or not fully installed.

---

### Post by Linuxforall on 2010-08-27
> **realzippy said:**
> */etc/X11/xorg.conf': No such file or directory*


Since he is at **root** shell,*sudo* is not necessary.Xorg.conf does not exist,what is strange after installing the nvidia-driver.   ;-)

     ------------------------------------------------------

What happens when running

```
nvidia-xconfig
```

instead of removing non-existing xorg.conf?

Nope not strange at all, new nvidia-drivers installed via Ubuntu Hardware applet doesnt' create xorg.cong, for that you need to type nvidia-config in root.

---

### Post by realzippy on 2010-08-27
So try:

```
sudo apt-get update
      sudo apt-get install --reinstall xserver-xorg
```




@ linuxforall:

*"Nope not strange at all, new nvidia-drivers installed via Ubuntu Hardware applet doesnt' create xorg.cong"*

    That's right.Does not create xorg.cong,it creates xorg.conf ;-) ;automatically,no matter if jockey or manually (manually you are asked if it should create one).The nvidia driver won't run without xorg.conf file.
    Somehow I have got the idea that you do not exactly know what you are talking/posting about.....???

---

### Post by squidpotion on 2010-08-27
> **realzippy said:**
> So try:

```
sudo apt-get update
      sudo apt-get install --reinstall xserver-xorg
```

When I tried to reinstall xserver-xorg, it says "E: Unable to fetch some archives, maybe run apt-get update or try with --fix-m(screen cut off the letter)sing?" So I ran update and it said "E: Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by realzippy on 2010-08-27
Try:

```
sudo apt-get update
sudo apt-get install xserver-xorg --fix-missing
sudo dpkg-reconfigure xserver-xorg
      sudo reboot
```


When running *sudo apt-get update*,do any errors occur?

---

### Post by squidpotion on 2010-08-27
> **realzippy said:**
> Try:

```
sudo apt-get update
sudo apt-get install xserver-xorg --fix-missing
sudo dpkg-reconfigure xserver-xorg
      sudo reboot
```When running *sudo apt-get update*,do any errors occur?

```
run apt-get update
``` I get this long, speeding line of text. The last couple of lines before it says "E: Some index files failed to download, they have been ignored, or old ones used instead", are along the lines of "W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz) Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)"

```
sudo apt-get install xserver-xorg --fix-missing
``` I got a long line of "failed to fetch, etc."

```
dpkg-reconfigure xserver-xorg
``` I get "xserver-xorg is broken or not fully installed."

---

### Post by realzippy on 2010-08-27
Try:

```
apt-get remove --purge xserver-xorg
```

```
apt-get install --reinstall xserver-xorg
```


sorry,I will not be online today anymore..tomorrow again.

---

### Post by goldenbrown on 2010-08-27
> **squidpotion said:**
> Ok. I booted to recovery mode, tried uninstalling the driver and when I did I got this:

You appear to be running runlevel1; this may cause problems. For example: some distributions that use devfs do not run the devfs daemon in runlevel 1, making it difficult for 'nvidia-installer' to correctly setup the kernel module configuration files. It is recommended that you quit installation now and switch to runlevel 3 ('telnit 3') before installing.

The first time I got that, I just said "eff it" and uninstalled anyway and then rebooted. Still stuck at the splash screen. Rebooted again, and then tried purging nvidia by entering 

```
sudo apt-get remove --purge nvidia*
```Got some text like it was working, which ended in "could not find file 'nvidia*'. Hmph.

I also don't have "Hardware Drivers" under Administration, for whatever reason. I remember looking for that when I was trying to get it working right the first time.

Anything else I can do?

Try
sudo apt-get install gdm

---

### Post by squidpotion on 2010-08-27
Nope, neither of those worked either.

---

### Post by realzippy on 2010-08-28
[I]I got a long line of "failed to fetch, etc.
W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
[/I]
So it might be interesting to watch your **/etc/apt/sources.list**...
Can you copy it on root shell to a USBstick and post it here?
Or you could start UbuntuLiveCD and copy that file from your broken filesystem (do not confuse it with the LiveCD's sources list..)?


Edit:
There is a bug around:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

---

### Post by squidpotion on 2010-08-28
> **realzippy said:**
> [I]I got a long line of "failed to fetch, etc.
W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
[/I]
So it might be interesting to watch your **/etc/apt/sources.list**...
Can you copy it on root shell to a USBstick and post it here?
Or you could start UbuntuLiveCD and copy that file from your broken filesystem (do not confuse it with the LiveCD's sources list..)?


Edit:
There is a bug around:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

How would I go about copying it and getting it on USB? And I only have a LiveCD or Karmic.

That bug sounds a lot like what I have, especially since I upgraded from Karmic to Lucid.

---

### Post by realzippy on 2010-08-28
On root shell it would be:

```
cp /etc/apt/sources.list /media/"YOUR USBSTICK"
```


Replace YOUR USBSTICK with the name of your USB stick,use quotes
if the name has a blank character.


```
ls /media
```

lists the devices in /media.....

Yep,bug sounds similar.If your sources list is not messed up,I have to admit that I am running out of ideas....we will see.

BTW,you use a router?

---

