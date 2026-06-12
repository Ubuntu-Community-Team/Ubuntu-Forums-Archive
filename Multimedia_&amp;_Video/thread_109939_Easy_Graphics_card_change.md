---
title: "Easy Graphics card change?"
date: 2005-12-29
forum: Multimedia &amp; Video
---

### Post by ge-force on 2005-12-29
Being a complete newbie to Linux and Ubuntu I am just trying to find my way around the system.  Is it me or are the help files still being updated and unavailable from the 'help' in Ubuntu?  Anyway is there a way to change the hardware, in this case the graphics card, from the one that was present when the OS was installed to a completely different one.  I was under the impression that there was plug and Play support now for Linux, is that not the case?  I have fitted the new Graphics card and 'installed' the Nvidia drivers using the method at [http://doc.gwos.org/index.php/Install_Nvidia_driver](http://doc.gwos.org/index.php/Install_Nvidia_driver)
the initial boot splash screen displays fine but then I get an error message stating "Failed to start the X server....."  This eventually will return me back to the text only login.  Then what?  any pointers or advice on what I have to do next will be appreciated.  Thanks

---

### Post by varunus on 2005-12-29
Linux does have plug and play support; unfortunately, x.org does not yet.

To fix your problem, once you're dropped to a console after your "failed to start the x server" messages come up, type
```
sudo nano /etc/X11/xorg.conf
```

Scroll down to the part that says "Device", and make sure that the driver line is set to "nvidia".
```
Driver          "nvidia"
```
and then reboot.
What video card did you put in the system?

If that doesn't work, do the following; change the driver line to "vesa".
```
Driver          "vesa"
```
and then reboot.

This will get you to a very very bad GUI.  (Everything will be slow and jaggy.)  But, its a GUI, so we can fix it more from there.

---

### Post by MetalMusicAddict on 2005-12-29
Try a **sudo dpkg-reconfigure xserver-xorg** after you log back in and X crashes.

---

### Post by poofyhairguy on 2005-12-29
Whats the exact card. You might need the legacy drivers.

---

### Post by ge-force on 2005-12-30
Hi all
The system was initially installed with the mainboards onboard 810 graphics chipset with no problems.  The 'new' graphics card is a Nvidia G-Force 2 128Mb PCI.  
The command **sudo dpkg-reconfigure xserver-xorg **worked a treat and correctly identified the 'new' graphics card. Thanks.
What is the command to restart the gui?  I tried **xstart** once the system had reconfigured but that did'nt work. I resorted to the power button which the system quite nicely detects has been pushed and then proceeds to shut the whole system down.  What is the command to get the system to restart?
Thanks again for your assistance.

---

### Post by codejunkie on 2005-12-30
[QUOTE=ge-force]Hi all
The system was initially installed with the mainboards onboard 810 graphics chipset with no problems.  The 'new' graphics card is a Nvidia G-Force 2 128Mb PCI.  
The command **sudo dpkg-reconfigure xserver-xorg **worked a treat and correctly identified the 'new' graphics card. Thanks.
What is the command to restart the gui?  I tried **xstart** once the system had reconfigured but that did'nt work. I resorted to the power button which the system quite nicely detects has been pushed and then proceeds to shut the whole system down.  What is the command to get the system to restart?
Thanks again for your assistance.[/QUOTE]
i ran into problems with a compaq that had onboard video and a pci video card. you have to completly disable the onboard video in the bios, restart the computer if that dosen't work run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
if that doesn't work and by chance you cannot completly disable the onboard video in the bios like in my case you might have to assign the BusID in the /etc/X11/xorg.conf file to the pci card.

---

### Post by varunus on 2005-12-30
The command to start X is not xstart, but "startx".

However, based on what you've said, you can't use the standard nvidia driver.  You need the legacy driver, as your card is old.

Once you're dropped to your terminal and logged on (assuming X still won't start) type
```
sudo apt-get install nvidia-glx-legacy
```

This will install the older 7174 driver instead of the 7667 drivers.  This will make your card work.

---

### Post by Anon E. Mouse on 2005-12-30
Hi,

I'm a rookie trying to reconfigure a S3 card that's a replacement for one that was configured during installation. If I read this thread correctly, I should be able to to login at the text prompt and then just type:

**sudo dpkg-reconfigure xserver-xorg**

and hit enter...right?

From there it should detect and configure the card (assuming compatability)?

Thx

Anon

---

### Post by Anon E. Mouse on 2005-12-31
By detect and configure I mean as though it was a clean install.

---

