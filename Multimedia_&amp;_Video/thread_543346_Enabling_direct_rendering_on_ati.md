---
title: "Enabling direct rendering on ati"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by kubilaycan on 2007-09-05
hi

my direct rendering is disabled but my ati driver seems to be installed correctly.

output of glxinfo:
kubi@k-linux:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
[COLOR="Red"]direct rendering: No[/COLOR]
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9600 XT

output of fgrlxinfo:
kubi@k-linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT
OpenGL version string: 2.0.6334 (8.34.8)

this forum here ([http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)) says that when this happens the following should be added to the xorg.conf

Section "Extensions"
    Option "Composite" "0"
EndSection

and when i went to check it was ALREADY THERE. i guess i added that when i was installing compiz fusion which is running perfectly.

i was able to find no further help on any fori and thus i am writing this.

i ran into this problem when i was trying to run cs source from wine 9.41 and it told me that my graphics card was unsupported and that it was direct3d hal. when i launch cs source from the terminal i get this message:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".


by the way i installed my ati drivers just by enabling the restricted devices thing and in automatically downloaded and installed it. so i did not use envy or anything.

can people help me how to enable direct rendering? i guess that is the culprit.

cheers

---

### Post by JoBoo on 2007-09-05
I've got the same problem when I log into a XGL session. But when I log into a Gnome session direct rendering is enabled.

Is this true for you too.

Greetz

---

### Post by kubilaycan on 2007-09-05
yeah its same for me too i just checked. how did u discover this? 

but in gnome session i cannot get cs source to start without crashing, so i cannot check if i actually have proper frames.

by the way, i first ran into all this trouble when i wanted to play cs source from wine. it said i had an unsupported video card, but it still let me play, but like about 1 fps.

---

### Post by whatever on 2007-09-05
once again: you cannot have dri AND xgl. the best thing you will get in xgl is accelerated indirect rendering.
if you want to mix compiz and gaming use aiglx instead of xgl.

---

### Post by kubilaycan on 2007-09-05
alright cool i didnt know that...thx

ati is not supported in aiglx nooooooooo

---

### Post by whatever on 2007-09-05
> **kubilaycan said:**
> ati is not supported in aiglx nooooooooo
with the radeon 9600 you can use the open source radeon driver which already has aiglx support. or you can wait until october when fglrx 8.42 will be released and include aiglx.

---

### Post by kubilaycan on 2007-09-06
cool.. i will wait then...

---

