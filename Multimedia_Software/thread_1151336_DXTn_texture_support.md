---
title: "DXTn texture support"
date: 2009-05-06
forum: Multimedia Software
---

### Post by solomonhomicz on 2009-05-06
I'm looking for support for DXTn textures.
It appears alot of my 3D graphics fritz.
I ran worldwind in terminal and got the following error message:

May 6, 2009 5:28:12 PM gov.nasa.worldwind.layers.TextureTile initializeTexture
SEVERE: Exception attempting to read texture file
javax.media.opengl.GLException: DXTn compressed textures not supported by this graphics card
 
Heres my graphics controller:
Mobile 4 Series Chipset Integrated Graphics Controller

I'm running 8.10 on a Dell Inspirion with Intel Core2
Any suggestions?:-?

Also, the image actually renders for a second, I see it and then it dissappears

---

### Post by garyvdm on 2009-09-22
From [http://forum.worldwindcentral.com/showthread.php?p=45020](http://forum.worldwindcentral.com/showthread.php?p=45020)

sudo apt-get install driconf
driconf

Under "Image Quality" change "Enable S3TC ..." to yes.

Save.

---

