---
title: "Nvidia 177 dr adjustments nessarry?"
date: 2008-12-10
forum: Multimedia Software
---

### Post by sandman3838 on 2008-12-10
Hello 

I have Ubuntu 810 new I just installed it.  For the Nvidia driver for my GeForce 7600gt card it suggested the 177 driver.  I'm using it now.  

However I found this here for setting up Nvida drivers?  Is this still necessary?

******  

[http://blog.golden-ratio.net/2008/05/03/compiz-and-emerald-in-xubuntu/](http://blog.golden-ratio.net/2008/05/03/compiz-and-emerald-in-xubuntu/)

****** 
Installation of a graphics driver

To get all the fancy effects enabled we need to install Compiz and Emerald. To enable these I had to get the graphics card working properly. Xubuntu managed to find and recognize the graphics card, but for some reason the drivers weren’t loaded properly.

mesa-utils contains a couple of nice tools for testing and debugging graphics so I decided to get it installed. Luckily it is part of the standard repositories, so all that was needed for the installation was to type:

sudo aptitude install mesa-utils

Among the packages installed along side meta-utils was the standard fglrx driver package for ATI-cards. Once all of the packages were installed I rebooted the computer and ran

glxinfo | head

The glxinfo program outputs a lot of information about your graphic setup, but for our current purpose the top part is the only one of interest - therefore we pipe it through head (head is a very nice little program that returns the first 10 lines of whatever is inserted). The output I got from that command was

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:

The important line here is the "direct rendering: Yes", which implies that the graphics hardware is properly initialized. If this says "direct rendering: No" it means that something is wrong with your current graphics setup.

Since I hadn’t done any real changes to the system yet I didn’t expect the graphics drivers to be loaded yet, but it seems that installing the fglrx drivers was the only thing required to get my ATI card working. I’m not one to complain about stuff working for no apparent reason, so I continued on to the next part.
Using AIGLX

Edit 2009-06-17: After getting some feedback it turns out that this part of isn’t always needed, sometimes Ubuntu will take care of AIGLX without you having to do anything. Some extra details about the modules used has been added to this section as well.

We now need to enable some form of composite managing of the rending in Xorg. Composite rendering ensures that the rendering of windows and other effects are done on the graphics card, instead of on the CPU as it was traditionally done. The standard composite manager in Xorg is called AIGLX. To check that your graphics card is supported you can run

glxinfo | grep 'GLX_EXT_texture_from_pixmap'

If that command returns a non-empty string you’re good to go.

Since AIGLX is part of Xorg now installation is pretty easy, all that is required is enabling a couple of options in the /etc/X11/xorg.conf file. When making changes to the xorg.conf file it is very important to make a backup of the previous working copy, since sooner or later you’re bound to make a change that stops Xorg from working properly. Once a backup has been made (cp /etc/X11/xorg.conf ~/xorg.conf-working) the first step is opening xorg.conf in an editor as root so we can make the required changes

sudo vim /etc/X11/xorg.conf

In the "Module" section of the file add the following lines

Load "dri"
Load "dbe"
Load "glx"

The dri and dbe modules aren’t required for Compiz to run, but they enable extra functionality that is nice to have. The dbe module supplies double buffering functionality in X, and dri enables the “Direct Rendering Interface” which is required for applications that need direct communication with the OpenGL library.

On older graphic cards the the following has to be added to the "Device" section

Option  "XAANoOffscreenPixmaps" "true"

I would recommend first trying without that option set, and only adding it if doesn’t work without.

Then the following should be appended to the end of the file

Section "DRI"
	Mode 0666
EndSection
 
Section "Extensions"
	Option "Composite" "Enable"
EndSection
 
Section "ServerLayout"
	Identifier     "Default Layout" #otherwise will give an error and fail to load GDM
	Option         "AIGLX" "true"
EndSection

The ServerLayout lines can also be added to an already existing ServerLayout section if it is present.

With those changes done you can restart the X server to ensure that everything still works. The fastest way to restart the X server is by executing

sudo /etc/init.d/gdm restart

This command will restart the Gnome Desktop Manager, which is the default even though I’m currently running Xfce and Xubuntu.

---

