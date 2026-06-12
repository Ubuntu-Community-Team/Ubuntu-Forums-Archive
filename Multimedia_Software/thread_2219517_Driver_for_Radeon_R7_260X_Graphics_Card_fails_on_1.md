---
title: "Driver for Radeon R7 260X Graphics Card fails on 14.04 LTS"
date: 2014-04-24
forum: Multimedia Software
---

### Post by jweiner on 2014-04-24
I just installed 14.04, and I have a graphics card AMD Radeon R7 260X that does not work with the built-in drivers for 14.04.  The AMD website claims to have a driver that is a 14.04 "candidate" whatever that means.  Does anybody know how to download and install the "candidate" driver?  I just installed 14.04 so I should not have to deinstall, purge or in any way get rid of earlier versions of the install software from Radeon or earlier failed versions of the drivers.

Thanks for any help...

John

---

### Post by jweiner on 2014-04-24
OK, I found a solution that seems to work.  First thing to do is to go to AMD site, [http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx), that announces the "AMD Catalyst 14.4 Release Candidate for Linux".  From that site the zip file for the driver can be downloaded and unzipped.  Then click on the "Installer Notes" link found at the top of the AMD page.  The url for the "installer notes" site is [http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx).  I just followed the instructions using the "Automatic Driver Installation Option", and the driver installed.  Then I rebooted.  I modified the boot so as to disable the "onboard" video an and enabled the "offboard" video option in the chipset section of the boot screen.  The 14.04 splash screen came up normally, and I checked the video driver by using 

fglrxinfo

in a terminal window.  The information returned shows that the Radeon driver is indeed being used.  Then I checked the graphics acceleration with

fgl_glxgears

which should show the traditional "glxgears" rotating rapidly around all three spatial axes in a box.

---

