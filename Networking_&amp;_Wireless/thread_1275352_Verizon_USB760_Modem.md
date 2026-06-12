---
title: "Verizon USB760 Modem"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by PlantMan2 on 2009-09-25
[FONT=Arial]I followed the instructions in the thread  [http://ubuntuforums.org/showthread.php?t=1002262](http://ubuntuforums.org/showthread.php?t=1002262)[/FONT]
  [FONT=Arial]And have the same problem many have had with this modem shutting down after about 50 seconds on one of my systems (see posts at the end of the above thread)[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]On a second system it works just fine.[/FONT]
  
  [FONT=Arial]Doing some troubleshooting I have found that:[/FONT]
  [FONT=Arial]After taking the RUN eject command out of the [/FONT]70-persistent-cd.rules
  [FONT=Arial]The flash drive never mounts. The auto-run doesn’t happen.[/FONT]
  [FONT=Arial]“Drives” are created  “USB drive” and “CD Rom” in the file manager but you can’t access them.[/FONT]
  [FONT=Arial]Entries are created in /dev/ for cdrom1 and cdrom2 but no additional drives are created in /media/ [/FONT]
  [FONT=Arial]I can’t mount cdrom1 or cdrom2[/FONT]
  
  [FONT=Arial]On the good working box the auto-run comes up and the device shows up in the file manager with VZAccess Manager as a name.[/FONT]
  [FONT=Arial]Same name is created in /media/[/FONT]
  
  [FONT=Arial]I believe that udev is not creating the device completely or properly and subsequently something in it’s monitoring causes udev to destroy the device  causing the USB760 to power down.[/FONT]
  
  [FONT=Arial]On a hunch I performed the following steps:[/FONT]
  
[LIST]
[*][FONT=Arial]Remove the physical DVD drive[/FONT]
[*][FONT=Arial]bring system up.[/FONT]
[*][FONT=Arial]mount /cdrom[/FONT]
[*][FONT=Arial]flash drive takes upwards of      1min to mount but I can then see the files.[/FONT]
[*][FONT=Arial]eject cdrom[/FONT]
[*][FONT=Arial]now I have access to the CDMA      modem in network applet on device ttyUSB0[/FONT]
[*][FONT=Arial]kill the process for udev[/FONT]
[*][FONT=Arial]the background processes turn      off the modem (led goes to yellow)[/FONT]
[*][FONT=Arial]unplug the modem and plug it      back in[/FONT]
[*][FONT=Arial]mount /cdrom – this time it      only takes a second[/FONT]
[*][FONT=Arial]eject cdrom[/FONT]
[*][FONT=Arial]now I have the CDMA modem      available again and I can stay online without the device going away.[/FONT]
[/LIST]
  [FONT=Arial]So … I know the modem will work on this system[/FONT]
But obviously this is not a convenient solution!

  
  [FONT=Arial]Both systems are up-to-date installs of 8.10[/FONT]
  [FONT=Arial]The working system is an intel system w/ Intel usb controller[/FONT]
  [FONT=Arial]The non-working system is a AMD motherboard with a ATI USB controller.[/FONT]
  
  [FONT=Arial]I believe that if the initial mount succeeded on this device it could solve the problem.[/FONT]
  [FONT=Arial]Anybody have some ideas?[/FONT]
  
  [FONT=Arial]Thanks in advance[/FONT]

---

### Post by PlantMan2 on 2009-10-01
Solved my own problem.
Changed to an Intel based MB w/Intel usb controller and this modem now works as it is supposed to.
Perhaps a bug in udev when dealing with ATI based usb hardware?

---

### Post by medic0079 on 2009-10-22
and how exactly did you do that?

---

### Post by PlantMan2 on 2009-10-23
I changed to an Intel based MB

---

### Post by itmattersnot on 2009-11-04
Anyone have any idea if this works in Ubuntu 9.10? Because I have tried to get it working on an HP laptop, running an Intel MB and Intel USB, with absolutely no luck at all. I can get VZ Access Manager to show up in the flie manager, but I cannot get CDMA to appear in the network applet, or anywhere in any of the networking settings, for that matter.

Is there any way to get this device working through the mobile broadband settings in the Network Connections dialogue?

Any help would be greatly appreciated, I am trying to save this machine from the clutches of Windows Vista, but it needs to be able to power this mobile broadband device in order for me to use Ubuntu on it.

---

### Post by pdc on 2009-11-04
there is a very compact distro called Crunchbang derived from Ubuntu: you can download; install on USB drive and try it; we used it for a bit on our Eee;

the latest 9.10 seems to have problems with USB modems: older distros seem better for USB modems

---

