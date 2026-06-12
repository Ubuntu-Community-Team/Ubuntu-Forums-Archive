---
title: "What's wrong with that ATI 8.42?!!!!"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by ivandrek13 on 2007-10-27
Hello everyone

I just can not make ATI 8.42.3 to work. I did everything I could have think of, followed the instructions form Forum, but I always get Mesa drivers back.
It seems that ATI drivers are installed somehow, and Catalyst is working, too, but system is not loading this driver. Instead, it keeps bringing back Mesa. 
Therefore, I have no 3D acceleration, I can not run games or Compiz. It's not that insist on these two things, but it's getting on my nerves when my hardware is not working as it should. 
I have Mobility Radeon X700 on Toshiba Satellite.

fglrxinfo just keeps giving me this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1

Can anyone help me with this?
Thanks!

Ivan

---

### Post by Nikos.Alexandris on 2007-10-27
[COLOR="Blue"]I have an ATI X1250. Read this... [http://ubuntuforums.org/showthread.php?t=588060&highlight=ati+catalyst](http://ubuntuforums.org/showthread.php?t=588060&highlight=ati+catalyst)
Hope it gives you a hint.[/COLOR]

---

### Post by ivandrek13 on 2007-10-27
I saw before most of the links you provided. Didn't help :(
Well, I guess that I'll just have to wait for some new version of drivers.
Anyway, thanks for trying to help.

Ivan

---

### Post by Supersaiyan.IV on 2007-10-27
> **ivandrek13 said:**
> Hello everyone

I just can not make ATI 8.42.3 to work. I did everything I could have think of, followed the instructions form Forum, but I always get Mesa drivers back.
It seems that ATI drivers are installed somehow, and Catalyst is working, too, but system is not loading this driver. Instead, it keeps bringing back Mesa. 
Therefore, I have no 3D acceleration, I can not run games or Compiz. It's not that insist on these two things, but it's getting on my nerves when my hardware is not working as it should. 
I have Mobility Radeon X700 on Toshiba Satellite.

fglrxinfo just keeps giving me this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1

Can anyone help me with this?
Thanks!

Ivan

I have been there aswell. Luckily I got it to work. The thing is to check if you actually install the necessary libraries, because some repositories may be off, and one little library makes you fallback to Mesa.

Then, before doing any fglrxinfo, make sure the driver is whitelisted so it can be loaded, _then_ reboot again (just in case). As I understand it, compiz uses it and therefore it loads on startup. Thats why whitelisting is so important. How to whitelist it says on may guider out there, just choose the more appropriate way that may work for you.

---

