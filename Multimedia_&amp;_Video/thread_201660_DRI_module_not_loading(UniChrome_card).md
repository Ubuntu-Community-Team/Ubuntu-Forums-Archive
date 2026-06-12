---
title: "DRI module not loading(UniChrome card)"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by Merlintrix on 2006-06-22
I have a Via UniChrome integrated graphics card VT8378.

This is the output of glxinfo |grep gl

server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
glu version: 1.3
glu extensions:

HOWEVER, 

glxinfo | grep rendering gives
direct rendering: No

My xorg.conf looks like this

Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"

Section "Device"
Identifier "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
Driver "via"
BusID "PCI:1:0:0"

Section "Screen"
Identifier "Default Screen"
Device "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
Monitor "hp m703"

glxgears too works without a hitch

Can any one help me?

---

### Post by pksings on 2006-06-22
If you look through your /var/log/Xorg.0.log file you will probably find at about halfway down that the "dri" kernel driver was not found.

A couple of the howtos for enabling 3D functionality state that you must load the module "dri" via /etc/modules.  This module doesn't exist on my system and you can confirm that it doesn't on yours by "sudo modprobe dri", if it comes back not found which it probably will then this will never work as the kernel was not compiled with this functionality.

I posted about this two days ago and no answer has been given or solution provided.

---

### Post by Merlintrix on 2006-06-22
Yup, sudo modprobe dri returns 
FATAL: Module dri not found

---

### Post by Oceola on 2006-06-23
I add this as it may relate to other cards under Linux ... a definitive answer might be nice.

I have an MGA g200 AGP card and I get the same message.
I went to my cards driver page and they have an rpm version of the drivers for my card and the G400 card as well. There's a hal module which comes in the package from MGA and I was wondering if I could just add the hal package to the modules folder and reboot to have the dri recognized. 

Also I found my card has 16MB memory and there had been some discussion the dri module wasn't loading due to lack of memory but it seems more it's just not recognized or not there and the HAL package may resolve it's application and recognition.:-k

---

### Post by Jasper Houtman on 2006-06-25
Have the same card, worked after i reinstalled DRM manually and added two lines to my xorg.conf file.
Under section "device" add the lines:

Option		"DisableIRQ"
Option		"EnableAGPDMA"

Restart and it should work

---

