---
title: "Nvidia 9600 no longer working with new monitor"
date: 2009-03-19
forum: Multimedia Software
---

### Post by ag93ds on 2009-03-19
EDIT: Issue resolved.

Hey all,

I'm running 8.04 and initially had an AOC monitor hooked up to my 9600 GSO card. Compiz and the Nvidia drivers were all working fine. I switched monitors to an Asus and now neither the drivers or compiz work. I followed [this]("http://ubuntuforums.org/showpost.php?p=5086971&postcount=6") guide, twice, and still nothing. No Nvidia logo display at start up, no compiz. Anyone have suggestions?

Thanks

-Matt

---

### Post by norwoods on 2009-03-19
i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by ag93ds on 2009-03-19
My system is 32-bit and I used 180.29. Will 180.37 work for sure?

---

### Post by norwoods on 2009-03-19
oops.  [www.avenard.org](www.avenard.org) is good for 8.10, not 8.04.  i think 180.37 is better than 180.29 on my system.  you  can try this to recover your 180.29 injstallation.  when you boot up, press the Esc key when grub says Press 'Esc' to enter the menu
then press the down arrow to highlight the menu entry ending with (recovery mode)
press Enter
you should get the Recovery Menu
repeat pressing the down arrow to highlight the menu entry:
root Drop to root shell prompt
type nvidia-xconfig
press Enter
wait for prompt
reboot

or try the menu Recovery Menu entry:
xfix Try to fix the X server
but this will probably get rid of the proprietary driver.

---

### Post by ag93ds on 2009-03-19
I followed your method and used 180.37 and still nothing. I can't remember how I got the card to work before with the old monitor but I remember it being quite simple and it worked fine. Any further suggestions?

---

### Post by norwoods on 2009-03-19
do you have a gui interface?
if so, open System--Administration--Hardware Drivers.
if there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

---

### Post by ag93ds on 2009-03-20
There's nothing in the Hardware Drivers window. I've uninstalled everything Nvidia and reset my xorg file so I'm in low graphics mode. I think I'm back to square 1 so how should a clean install of the drivers go?

---

### Post by ag93ds on 2009-03-20
Strike that. I got 180.29 to work after resetting everything and then selecting 'yes' for the last question during the install, though the write-up states not to. One problem fixed, two more created.

Now I can't access the nvidia-settings or adjust screen resolution from the System>Preferences menu. The errors I get are:
> 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

and

> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

respectively.

Suggestions?

---

### Post by norwoods on 2009-03-20
> **ag93ds said:**
> Strike that. I got 180.29 to work after resetting everything and then selecting 'yes' for the last question during the install, though the write-up states not to. One problem fixed, two more created.

Now I can't access the nvidia-settings or adjust screen resolution from the System>Preferences menu. The errors I get are:
and
respectively.
Suggestions?

does the nvidia logo flash when you are starting up?

have you tried Hardware Drivers again?

try gksu nvidia-settings in a terminal window.

when you boot up, press the Esc key when grub says Press 'Esc' to enter the menu
then press the down arrow to highlight the menu entry ending with (recovery mode)
press Enter
you should get the Recovery Menu
repeat pressing the down arrow to highlight the menu entry:
 root Drop to root shell prompt
run `nvidia-xconfig`
reboot

read the nvidia README that matches the driver 180.29

---

### Post by ag93ds on 2009-03-20
Nvidia logo displays, still nothing under hardware drivers, gksu nvidia-settings returns the same error as sudo nvidia-settings.

---

### Post by ag93ds on 2009-03-20
Ok, I ran this in terminal:

> 
sudo apt-get remove --purge xserver-xgl

and reset X and it all works flawlessly. Thanks again for your help.

---

