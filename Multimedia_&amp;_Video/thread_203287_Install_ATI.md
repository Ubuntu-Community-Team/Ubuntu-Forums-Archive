---
title: "Install ATI"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by stijn1989 on 2006-06-25
hi

I have ASUS A9250 ati card and I download and run the driver installation. I took the easy way (tikking the first options) and installed it. But when I do this in the terminal:
> 
jozef@jozef-computer:~$ sudo fglrxinfo
Password:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

What do I do wrong?

I get this to:

> aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

This is the image: [IMG]http://img148.imageshack.us/img148/544/schermafdruk8lo.png[/IMG]

and for my xorg.conf click this: [http://www.pastebin.be/881/](http://www.pastebin.be/881/)

Can some help me?

thanks, stijn

---

### Post by stijn1989 on 2006-06-25
i'm using this docs: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually)

but it can't do the first command in the console.... :mad: 

******* ATI

can someone helps me, plzzzzz

---

### Post by stijn1989 on 2006-06-26
hi

ok the ATI has been installed but when I do quake3 it gives errors like this:

> [fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
.....
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT


does someone knows a solution for that?

thanks stijn

---

