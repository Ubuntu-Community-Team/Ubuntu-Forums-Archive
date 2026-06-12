---
title: "Ubuntu 10.04 rt2870/rt3070 Driver Install"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by Willyweasel on 2011-08-16
**DISCLAIMER:** I made this tutorial for my personal use because I couldn't always remember all of the steps off the top of my head, but I thought I would post it so I could possibly help someone. I am not a expert Linux User, in fact I am still a newbie. Follow this tutorial at your own risk, it has never gave me any problems but I am not to blame if you wreck your system. If someone knows of a better way to do any of the following please let me know. After all I'm Still learning 

First obtain a driver for your device, the best place to look would be on the manufacturers website. In my case it was [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501) because I have a Ralink RT3070STA Chipset.

After you download and extract you driver files open the usb_main_dev.c file in a text editor, it is located in os/linux/ directory of the driver folder.

Change this:

```
#include "rt_config.h"


// Following information will be show when you run 'modinfo'  
// *** If you have a solution for the bug in current version of driver, please mail to me.
// Otherwise post to forum in ralinktech's web site([www.ralinktech.com]("http://www.ralinktech.com/")) and let all users help you. ***
MODULE_AUTHOR("Paul Lin <paul_lin@ralinktech.com>");
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
#endif
#endif // CONFIG_STA_SUPPORT //
``` To this:

```
#include "rt_config.h"


// Following information will be show when you run 'modinfo'
// *** If you have a solution for the bug in current version of driver, please mail to me.
// Otherwise post to forum in ralinktech's web site([www.ralinktech.com]("http://www.ralinktech.com/")) and let all users help you. ***
MODULE_AUTHOR("Paul Lin <paul_lin@ralinktech.com>");
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
MODULE_LICENSE("GPL");   <----------Add the line the arrow is pointing to 
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
#endif
#endif // CONFIG_STA_SUPPORT //

```You are adding the **'MODULE_LICENSE("GPL");'**

There is one other problem. The compile looks for a RT3070STA.dat file, but there is a RT2870STA.dat file instead. Open a terminal and fix that with this command:
[you need to be in the root directory of the driver your using for this to work]

```
cp RT2870STA.dat RT3070STA.dat
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Parts of the above were taken from [[http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved.html]](http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved.html]) and was written by member "waterhead" I made some modifications, but do not take credit for his or her work.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Now we need to do a few other things,
 
**1:** open the config.mk file in a text editor, it's located in "the folder where you extracted your driver"/os/linux/config.mk now change 'HAS_WPA_SUPPLICANT=n' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n' to 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'

**2:** Open a terminal and change to the directory were your driver resides

**IMPORTANT READ THIS!**
There are two options below only use one, if the first option doesn't work and you need to use option #2 do this first:
Make sure you are in the directory of the driver your using, then run these two commands in the terminal.
sudo make uninstall
sudo make clean


Now compile your driver, make sure your in the directory where you extracted your driver and run:
**[OPTION #1]**
```
sudo make
sudo make install
```
**[OPTION #2]**
The install process sometimes needs a special make install command, run this if make install does not seem to be working:
```
sudo make
sudo make install DAT_PATH=/etc/Wireless/RT2870STA DAT_FILE_NAME=RT2870STA.dat
```Now We need to blacklist the rt2800usb driver and some others to resolve conflicts, open a terminal and do this:

```
sudo gedit /etc/modprobe.d/blacklist.conf

```Then add the lines below to the end of the blacklist.conf file under a custom heading if you wish. An example of a custom heading would be: #my custom heading. Remember to add the pound sign before your heading. Otherwise it will be treated as a command.
 
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb

Now We need to do one other thing, open a terminal and do the following:

```
sudo mkdir /etc/Wireless/RT3070STA
sudo cp /etc/Wireless/RT2870STA/RT2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat

```This makes a RT3070STA.dat file in /etc/Wireless/RT3070STA  directory. The driver looks for this file but the install does not make this file.  Restart your system for the changes to take effect.

--------------------------------------------------------------------------------------------------------------------**OPTIONAL**-----------------------------------------------------------------------------------------------------------------------------------

**Note: USE CAUTION WITH THE NEXT STEP USE IT ONLY AS A LAST OPTION!** There is a built in driver named rt2870sta already, if you install your driver and it's named rt2870sta or rt3070sta and nothing happens or your device doesn't connect most likely you need to open a terminal and do the following:

```
sudo mv /lib/modules/2.6.32-33-generic/kernel/drivers/staging/rt2870/rt2870sta.ko /lib/modules/2.6.32-33-generic/kernel/drivers/staging/rt2870/rt2870sta.ko.bak
```What this does is rename the built in rt2870sta driver so we can use our driver,one thing to note here is in my example the path is /lib/modules/2.6.32-33-generic/kernel/drivers/staging/rt2870/rt2870sta.ko. This is because I'm using the 2.6.32-33-generic kernel, it very well could be different on your system.

For example the file in question would be at "/lib/modules/Your-Kernel-Version/kernel/drivers/staging/rt2870/rt2870sta.ko"

Now after you have done this and it still doesn't work or you would like to restore the built in driver open a terminal and do the following:

```
sudo mv /lib/modules/2.6.32-33-generic/kernel/drivers/staging/rt2870/rt2870sta.ko.bak /lib/modules/2.6.32-33-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
sudo insmod /lib/modules/2.6.32-33-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
sudo modprobe rt2870sta

```Now we need to uninstall the manufacturers driver, change to the directory of the driver you downloaded and do this:
```
sudo make uninstall
sudo make clean

```Rememer the above rule about your kernel version when executing the first set of commands listed in this section, you will most likely have to restart you system for this to take affect.




Hopefully after all this you have a working WiFi connection

                                                               
                                                                                                                                     - Willyweasel

P.S. Please leave a reply if this guide helped you, or if you just want to give me your 2 cents. :tongue:

---

### Post by nealos on 2012-09-14
Willyweasel,

I'd like to thank you for this clear and thorough tutorial.  I was finally able to get one of our classroom computers online!  The key for me was the "uninstall" and "clean" command lines since I had tried a lot of other stuff before reading your post.  Big help indeed.  Happy students = happy me and visa versa.

Neal

---

