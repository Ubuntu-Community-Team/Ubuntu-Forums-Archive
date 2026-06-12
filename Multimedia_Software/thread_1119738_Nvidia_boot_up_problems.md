---
title: "Nvidia boot up problems"
date: 2009-04-08
forum: Multimedia Software
---

### Post by DJonsson2008 on 2009-04-08
Below is the list of the current driver and various
parameters in use. I'm using a 1024 wide screen, 
ACER LCD. 

I've an intermittent problem on boot up. 
During bootup I see the NVIDIA splash screen.
The Ubuntu horizontal line spash boot up thermomenter
And then the logon screen appears mostly white and 
completely scrambled, if i try to log in using the barely
visible user/pass field the screen starts flashing and
the usually locks up.  Sometimes this is corrected by
rebooting sometimes by re-installing the drivers from
the command prompt using Alt+CTRL F1.

I'm placing this under all variants because I use both Xbuntu 
and Ubuntu on this machine, this problem seems to happen before
the machine selects the variant in the boot up process.

The Ubuntu Flash screen looks ok then the logon screen appears garbled. 

I wonder why this happens, is ubuntu selecting a different
driver somewhere in the process?  

Where can I delete the extra drivers that may be perhaps 
making this happen (if that is the case)?

Below are some specs, any clues or speculations or links appreciated.

*********************************************************
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

Nvidia driver version 173.14.12
Ubuntu Hardy 8.4 Xfce4
Geoforce 8400 GS

---

### Post by DJonsson2008 on 2009-04-09
I'm attaching an image so so you can see what the
boot up screen looks like. 

I've dug around in the folders but find nothing that
resembles a log that would chronicle what takes place
after the system boots and begins loading the login
GUI.

If anybody can point me to an explanation of the sequence
that occurs from linux to ubuntu that may hold a clue.

It seems to me that something gets loaded between the 
ubuntu loading splash screen with its horizontal loading
bar (which looks fine) and when the logon screen appears.

Any help would in trouble shooting this would be appreciated,
I often have to reboot 2 or 3 times in order to get a usable
screen.

---

### Post by Lunatico_22 on 2009-04-09
I think you are using the wrong driver for your graphic card. All the geforce 6 and up should use the 177 or 180 driver, the 173 driver is for older cards. Try the 180 driver that has been recently added to the repositories, maybe that could solve the problem.

---

### Post by DJonsson2008 on 2009-04-11
Thanks for the suggestion. But the new driver does not help this problem. 

As well getting the 180 drivers to work on Hardy is somewhat complicated. Every time I attempt it takes about 2-3 hours. If I had to do this again I would of went with an Nvidia Series 7 Card which seems to better supported by Hardy. I do hope though that somewhere between Nvidia and Hardy the 180 driver somehow gets more fully functional.

---

### Post by DJonsson2008 on 2009-04-13
For now I've rolled back to Ubuntu generic Vesa drivers and Generic monitor settings.

The problems I've encountered is that neither the 173 or the 180
drivers will boot dependably on this workstation. As well the installation of both of the drivers (by any of the myriad methods available) is a time consuming rocket science unless one is fortunate enough to have it work the first time. 

The various methods and vintages of drivers as well seem to conflict and corrupt each other with each attempt of installation.

The older drivers in the 'restricted' repositories as well seem to have a multitude of issues, even though my Nvidia card here is documented to be compatible with them as well as the newer drivers. At this point having valuable work on this machine, I'm going to wait until I've a clean hard drive a stack of CDs to listen to and a free afternoon or 2 to to attempt to get these drivers working on a clean install.

Caveat -- it seems if an Ubuntu video driver install does not take -- cleaning up the flotsam and layering another set of drivers on top of it -- to enable a different version of video driver is as iffy as it is time consuming.

---

