---
title: "Leadtek WinFast DTV2000H Plus (+)"
date: 2011-02-03
forum: Multimedia Software
---

### Post by m0po on 2011-02-03
Hello all!
 I'm relatively new to linux, and I'm setting up a spare machine as a  HTPC. I've gotten Boxee working no problems and indexed all my media,  however I wish to get live tv on it. I'm just wondering how I can get my  DTV2000H + working... it seems to be a bit picky.
 I've followed instructions on the following two sites, but it still doesnt seem to work:


 [http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000_H_Plus](http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000_H_Plus)
 [http://istvanv.users.sourceforge.net/v4l/xc4000.html](http://istvanv.users.sourceforge.net/v4l/xc4000.html)
 

I have the 107d:6f42 variant, so the XC4000.
 Help?!?!

---

### Post by btdave on 2011-02-05
With this card I CAN confirm that it works, I'm in the process of setting it up again now so I will get back to you with the details on how to get this card working under Ubuntu 10.10 64bit

Cheers

---

### Post by btdave on 2011-02-05
ok am pretty sure i've got the card working now, is locking on channels in mythtv backend front end is crashing but thats another seemingly unrelated problem.

This is how I did it

First create a new folder in your home directory, this is where you'll be working from.
Next open up a terminal session and type in **hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)**
You may have to install mercurial but it will tell you if you need to or not and how to.
Next get the xc4000 patch from **[http://istvanv.users.sourceforge.net/v4l/xc4000.html](http://istvanv.users.sourceforge.net/v4l/xc4000.html)** the top one and copy that into the folder that you created earlier, there should also be a v4l-dvb folder in there as well.
In the terminal window go into the v4l-dvb folder and copy and paste this into the terminal window [B]patch -p1 < ../xc4000-winfast-a79dd2ae4d0e.patch

[/B]You may have to put sudo before it as without it it can throw up a few errors, even with this I still got two errors but its working so I'm not that fussed.

Next type in **make clean**
Then you'll have to **make menuconfig** but have to install something else, so copy and paste this in if you need to 
**sudo apt-get install ncurses-dev**
ok so once that is done you will have to edit the .config file in v4l so presumably you are in the folder you created earlier type in **sudo gedit /v4l-dvb/v4l/.config** and look for CONFIG_DVB_FIREDTV=m and change the m to an n, otherwise you will get an error when typing in make and it won't work.
Next type in **make**
Then **sudo make install**

Now we have to set the card option
type into terminal **sudo gedit /etc/modprobe.d/v4l-dvb.conf**
it will be an empty file but thats ok
type in **options cx88xx card=81**
Yes this is different card than what you have but thats ok, save and exit.
Now wherever you have downloaded the firmware go into that folder and type in.
**sudo cp xc4000.fw /lib/firmware/**

Now with a bit of luck restart and hopefully it should work, if not it may need the xc3028 firmware.

Its a long winded process but it worked for me and hopefully will work for you

Cheers

EDIT
Can obtain the xc3028 firmware here
[http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#How_to_Obtain_the_Firmware](http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#How_to_Obtain_the_Firmware)

---

### Post by Stibbs on 2011-02-21
> **btdave said:**
> 
Next type in **make clean**
Then you'll have to **make menuconfig** but have to install something else, so copy and paste this in if you need to 
**sudo apt-get install ncurses-dev**
ok so once that is done you will have to edit the .config file in v4l so presumably you are in the folder you created earlier type in **sudo gedit /v4l-dvb/v4l/.config** and look for CONFIG_DVB_FIREDTV=m and change the m to an n, otherwise you will get an error when typing in make and it won't work.

I got up to the make menuconfig part. Here is what happens:

"make[1]: Entering directory `/home/mirek/DTV/v4l-dvb/v4l'
/lib/modules/2.6.35-25-generic/build/scripts/kconfig/mconf ./Kconfig
#
# configuration written to .config
#


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

./scripts/fix_kconfig.pl
make[1]: Leaving directory `/home/mirek/DTV/v4l-dvb/v4l'"

Now, upon opening .config I find a blank file. What did I do wrong?

EDIT: For some reason, if I navigate to the v4l folder and then gedit .config it works, but trying to do it from the DTV folder resulted in an empty file. Hopefully this helps if anyone else has the same problem as me.
EDIT2: To make the v4l-dvb.conf file, first cd /etc/modprobe.d/ and then sudo gedit v4l-dvb.conf
EDIT3: I'm now at the "sudo cp xc4000.fw /lib/firmware/" part. Where/when did we download a .fw file? Typing locate .fw came up with nothing outside of the lib/firmware folder...
EDIT4: Ended up using xc4000-1.4.fw from the site. Didn't work. Installed xc3028 firmware also. Didn't work.

So after all that, I'm left at the beginning with an unusable tuner card.

---

### Post by btdave on 2011-04-03
try sudo make menuconfig

Also I remember reading something somewhere stating that you need to unload the firmware from the card inbetween tries, to do this you need to change the firmware file over and then shut down the machine, turn it off at the power point, press the power button to remove any residual power in the system then turn it all back on again. This is because at boot time the firmware is loaded to the card and doesn't get unloaded until power is cut off from the card.

---

