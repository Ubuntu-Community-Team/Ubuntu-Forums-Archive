---
title: "Just install ubuntu 9.10 New to it =( Ati 4600"
date: 2010-03-29
forum: Multimedia Software
---

### Post by Ganju on 2010-03-29
):P hey guys im a newb to linux this is my first one to install :P
my question is how do i install a driver for my radeon ati hd 4600?

---

### Post by Icarus315 on 2010-03-29
Go to System > Administration > Hardware Drivers and activate the Ati Driver.

Or, advanced install and latest driver (usually not needed):

Go to:
[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and download the appropriate Linux driver for your system.

In a terminal, go to the folder you downloaded it to and do a chmod +x on the file and then run it with sudo.  These two commands with the latest driver on a 64-bit system will look like this:

chmod +x ati-driver-installer-10-3-x86.x86_64.run
sudo ./ati-driver-installer-10-3-x86.x86_64.run

Follow the Next buttons to fully install it.

REBOOT after either of these methods to get the driver going properly.

If you are interested in an open-source driver (which doesn't have all the features for 3d games but is fine for everything else) see this page:

[https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

The open-source driver is usually set up correctly without you doing anything much on your part ;)  If you can move windows and they don't chug (you will know if they chug) then the open-source driver is working!

---

