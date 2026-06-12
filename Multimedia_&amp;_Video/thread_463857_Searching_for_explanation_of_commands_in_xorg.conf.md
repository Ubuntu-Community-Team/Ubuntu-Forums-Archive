---
title: "Searching for explanation of commands in xorg.conf"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by Vantskruv on 2007-06-04
Have anyone found a good explanation of all the commands in xorg.conf (specially for the graphics options)?

I've found one but it doesn't explain all of the commands and sometimes it lacks a good explanation of what the command do (i.e. Option "NoTV", "UseFBDev", "UseInternalAGPGART" etc). 

[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html)





Here are three explanations of options in the device tab of xorg.conf I found with google  (I've copied and pasted):

Option "UseFBDev" "True/False"-----------------------------------------------------------------------------------------
XFree86 can also use the Linux framebuffer device. There is a special XFree86 driver, called fbdev, which uses the framebuffer device. This allows XFree86 to support even more videocards (specially with the vesafb). Note however that this driver is un-accelerated, meaning it doesn't make use of specific extra graphics hardware on your video card, so graphics rendering can be slow. Many other XFree86 videocard drivers can also use the Linux framebuffer device (without losing hardware acceleration). This is done by adding above option with a "true" statement to the Device section of the XF86Config file. Check the manual page of the XFree86 driver to see if it supports this. There isn't a difference in performence between using the framebuffer device and not. The difference lies in the implementation of the driver (using the fbdev device moves videomode and colormap handling into the kernel). So it's mainly a developer thing -- users normally don't care. It just makes XFree86 use a 'clean' API to access the hardware, instead of it's own code that directly accesses the hardware.
----------------------------------------------------------------------------------------------------------------------

Option "UseInternalAGPGART" "yes/no"----------------------------------------------------------------------------------
At one point, the program will ask you "Do you want to use the external AGP GART module (y/n)? [n]". It wants to know if it should rely on the AGP support contained in the driver itself, or if it should use the kernels own AGP modules. The answer to this question will vary from system to system - sometimes either option will work, sometimes only one will work. Answering "n" means use the drivers AGP support, "y" means use the kernel AGP support.

This setting can be changed later on through the "UseInternalAGPGART" option in your X configuration file (/etc/X11/xorg.conf or /etc/X11/XF86Config-4). Setting "UseInternalAGPGART" to yes means "use the AGP support in the driver", and setting it to no means "use the AGP support from the kernel" (this requires kernel AGP to be enabled - see Q2.1).

There is some potential for confusion here because of the way fglrxconfig asks its question, so I'll try and state things explicitly. When you answer "yes" to the question ("Yes, I want to use the kernel AGP support"), it will set "UseInternalAGPGART" to "no". When you answer "no" ("No, I want to use the AGP support in the driver"), it will set "UseInternalAGPGART" to "yes". Make sure you don't get mixed up between the answer to the question and the value of the "UseInternalAGPGART" setting. 
----------------------------------------------------------------------------------------------------------------------

Option "UseFastTLS" "0/1/2" ------------------------------------------------------------------------------------------
Know parameters:

0 - fast
1 - faster
2 - working with everything

Effects:
TLS settings are critical for many apps you may like to use (just to name one: wine). The UseFastTLS should be 2 if you want wine and other apps with wacky threading models working fine.
Side-Effects:
When set to something different than 2 some apps might stop working.
----------------------------------------------------------------------------------------------------------------------






It would be very nice to find a complete documentation of the commands and what they do so you can configure your xorg.conf to the better. I.e. I'm using an ATI-card and running aticonfig to half-automatically configure my xorg.conf. But it doesn't configure everything I want so I have to manually  do the configuration myself. And it would help very much if I know the function of the commands I'm editing.

/Johannes

---

