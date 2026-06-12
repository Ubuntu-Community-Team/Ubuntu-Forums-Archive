---
title: "Mounting hard drive from apple airport extreme base station"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by msharelick on 2009-11-04
Hi:

I have an apple airport extreme base station as a router.  It currently has my Ubuntu 9.0 desktop successfully routing internet traffic through it.  

There is a Western Digital external drive plugged into the usb jack for the base station. 

How do access it from Ubuntu?

Thanks

Matthew Harelick

---

### Post by raidoh on 2009-11-26
It took a little trial and error, but I got this working today on Ubuntu 9.10 with Gnome desktop (I didn't do this on the command line). Granted, I originally configured the Airport setup utility from another computer, so your situation may be complicated if you can't do that. 

First, I installed Samba for sharing folders (right-click on a folder in the file manager and choose *Sharing Options* to prompt for the installation). Then I went to *Places* -> *Connect to Server*. 

*Service Type*: Windows Share
*Server*: IP address of your Airport Extreme
*Share*: the name (case-sensitive) of your shared partition, even if there is only one.
*Folder*: I left this blank since the whole disk is shared, not just a particular folder.
*User Name*: If your disk is shared via accounts, enter a username. Mine is shared just by a password, so I think I left this blank. 
*Domain Name*: name of your domain or workgroup

If you select *Add a bookmark*, it will be listed in the file manager on the left side and easy to get back to. You'll be prompted for a password once you hit *Connect*.

---

### Post by cozybop on 2009-12-02
I actually found a solution to this on my own one night.

On a Mac or Windows with AirPort Utility.

Go to AirPort Utility.
Click Manual Setup on the bottom.
Click on Disks on top.
Then click on File Sharing.
In the Airport Disk Guest Access drop down menu make sure that it is on Read and Write.
Wait for the router to restart and viola you got access.
Just go to Network on Ubuntu and you should find an extra server that says the name of your router.

Also make sure that Enable File Sharing is checked as well.
And that Secure Shard Disks drop down menu is on With AirPort Extreme Password.

---

