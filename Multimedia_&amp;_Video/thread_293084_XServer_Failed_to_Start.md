---
title: "XServer Failed to Start"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by AJGoodwin42 on 2006-11-04
I just say this to get it out the way.  I am new to Linux, have been trying it out for the last two weeks as I consider moving over to it for all of my machines at home.  The laptop is fine, however the desktop is having same major difficulties...

I have a higher end NVidia card - 7900 series.  And while the standard kernel drivers for EFT are ok they do not allow for the resolution I want.  I downloaded the drivers from NVidia and also did some reading around here on how to install them.  The first time I did it, the same thing happened, but now this is the second time in a row and I thought I had everything ready this time - but apparently not.

Here is what I have happening.

First Error screen...

[asks if I want to see the output of the error]
Error: API Mismatch: the NVIDIA kernel module has version 1.0-7184 but the X module has the version 1.0-8776... please make sure all versions have the same version

the next section is just the fact that the above is not working, and the last message is start the GDM once the above is configure properly...

Which leaves me with...  where the heck to I even start.  All I am left with is a TTY1 screen and can log on, but not much else except navigate the file structure.


Thanks for any help.

---

### Post by tommcd on 2006-11-05
Well, to get the GUI back you can boot to recovery mode and do:
sudo dpkg-reconfigure xserver-xorg
this will get your GUI back, but you will need to reinstall the nvidia driver.
The best guide for that is this if you are on Dapper:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
or for Edgy:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
you want method #2 if you want to install the drivers from nvidia.
Hope this helps.

---

