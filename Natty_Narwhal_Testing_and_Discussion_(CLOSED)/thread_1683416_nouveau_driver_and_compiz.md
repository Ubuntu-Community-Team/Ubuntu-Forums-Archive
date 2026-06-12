---
title: "nouveau driver and compiz"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2011-02-07
wonder if someone can help.

i have an nvidia geforce glx460 card. 

i installed xserver 1.10 by mistake and needed to go back to nouveau so i thought i try the libgl1-mesa-dri-experimental for 3d support.

before i installed it i get the same output from glxinfo than i did after i installed it.

i am unable to start compiz and therefore cant start unity, but glxgears works and gives over 500fps. when trying to start compiz get error saying GLX_EXT_texture_from_pixmap is missing when it is listed in glxinfo. 

any ideas.

---

### Post by mc4man on 2011-02-07
Don't have that nvidia card avail. here but have found that 2 pci-e cards (8&9000 series) will not work w/nouveau 3d, though an AGP card (7800) will.
While your error message  is different, here is a current on nouveau 3d and compiz
(same result, no compiz/unity w/ nouveau 3d
[https://bugs.launchpad.net/nouveau/+bug/710588](https://bugs.launchpad.net/nouveau/+bug/710588)

---

### Post by lekzz on 2011-02-12
Same problem here on natty on a GLX460: compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing

Tried both manual install of libgl1-mesa-dri-experimental and by selecting "Experimental 3D support for NVIDIA cards" in jockey-gtk.

Can't seem to find any more about this issue, which makes me think it's perhaps a GTX460 issue?

---

### Post by cecilpierce on 2011-02-12
Same thing with GF 6200 AGP, tried everything I could but just have to wait I guess :(

---

### Post by terry_gardener on 2011-02-12
i downgrade to xserver 1.9 and then installed the nvidia current driver and back to normal i will wait for the new nvidia driver to be release before upgrading the xserver again.

---

### Post by cecilpierce on 2011-02-12
> **terry_gardener said:**
> i downgrade to xserver 1.9 and then installed the nvidia current driver and back to normal i will wait for the new nvidia driver to be release before upgrading the xserver again.

How did you do that ?   :confused:

---

### Post by terry_gardener on 2011-02-12
step by step guide of what i did. 

before i upgraded to 1.10 i moved the xorg file just incase. 

1. download the attached script. 
2. remove the .txt extension and then make it executable. 
3. double click the file and select run in terminal. 
4. type sudo password and press enter. 
5. wait for it finish and then open hardware drivers (system-admin -hardware drivers) 
6. install the nvidia driver. 
7. copied old xorg file back to correct place (/etc/X11/ )

reboot and then you should have xserver 1.9 with nvidia current driver. 

note: if you didn't move the xorg file before you upgraded or installed fresh then at step 7. run the command sudo nvidia-xconfig 

this is for x86 (32bit version of ubuntu) 

hope this helps.

---

### Post by cecilpierce on 2011-02-12
Thanks ! :)

---

### Post by lekzz on 2011-02-17
Thanks. Decided to go back aswell as the new nvidia beta drivers still don't support 1.10

Get newer xserver-xorg-input-evdev if you want working deceleration here: [https://launchpad.net/~xorg-edgers/+archive/ppa/+files/xserver-xorg-input-evdev_2.5.99.901%2Bgit20101204.31ba99e9-0ubuntu0sarvatt%7Emaverick_i386.deb](https://launchpad.net/~xorg-edgers/+archive/ppa/+files/xserver-xorg-input-evdev_2.5.99.901%2Bgit20101204.31ba99e9-0ubuntu0sarvatt%7Emaverick_i386.deb) (or _amd64.deb)

---

