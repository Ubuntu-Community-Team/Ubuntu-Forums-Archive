---
title: "How to install latest nVidia driver"
date: 2008-06-03
forum: Multimedia Software
---

### Post by hurinth on 2008-06-03
WHat should I configure after installing the latest drivers 173.14.05?

I downloaded the file, and the installed succesfully the package, but after a log out to enter in graphics console, the resolution goes down to 640x480, and even though I can see the restricted drivers are in use (System>Administration>HW Drivers), I can't change the res. And even worse, when rebooting, the resolution shows up correctly, but no restricted drivers are loaded.

Ne idea please?

---

### Post by helino on 2008-06-03
You could use Envy-NG to install the latest driver. As soon as a new driver is released from Nvidia, your will find the new driver in the Update Manager as soon as it has been tested.

You find Envy-NG here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by papuaq on 2008-06-03
Stop GDM (
Code:
> sudo /etc/init.d/gdm stop
) and go in terminal line.

Backup your xorg.conf (if this does not work for you!)

Remove all nvidias:
Code:
> sudo apt-get remove --purge nvidia-glx nvidia-glx-new
Remove all nvidia drivers:
Code:
> sudo nvidia-installer --uninstall
In:
Code:
> sudo gedit /etc/apt/sources.list
edit more sources for beta/beta repositories:
look for this line:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted


after this line add:
# add hardy-proposed
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe

...and save file.

Do:
Code:
> sudo apt-get update
sudo apt-get upgrade
You should now have a lot of beta/beta fixtures, install them and reboot

Install new nvidia beta drivers:
Code:> sudo sh NVIDIA-Linux-x86-173.08-pkg1.run
Reboot again... 

Hope it will work for  you...
Or better check the last two post of the thread

[http://ubuntuforums.org/showthread.php?t=776802](http://ubuntuforums.org/showthread.php?t=776802)

---

### Post by Pjotr123 on 2008-06-03
Envy is in the Universe repository nowadays. So it has become even easier, to install the latest ATI or Nvidia video driver.

Here's how to install it:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2)

Greetz, Pjotr.

---

### Post by hurinth on 2008-06-03
Hello, thank you all for the help, the thing is my drivers are installed already, I know it because after installation the drivers were there and the nvidia settings manager recognized them.

I followed a guide from tselliot in envy's site where he listed this step: > sudo nano -w /etc/default/linux-restricted-modules-common, and I added the portion > DISABLED_MODULES="nv nvidia-new" since this step is supposed to make linux stop the loading of default drivers, which I believe its the problem here.
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2)

I use envy since the beginning and it has done all the dirty work pretty well. But this time is time to do it myself, most of all because the version of envy I have hasn't detected the new drivers. So now that the drivers are in my OS, how should I configure them to make them work????

---

### Post by Sadaiyappan on 2008-06-03
> **papuaq said:**
> Stop GDM (
Code:

) and go in terminal line.

Backup your xorg.conf (if this does not work for you!)

Remove all nvidias:
Code:

Remove all nvidia drivers:
Code:

In:
Code:

edit more sources for beta/beta repositories:
look for this line:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted


after this line add:
# add hardy-proposed
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed main restricted universe

...and save file.

Do:
Code:

You should now have a lot of beta/beta fixtures, install them and reboot

Install new nvidia beta drivers:
Code:
Reboot again... 

Hope it will work for  you...
Or better check the last two post of the thread

[http://ubuntuforums.org/showthread.php?t=776802](http://ubuntuforums.org/showthread.php?t=776802)

Yeah, this did the trick for me.  Before this my system was going into white screen of death or going into "low graphics mode."  Much thanks.:)

---

