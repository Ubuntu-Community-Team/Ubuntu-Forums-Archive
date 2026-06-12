---
title: "No sound after update to 10.10"
date: 2010-11-25
forum: Multimedia Software
---

### Post by Chrysalis700 on 2010-11-25
Hi,

I recently updated my laptop to Ubuntu 10.10 version. In the process of updating I lost all sound. 

Looking through my information I cannot see any sound card. I do have one. It's integrated on the motherboard. Worked fine under 10.04. Now not at all. 

Help?

-Chrysalis

---

### Post by lidex on 2010-11-27
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Chrysalis700 on 2010-11-28
Thanks Lidex for the commands. 

When I ran the commands it indicated that pulseaudio is not installed. 

Please find the output below:
[http://www.alsa-project.org/db/?f=6491f8592074190540472671708cb16467ad1ecf](http://www.alsa-project.org/db/?f=6491f8592074190540472671708cb16467ad1ecf)

Just tell me what I have to do. 

Optimally I would prefer alsa over pulseaudio. But anything is better than nothing.

---

### Post by lidex on 2010-11-28
> **Chrysalis700 said:**
> Thanks Lidex for the commands. 

When I ran the commands it indicated that pulseaudio is not installed. 

Please find the output below:
[http://www.alsa-project.org/db/?f=6491f8592074190540472671708cb16467ad1ecf](http://www.alsa-project.org/db/?f=6491f8592074190540472671708cb16467ad1ecf)

Just tell me what I have to do. 

Optimally I would prefer alsa over pulseaudio. But anything is better than nothing.

You get both with ubuntu.
Pulse appears to be installed and running but it can only recognize hardware that alsa sees and your alsa install is borked. An alsa re-install is in order but make sure your kernel is updated first:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot**

```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by Chrysalis700 on 2010-11-28
I followed all the instructions above to the letter. 

Still not getting any sound. Looking through the information, my sound card is still not being recognised. 

Please find an output below. 
[http://www.alsa-project.org/db/?f=ce4e83e6c459288c723238b51bbe4a8871f0e083](http://www.alsa-project.org/db/?f=ce4e83e6c459288c723238b51bbe4a8871f0e083)

---

### Post by anthony62490 on 2010-11-29
Hey, sorry this didn't work for you, but I'm just posting to say that it worked for me. Thanks!

---

### Post by Chrysalis700 on 2010-11-29
Ubuntu Maverick Meerkat uses version 2.6.35 of Linux Kernel. A lot of  users have solved their problems by upgrading to version 2.6.36. You  can do so by downloading the deb files and installing them from the  Ubuntu Kernel Mainline PPA: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")  Open the latest version that is available (rc8 is the latest in the  time of writing this, however only 64bit is available, if you have  32-bit, use rc7) and download the following files:


 linux-headers-VERSION_all.deb
 linux-headers-VERSION-generic_VERSION_amd64.deb
 linux-image-VERSION-generic_VERSION_amd64.deb


If you have 32bit, choose the ones that contain i386 instead of amd64 in the name.
 Install them one by one in the same order as listed above and reboot.
Note  that if that does not help and if you want to switch back to 2.6.35  kernel again, you can always remove 2.6.36 kernel from Synaptic Package  Manager (Alt+F2>gksu synaptic). Also note that you will not get  updates to 2.6.36 even if newer versions are out, so you should update  manually later if you find newer versions of 2.6.36 kernels.


This worked for me. 



-Chrysalis

---

### Post by ankara on 2010-11-30
hiya, can anyone shed any light on this for me, i've suddenly lost sound recently. i have gone back to an older kernel, upgraded to the latest 2.6.37 kernel, and run the alsa script posted above, this is my output
[http://www.alsa-project.org/db/?f=76ad29452d29503d78bf6990f7cf3728826ceed3](http://www.alsa-project.org/db/?f=76ad29452d29503d78bf6990f7cf3728826ceed3)

i have tested the speakers with another device, and when i boot, i get the *POP* of the driver being loaded. but when i am at the desktop, i get nothing.
it is not muted BTW :)
thanks

---

### Post by ankara on 2010-11-30
Ok, turns out that it was an obscure setting, only accessible in gnome-alsamixer, which had been changed somehow. i selected analog source, reverting it from digital. 
i have no idea how it got changed in the first place.
HTH

---

