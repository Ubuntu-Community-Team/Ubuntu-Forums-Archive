---
title: "Can't Change Screen Resolution!"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by gwoodard on 2007-02-27
I got Ubuntu installed on a Nvidia Geforce 2 (AGP) can anyone help?

---

### Post by mr_mop on 2007-02-27
What is the contents of your /etc/X11/xorg.conf file?

---

### Post by gwoodard on 2007-02-27
how do i get into that?

---

### Post by domestic on 2007-02-27
sudo gedit /etc/X11/xorg.conf

or whatever editor you like

---

### Post by gwoodard on 2007-02-28
okay here is the video card

Section "Device"
	Identifier	"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Driver		"nv"
	BusID		"PCI:2:0:0"

---

### Post by Iceni on 2007-02-28
Did you install the legacy driver? If not, that could probably help. I experienced the exact same problem, but all I had to do was go into nvidia settings ( sudo nvidia-settings ), set everything up the way I wanted and apply ( do NOT save to X configuration file, as this can break X ), and everything went back to normal. 

You might want to look into installing a driver, if you haven't already.

---

### Post by gwoodard on 2007-02-28
there is a problem with the legacy driver issue, when i select it (add/remove programs) it says my hardware is not compatible with it

---

### Post by hise0001 on 2007-02-28
Seems like I recall a similar problem after my initial Edgy (6.10) install.

Read all of the Nivida Binary driver Howto ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)), there's alot of good information in there.

The part that seemed to do the trick for me was stepping through dpkg-reconfigure as described in the troubleshooting section of the nvidia howto... the snipit is quoted below.

> 
#

You may need to activate the "kernel framebuffer device interface" in X server. Copy/paste the below command into the terminal. The terminal will then start stepping you through each configuration setting. Most of the settings can be left at their defaults by pressing the ENTER button, but when you get to "Select the desired X server driver" (question 2), make sure to select "nvidia" and NOT "nv". At question 7 ("Activate kernel framebuffer device interface?") select "yes". Finish the rest of the questions (the rest of the settings can be left at their defaults) and then restart X server (or just restart your computer). If, when you reboot, you can't see the login screen, but instead get a message saying "X server failed to start (etc. etc.)", you will start in text mode (white text on black background) and it will ask you to login. After logging you will still be in text mode. Retype the same command below (make sure to write it down!) and then the configuration sequence will start again. This time at the "Activate kernel framebuffer device interface?") select "no" then restart your computer and your login screen will be restored.

sudo dpkg-reconfigure xserver-xorg 




Good Luck.

--hise

---

