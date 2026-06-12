---
title: "FGLRX/Ati drivers issues"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by varean on 2006-08-11
Im hvaing problems installing the ati-dirvers and getting them to work with my video card(ATI Radeon X1600 Pro PCIe).  I follow the guide in the wiki on installing the drivers manually and I get no errors during the entire thing, however, after logign back in, fglrxinfo shows this:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

What bothers me mainly is the top line: "Xlib..."  What does that eror mean?  I beleive that is why I cant swtich to opengl and why my drivers aren't working.  If you need more info to help, please let me know.

---

### Post by TheEmb3rEgg on 2006-08-11
I was trying to install proprietary ATI drivers last night, and I get the same xlib line. I don't have 3d rendering either. =/ My card is an X700 Pro PCIe. Any ideas?

---

### Post by ricesteam on 2006-08-11
Before doing this, make sure you have manually installed the ATi drivers correctly. 

Open up your apt-get and search for instances of "fgl". Remove the xorg ati drivers.

Not sure if it will fix for you, but it worked for me.

---

### Post by Greycloak on 2006-08-11
I followed the steps in this howto:

[http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)

I just replaced every instance of 8.25.18 with 8.27.10.

This worked perfectly to get direct rendering working on my Radeon 9200.

---

### Post by TheEmb3rEgg on 2006-08-12
Thanks for that link, I finally got 3D rendering!

---

