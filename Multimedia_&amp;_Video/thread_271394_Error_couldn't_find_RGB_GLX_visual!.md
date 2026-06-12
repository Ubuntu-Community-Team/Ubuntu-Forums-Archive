---
title: "Error: couldn't find RGB GLX visual!"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by Over1ord on 2006-10-04
I'm trying to install my x800xt but its not working out for me.  I followed the instructions here [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually) but when I get to the fglrxinfo step it keeps giving me the same error, "Error: couldn't find RGB GLX visual!".  I have my xorg.conf device set as fglrx so now I am getting the right resolutions and my desktop looks alot better but I still dont have any of the 3d screensavers.  Any ideas?

---

### Post by Over1ord on 2006-10-04
Update: I was able to get the fglrx driver installed properly, now when I type in:

$ fglrxinfo 

I get:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.6065 (8.29.6)

But I still cant use any of the 3d screensavers or do anything non-2d

---

