---
title: "Added new graphics card - white screen"
date: 2009-02-17
forum: Multimedia Software
---

### Post by bailout on 2009-02-17
I have a dell desktop that came with onboard graphics. Ran fine with a 8.04 install. I have just tried to add an ati graphics card. Now it boots ok and displays the gdm screen but after loging on the screen just goes white.

I have tried sudo dpkg-reconfigure xserver-xorg but it makes no difference. How do I get ubuntu to rescan the hardware, recognise that it has a different graphics card and install the correct driver without reinstalling the entire os?

thanks

---

### Post by bettlebrox on 2009-02-17
Add the vesa module to xorg.conf that should get graphics running (maybe with a low resolution). Under the "Device" section of your xorg.cong add 	
Driver		"vesa"

If your not sure how to do this, post your xorg.conf and ask.

Then restart, see if X starts up, login, and see if you can get the "Hardware Driver" application to start, it should load the ati driver for you. It start it look under System->Administration->Hardware drivers.

Also have a look at the Ubuntu Guide for Hardy at:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers)

---

### Post by bailout on 2009-02-17
Thanks for the reply. IIRC the xorg.conf doesn't have a device section but I will try adding the vesa line in. However, I don't really want to install the proprietory driver. I just want to get the basic driver that would be used if I installed with the new card installed.

---

### Post by bettlebrox on 2009-02-17
Then the vesa driver should do the trick (if you can get a higg enough resolution setting).

---

### Post by markbuntu on 2009-02-17
Since the login screen works you should be able to change session and login to gnome-safe mode which will load the VESA driver. When you getback to your desktop make sure to set your desktop visual effects to none and you should be good to go. The latest ati driver 9.1 works very well with 8.04 except if you are using the rt kernel it will not work because the packagers forgot to include the rt patch.

---

