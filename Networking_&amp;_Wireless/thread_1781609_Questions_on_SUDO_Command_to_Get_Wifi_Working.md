---
title: "Questions on SUDO Command to Get Wifi Working"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by Griegfan on 2011-06-13
Good afternoon.  I am working to get Wifi on an older notebook (HP Pavilion zv6000 or zv6100).  

Ubuntu 11.04 has been successfully installed on this notebook, but Wifi does not work.  I still consider myself a new user.

I ran "sudo lspci" and, among other items, got this:
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

My understanding is that the following command might get Wifi working:
sudo apt-get install b43-fwcutter firmware-b43-installer

FYI Sources:
[http://ubuntuforums.org/showthread.php?t=1772744](http://ubuntuforums.org/showthread.php?t=1772744)
[http://ubuntuforums.org/showthread.php?t=1682391](http://ubuntuforums.org/showthread.php?t=1682391)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I was not connected via cable to the Internet when I ran the command.  I got prompted for my password then got this response:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package b43-fwcutter
E: Unable to locate package firmware-b43-installer

My understanding is that I need to be hooked up to the Internet when I run the command, but until I do that could you please answer these questions:

* From where is my system retrieving the items named in the command line -- from ubuntu.com?

* The last link listed in the "FYI Sources" above says the "firmware is copyrighted by Broadcom" and "the firmware from the binary drivers is copyrighted by Broadcom Corporation and must not be redistribted."  This question is probably a bit silly, but am I in violation of any copyright laws by running the above-mentioned command, "sudo apt-get install b43-fwcutter firmware-b43-installer"?

* This is not sudo-related, but I have the same two questions about the "Synaptic Package Manager."  When I click the "Reload" button, where is the data being downloaded from and is any of it ever proprietary and/or copyrighted?

Thank you for any help.

---

### Post by chili555 on 2011-06-13
> My understanding is that I need to be hooked up to the Internet when I run the commandCorrect.> From where is my system retrieving the items named in the command line -- from ubuntu.com?Th b43-fwcutter package comes from an Ubuntu repository. The package then goes elsewhere to get the firmware files, [http://downloads.openwrt.org/](http://downloads.openwrt.org/) I believe. OpenWRT creates aftermarket firmware for, primarily, Linksys WRTxx routers using, guess what, Broadcom chips.> am I in violation of any copyright laws by running the above-mentioned command,I believe Broadcom licenses anyone to use the firmware and no one to package it and re-distribute it.> where is the data being downloaded from and is any of it ever proprietary and/or copyrighted?From Ubuntu repositories unless you've added other non-Ubuntu repos; in which case I assume you know what you are doing. The header files simply tell the system what the latest versions are; a later version of a package installed on your system triggers an update. Nothing in the headers is proprietary. Some few actual packages may be. For instance, I believe you need to agree to a license agreement in the process of installing Macromedia flash. I think it's roughly the same as Broadcom; you can use it but you can't redistribute it as Griegfan flash.

---

### Post by Griegfan on 2011-06-14
> **chili555 said:**
> Correct.Th b43-fwcutter package comes from an Ubuntu repository. The package then goes elsewhere to get the firmware files, [http://downloads.openwrt.org/](http://downloads.openwrt.org/) I believe. OpenWRT creates aftermarket firmware for, primarily, Linksys WRTxx routers using, guess what, Broadcom chips.I believe Broadcom licenses anyone to use the firmware and no one to package it and re-distribute it.From Ubuntu repositories unless you've added other non-Ubuntu repos; in which case I assume you know what you are doing. The header files simply tell the system what the latest versions are; a later version of a package installed on your system triggers an update. Nothing in the headers is proprietary. Some few actual packages may be. For instance, I believe you need to agree to a license agreement in the process of installing Macromedia flash. I think it's roughly the same as Broadcom; you can use it but you can't redistribute it as Griegfan flash.

Thank you for the reply.  I'm on the notebook right now and have connection via a cable.  I ran the commands via Terminal but no luck.  Dang!  Here's the output:  

frank@frank-Pavilion-ZV6100-PN494AV:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
[sudo] password for frank: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
E: Unable to locate package firmware-b43-installer
frank@frank-Pavilion-ZV6100-PN494AV:~$

I'm sure it's a simple case of beginner's error.  When you have a moment, please let me know what I did wrong.

Thank you again!

---

### Post by chili555 on 2011-06-14
If I am not mistaken, I think it's a matter of adding the software source, i.e. repositories, that hold b43-fwcutter. The easiest way is to open Synaptic and go to Settings > Repositories and enable as shown attached. You will be prompted to Reload, because new packages are available and Synaptic needs the header files to know what they are. As long as you are in Synaptic, search for b43 and install your packages.

Select, or leave alone, the Server for... part as appropriate for your locale.

---

### Post by worm91 on 2011-09-22
Thank you sooooo much !!!!

works perfect for me on a Pavilion zv6000

---

### Post by mattmike310 on 2012-11-22
It worked perfectly. Dell inspiron 2200. Edubuntu 12.04
Was getting error about missing firmware for wireless adapter, Broadcom BCM4318 [Airforce One 54g]. Nothing seemed to work. Tried above and now its working. THANKS!!!!
Recap:
Connect to network with Ethernet cable.
On UPDATE MANAGER, click SETTINGS. On the Ubuntu Software tab, Make sure all boxes checked as shown in above illustration. Was having problems with my password being recognized to initiate the update. I changed DOWNLOAD FROM to: Main Server. (Slight change from above)
No more update errors.
Once update complete, restart machine.
Open terminal (Control+Alt+t)
Type:          sudo apt-get install b43-fwcutter firmware-b43-installer
Enter your password. After it finishes firmware update, disconnect Ethernet cable, wait a few seconds. It should then be able to detect wireless in your area.

*****Be sure wireless card active. On inspiron 2200, (Fn + F2) to toggle off/on.

Hope this helps others. Again, thanks for the help.

---

### Post by mattmike310 on 2012-11-22
Very strange..
Have another inspiron 2200, exact same specs as previous one.  Am trying same process described in previous post. When I update using the MAIN SERVER, it tells me everything is up to date. (I updated yesterday). However when i try to update the firmware, it indicates that the location is not found. I changed to update from the US server. Now it indicates 300+ updates and about 300 Mbs of updates are needed. I did not run the software update, but left the US Server as location.  I ran the sudo apt-get terminal command mentioned above. It seemed to find it. The wireless card was enabled so not sure what the problem was. I disconnected the Ethernet, waited a few seconds. Now its working.  I`m changing the location back to MAIN SERVER. It keeps saying 343 updates available, 0 from the main server. As mentioned earlier, kept getting password error when using US Server. Internet still working great.

Thanks again!

---

