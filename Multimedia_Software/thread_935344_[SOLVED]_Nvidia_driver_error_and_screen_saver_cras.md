---
title: "[SOLVED] Nvidia driver error and screen saver crash"
date: 2008-10-01
forum: Multimedia Software
---

### Post by bedhead75 on 2008-10-01
My Nvidia driver installation (96.43.05 through EnvyNG) and xorg.conf settings were fine before in Hardy Heron 8.04 LTS.  I had this working fine as of 3 weeks ago and everything was fine the first time around.  In an effort to try to improve DVD playback performance very recently, I was playing around with the "Nvidia X Server Settings" and caused a crash after clicking on "Apply".  Everything froze up and I had to hard boot the computer.  When I try to go back into Nvidia X Server Settings I get an error that reads "You do not appear to be using the Nvidia X Driver.  Please edit your X configuration file"...etc.  I am also unable to change my screen resolution through system preferences and I get an error that reads "The X server does not support the XRandR extension.  Runtime resolution changes to the display size are not available".
     In an effort to fix this I had tried re-installing the Nvidia drivers using EnvyNG, through Synaptic, and even downloading the proper *.run file from the Nvidia site. The first time I reinstalled the driver using EnvyNG I might not have uninstalled the driver first before installing it again, and I'm not sure if this is a cause of my problems. The driver from the Nvidia site resulted in a screwed-up Compwiz (white screen problem) so I uninstalled that and re-installed the driver using EnvyNG, and I'm using my original xconf.org file (I had a back up of the one that worked in the very beginning). 
     I am still getting the same errors when trying to use Nvidia X Server Settings and when I try to change screen resolutions.  I also realized that using the screensaver now crashes gnome. It freezes, the screen goes black, and goes back to the login screen.  This never happened before.  The screensaver crash happens when I'm just previewing screen savers in the little window.  I notice what used to be a smooth playing of the screensaver in the preview window before has now become very choppy and then everything crashes.  
     My video card is the Nvida Geoforce2 MX 420.  I know that a Nvida driver is installed and running because because I can get Compwiz 3D effects and glxgears gives ~1000fps rates, but somehow my settings or the installation has changed from the first time when everything was working properly.  Sorry for the long post but I wanted to make sure I explained the history of what happened.  Can anyone help?

---

### Post by bedhead75 on 2008-10-01
I forgot to add that the screensaver crash is only specific to the "busy spheres" saver, which was what I was using originally.  The other ones don't seem to have this problem.  Isn't that weird?

---

### Post by bedhead75 on 2008-10-01
After digging around in Google I found this link ([http://forum.compiz-fusion.org/showthread.php?t=8666&page=3](http://forum.compiz-fusion.org/showthread.php?t=8666&page=3)) and I managed to fix everything at once simply by uninstalling xserver-xgl using Synaptic, which apparently was not needed by Compwiz...and was somehow interfering with my Nvidia drivers after their reinstallation.

---

