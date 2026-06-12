---
title: "Broadcom 4318 Wireless Lan Controller"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by tbullock17 on 2009-08-09
My equipment: Dell Inspiron 2200 laptop
My wireless controller: Boadcom 4318 [AirForce One 54g] 802.11 (rev02)
uname -mr:  2.6.28-14-generic i686
op sys: Jaunty 9.04

I should also say at present I have windows XP also on the computer and installed jaunty by wubi from the Ubuntu site for same.
Does anyone think that dropping windows and reinstalling jaunty after purging the disk might make the install work?  The Broadcom is the only controller I have for wireless and it works in Windows XP.  I have been able to reach Unbuntu forums from the windows side using Firefox. 

So far in my forum browsing I have found many Broadcom lan controllers that were made to work, but never the one I have.  

Has any one been able to make that happen for this controller in Ubuntu 9.04?  I have tried using ndiswrapper, but probably my lack of success is my newbie status in ubuntu and linux generally.  

The information on the Ubuntu pages for this controller manufacturer indicates that there are many who have trouble.  I just discovered this category of the forums so I am moving my request for help here from the Absolute Beginner forum.

All Help Greatly Appreciated!

tbullock17 ;)

---

### Post by Metaljaz on 2009-08-09
I have a dell inspiron 9100 and have had no problems with my wireless once i did the below. 

Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

If the fwcutter is still not found, once synaptic is open go under:
Settings>Repositories>Third Party Software and check all boxes then
do the sudo update and install fwcutter again.

---

### Post by tbullock17 on 2009-08-10
> **Metaljaz said:**
> I have a dell inspiron 9100 and have had no problems with my wireless once i did the below. 

Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

If the fwcutter is still not found, once synaptic is open go under:
Settings>Repositories>Third Party Software and check all boxes then
do the sudo update and install fwcutter again.


Your instructions helped me confirm that I have b43-fwcutter, but cannot proceed from there; need more direction.  Now that fwcutter is installed, what do I do with it?
 
thanks. ;)

---

### Post by Metaljaz on 2009-08-10
Okay..making progress.
Go under System > Administration > Hardware Drivers and make sure the driver is activated.
If it is activated in the top right hand corner...oops Mac..lets try it anyway...look for the icon for wireless internet connection. Click on the connection to use it. Make sure you unplug your wired connection.

---

### Post by tbullock17 on 2009-08-11
The icon for wired/wireless connection is also in the upper right corner of the panel for a Windows Laptop.  I had to retain my wired connection in order for the download to work.  Under System>Admin>Hardware Drivers the messages were: (a) No proprietary drivers are in use on this system, and (b) Broadcom B43 wireless driver.  the screen showed that the driver was not activated and gave me a button to activate.  Pushing on the button caused nothing to happen until I connected to wired access.  Doing that enabled the download activity to complete.  After completing the message said that the driver is activated and currently in use.  But the system showed that the wired connection was active. 

I then disconnected wired and tried to connect in wireless mode.  I am doing this at work and will have to ask the help desk what the security values are that I need to enter.  It is asking for a Certificate Authority certificate.  I can choose ignore or choose CA certificate.  I choose CA certificate and the system sits there and does nothing.  I will have to get help desk input to see whether I am trying the correct hidden network here at work.  When I have their answers and have tried to see if I get connection, I will reply to this message and give an update.

The help desk says I do need the CA certificate.  However, I have not found a place where I can specify the certificate I need.  So I am hung there.  That is, wireless does not work and wired does.

---

### Post by Metaljaz on 2009-08-11
Okay now I think its just a matter of setting up the network you wish to use. Try right clicking on the network icon and select edit connections. From there choose wireless then add network and then fill in the requested information.

---

### Post by tbullock17 on 2009-08-12
> **Metaljaz said:**
> Okay now I think its just a matter of setting up the network you wish to use. Try right clicking on the network icon and select edit connections. From there choose wireless then add network and then fill in the requested information.

I have followed your steps above and still no luck.  Part of the problem is getting the needed information requested by the system.  Still working on that.  The people who can help me are not yet available due to press of business.  Will get  back to this thread after talking with them.

Thanks for your help thus far.  I am grateful you are persistent, even tho I am long between my postings.

Back after Help desk input.  We checked out values for wireless access to system here at work.  All seemed to be correct and still no connection.  That makes me wonder about my drivers.

System>Admin>Hardware Drivers screen shows that I have no proprietary drivers, that i do have Broadcom B43 wireless drivers available and that the driver is activated and currently in use.  Green dots to the left of the messages tell me that the effort to activate them was successful.

In the middle of the hardware driver window there is a message: "fwcutter is a tool that can extract firmware from various source files.  It is written for BCMB43xx driver files."  Does the fact of the messages having green buttons mean that fwcutter installed the correct drivers in the right locations?

All ideas appreciated!!

Tom

---

### Post by Metaljaz on 2009-08-14
Read through this link to see if there is any information that you have not tried:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by tbullock17 on 2009-08-18
> **Metaljaz said:**
> Read through this link to see if there is any information that you have not tried:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Success at last!!

Here is what I did:
a) used DBAN to wipe my disk entirely - no windows, no ubuntu, totally clean
b) used an ISO version of jaunty [previously burned to a CD-RW and verified by MD5sums] to install a fresh copy of Jaunty on the hard disk (I have an x386 computer); totally scrapped my wubi attempt and started over by building a Live Desktop CD and following the Community guidelines for doing this [[https://help.ubuntu.com/community/GettingUbuntu]]("https://help.ubuntu.com/community/GettingUbuntu%5D")
c) after installation of Jaunty, used wired connection and updated it by Synaptic Package Manager
d) after update, used above article reference and its info; found that the built-in Jaunty process did find and activate my wireless driver.  So now I have both wired or wireless access to the internet based on my physical environment.

Metaljaz, thanks very much for the help you gave me and your time digging out the needed information!

Tom

---

