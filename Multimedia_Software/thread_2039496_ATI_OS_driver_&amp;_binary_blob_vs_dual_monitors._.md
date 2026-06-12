---
title: "ATI OS driver &amp; binary blob vs dual monitors. (Rant)"
date: 2012-08-09
forum: Multimedia Software
---

### Post by AKADAP on 2012-08-09
I have been using the OS drivers for several years due to previous experiance of ATIs binary blobs problematic instalation and issues with video.

I bought a second monitor a few days ago, and the fun began.

I have a PowerColor AX4850 which is an ATI HD 4850 card with 512 MB of memory. It has a dual link DVI, a DisplayPort, and an HDMI output.
My main monitor is a 2560x1600 display connected via dual link DVI. The new monitor is 1920x1080 120 Hz that I want to connect via DisplayPort.

After booting, the bios detected both monitors and displayed boot text on both. As soon as the OS ATI driver kicked in, the DisplayPort display went blank. I even tried with the DisplayPort as the only monitor connected, but the OS ATI driver refused to detect it. I hooked it up via the HDMI cable, and was able to get it to work, but with this connection it can only do 60 hz refresh.

With great dread I decide to install the binary blob from ATI. I go to the "Hardware: Aditional Drivers" in System settings. 
There are two items: 
ATI/AMD proprietary FGLRX graphics driver (post-release updates)
ATI/AMD proprietary FGLRX graphics driver

I try the first item. It fails. It points me at a log file that is thousands of lines long with hundreds of error messages almost all of which appear to be the script testing to see if it needs to do somthing and generating an error message for things it finds it does not need to do. It is impractical for someone unfamiliar with this tool to figure out what is actually going wrong since the actual error messages are hidden by the irrelevent ones.

I figure the first item is intended to be installed after the second item, so I try that, it works. (reboot... Installing ATI drivers is remanicent of installing anything on Windows, reboot about every minute or so, 20 times in a row). Try the 1st item again, that fails. Find that the second item is now uninstalled, install it again...

Do a bit of online research (Yah I know I should have started here.) Found that the 1st item has been failing for many people for quite some time. (Why is it still available to download if it does not work?)

Anyway...
The ATI drivers recognize my that there is a DisplayPort monitor connected, and I try to set it up. It does not let me set both monitors to full resolution. Both the System Settings Hardware:Displays, and the ATI tool both say that the desktop is too large. Only if I rotate the small display 90 degrees does it let both displays have the full resolution. At least I prove that the video card can drive both monitors at full resolution at full frame rate.

After wasting hours trying every suggestion I find online, including updating to the 12.6 drivers directly from ATI, I must conclude that both drivers are broken in ways that prevent me from using my monitors the way I wish.

The ATI blob will not let me set up a large desktop with side by side monitors because the desktop is "Too big".
The OS driver has no problem with the desktop size, but can't find monitors connected to the DisplayPort.

The ATI Binary Blob driver did not disappoint in the "screw up your system" department. When I was done messing with it and had removed it from my system, there were 3 copies of each Gnome panel on my system, and 3 copies of many of the icons & menues as well.
At least it did not leave me with a blank screen requireing a telnet in to the computer to uninstall the driver as it has in the past.

---

### Post by QIII on 2012-08-09
The post release updates version does not always work.  It is also not something that needs to be installed after the normal version is installed.

The normal version does not always work if installed using the "Additional Drivers" GUI method.

I generally suggest using the command line.  See "Using the Ubuntu repositories (alternate command line method)" in the ATI driver wiki in my signature.

What did you do in the Catalyst Control Center to attempt to solve the issues you ran up against?  Disabling Xinerama is generally a good idea when using monitors of different resolutions.

If you are angry about having to reboot several times, I hear you.  That is just the way it is with the ATI Linux driver.

It was much worse before AMD bought ATI.

---

### Post by AKADAP on 2012-08-10
> **QIII said:**
> 
What did you do in the Catalyst Control Center to attempt to solve the issues you ran up against?  Disabling Xinerama is generally a good idea when using monitors of different resolutions.


I did not realize I was disabling Xinerama, but I effectively did just that by selecting a mode in the ATI settings tool.
While in this mode, I was able to set both monitors to full resolution, this is the mode that added extra Gnome Panels to my main display. Also I was not able to drag windows from one monitor to the other in this mode. In fact I could not figure out how to open windows on the second monitor, making this mode useless. It was the correct resolution and refresh rate, but it was a blank white display with grey bars on the top & botom (an artifact of the broken gnome panels I think) I could move the mouse over to the second monitor, but not while dragging a window.

Xinerama works fine with the open source driver, so that is not the problem. The ATI driver is just broken.

---

### Post by QIII on 2012-08-10
I wouldn't say the ATI driver is broken.  Works on this machine with two monitors.

But it's clear you are having problems with it.

---

### Post by QIII on 2012-08-10
Are you setting your monitors thus?

---

### Post by AKADAP on 2012-08-10
> **QIII said:**
> Are you setting your monitors thus?

Yes, this is what I was trying to do, and I could do if one of the two monitors was set to a lower resolution than optimal. 

For instance 2560x1600 and 800x600 would work,or 1920x1080 and 1920x1080 would work, but 2560x1600 and 1920x1080 (optimal for both monitors) would not with the ATI binary blob.

I do have this working with the OS driver and HDMI, but of course I can't get the 120 hz refresh with this connection.

---

### Post by QIII on 2012-08-11
I am surprised this isn't working for you, although I certainly believe that you are having problems.  Few things in the world work just right for everyone.

However, monitors of different sizes and optimal resolutions have worked for me without fail.  I eventually simply just got tired of the different resolutions and bought another 1920x1080 to give me two monitors at the same resolution just for looks (although they are two different brands and one has a magazine under it so the frames align physically on my desk.)

---

### Post by AKADAP on 2012-08-11
> **QIII said:**
> I am surprised this isn't working for you, although I certainly believe that you are having problems.  Few things in the world work just right for everyone.

However, monitors of different sizes and optimal resolutions have worked for me without fail.  I eventually simply just got tired of the different resolutions and bought another 1920x1080 to give me two monitors at the same resolution just for looks (although they are two different brands and one has a magazine under it so the frames align physically on my desk.)

Did you try a set of monitors that would create a desktop exceeding either dimention of 3968x2560?
This is the number that the Ubuntu screen setting software included in its error message.
The ATI tool would allow a larger desktop than the Ubuntu one, but it did not specifiy what the limit was.

---

