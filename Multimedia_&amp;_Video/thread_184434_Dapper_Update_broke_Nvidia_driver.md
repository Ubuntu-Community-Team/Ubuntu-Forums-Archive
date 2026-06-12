---
title: "Dapper Update broke Nvidia driver"
date: 2006-05-29
forum: Multimedia &amp; Video
---

### Post by sbakker on 2006-05-29
I allowed dapper to update the nvidia-glx package today, and now I cannot get back into gnome.  When I start up my machine, I get:

> Version mismatch detected between the NVIDIA X driver and the NVIDIA GLX module.  X driver version: 1.0-8756; GLX module version: 1.0-8762.  Please try reinstalling the NVIDIA driver.

I have reinstalled the 8756 driver, but that didn't help.  I have now downloaded and installed the 8762 driver, but that didn't help either.  Anyone else have this problem or know of a solution.

Cheers.

---

### Post by gerard67 on 2006-05-30
Hello,
Exact same issue for me ? any solution ?

Mathieu

---

### Post by FredB on 2006-05-30
I have no such problem here. I updated all packages yesterday, and I am using the lastest version without problem. Did you upgrade also linux restricted drivers ?

---

### Post by tseliot on 2006-05-30
I guess they didn't upload nvidia-kernel-common version 8762.

Try this:

Remove the driver from the repos:
```
sudo apt-get --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common
```

Now install the driver from the repos:

```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

If that doesn't work then try this:
```
sudo nano -w /etc/X11/xorg.conf
```

and set the driver to "vesa" instead of "nvidia" in the Section Device of that file

CTRL+X to exit (save the file)

Then

```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

and wait until also the nvidia-kernel-common is updated

---

### Post by Horizon on 2006-05-30
Didn't work :( . Why is it that something like this always HAS to happen when i have a day off ](*,)  Bahumbug

This time i even purposely left it over night, and resisted the urge to press that damn-tempting red update button to avoid any nasty suprises by updating too early...*sigh* I guess i should have waited longer

---

### Post by tseliot on 2006-05-30
[QUOTE=Horizon]Didn't work :( . Why is it that something like this always HAS to happen when i have a day off ](*,)  Bahumbug

This time i even purposely left it over night, and resisted the urge to press that damn-tempting red update button to avoid any nasty suprises by updating too early...*sigh* I guess i should have waited longer[/QUOTE]
Doesn't this work?:

```
sudo nano -w /etc/X11/xorg.conf
```

and set the driver to "vesa" instead of "nvidia" in the Section Device of that file

CTRL+X to exit (save the file)

Then

```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

Then (ONLY AFTER doing what I wrote above) you can use my script to install the Nvidia driver:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by sbakker on 2006-05-30
FredB:  I have updated everything available.  I always do.  Is that bad?

tseliot:  Removing and reinstalling packages didn't work.  I changed my driver to vesa, and I am back into gnome now.  I don't have time to try your script right now, but I'll try after work today.  

Thanx for the help.

---

### Post by skorpio11 on 2006-05-30
Seems to happen with a kernel upgrade.  Change back to "nv" driver in xorg to get a working system.  Uninstall and reinstall nvidia-glx via synaptic.  Then change back to "nvidia" in xorg .... restart X ....  

work for me...

---

### Post by Horizon on 2006-05-30
[QUOTE=tseliot]Doesn't this work?:

```
sudo nano -w /etc/X11/xorg.conf
```

and set the driver to "vesa" instead of "nvidia" in the Section Device of that file

CTRL+X to exit (save the file)

Then

```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

Then (ONLY AFTER doing what I wrote above) you can use my script to install the Nvidia driver:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")[/QUOTE]

Nice one mate, it worked flawlessly. :-D

---

### Post by gerard67 on 2006-05-30
Vesa or nv trick works fine (it would have been very sad if not...)
I'll wait for an update of kernel-common.  
Horizon is right, I also fear the update time but I convince myself I've to keep pushing the button .... Good'ol J.Locke syndrom.

---

### Post by sbakker on 2006-05-30
Horizon,  which nvidia driver did you install, 8756 or 8762?  I'll try it when I get home.

---

### Post by Horizon on 2006-05-30
[QUOTE=sbakker]Horizon,  which nvidia driver did you install, 8756 or 8762?  I'll try it when I get home.[/QUOTE]
I had 8756 installed so i uninstalled it with the 8756 script (make sure you still have the installer and extracted folder in the same directory as the script) and then used the 8762 script to install it again. 

As a side note, afterwards i had to install nvidia-glx and reinstall libgl1-mesa to get compiz working.

---

### Post by Nailor on 2006-05-30
I filed a bug of this to launchpad: [https://launchpad.net/distros/ubuntu/+source/nvidia-kernel-common/+bug/47514](https://launchpad.net/distros/ubuntu/+source/nvidia-kernel-common/+bug/47514)

---

### Post by sbakker on 2006-05-30
tseliot, Horizon ... thanks, worked great ... I can play NWN again! ;)

---

