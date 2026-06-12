---
title: "Brand New to Linux! Need Wireless Help!!!"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by tafunk on 2009-12-17
Please forgive me if this post should be in the new user section...

I have an Aspire D250 Netbook with a Broadcom BCM4312 ver 1 Wireless Card.  I have downloaded and installed Ubuntu 9.10 as well as downloaded the driver package and read me txt file from Broadcom.  I have tried using one solution on this forum as well as followed the directions in the read me txt file and am still unable to get my wireless running.  Is there and way to get directions that are a little more understandable for a guy that has little to no experience using terminal?  As I am new to Linux as a whole I have been looking for an 'installable' solution without using terminal and was not able to find one.  I have also searched the forum and seem to get more lost than anything...please help!

Any and all help WILL be appreciated!!!

Thanks, Tim

---

### Post by Ubucrates on 2009-12-17
Open a terminal and run the following command. Make sure you've got a wired connection to be able to download the driver.
sudo apt-get install b43-fwcutter

If that doesn't do it, then try the following steps on this link:
[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560").
Post back here what worked for you.

---

### Post by tafunk on 2009-12-18
Got it working!!!  After trying a number of solutions I un-installed the OS and re-installed after reading that advise on another forum.  Sorry I did not keep the link to post...

After all that I read I believe the problem with my wireless came from my initial install.  When I did the first install I downloaded the OS and used the Windows Installer.  As the OS installed I did not have a wired connection.  The second time around I kept my network cable plugged in and after the install all of the wireless stuff came up after installing the drivers.

Thanks for the help!

---

