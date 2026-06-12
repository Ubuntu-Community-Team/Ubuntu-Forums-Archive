---
title: "ATI drivers problem"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by italian_boy on 2006-09-12
I had a problem with shutdown process hanging with a blank screen, then I read about a possible solution which consisted in upgrading the ATI drivers.
So I followed this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)

But now glxgears gives me bad fps values (around 200) while before, with the old multiverse drivers, I had 1400.
Also, I had to make a symlink from libGL.so.1 to libGL.so.1.2 in /usr/lib32 in order to solve a Google Earth startup problem (anyway, now google earth shows me the startup screen but then hangs at the initialization phase).

Are these known problems?
I'd really like to keep the latest drivers but they seem worse on my hardware.

My system: Ubuntu Dapper 64 bit with AMD Turion X2 and ATI Xpress 1100 card

EDIT: forgot this:

$ glxinfo | grep 'direct'
direct rendering: Yes

---

