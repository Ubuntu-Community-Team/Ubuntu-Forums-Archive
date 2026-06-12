---
title: "Enabling hardware 3D support with ATI"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by haemphyst on 2007-10-08
Well, I think I have searched as far as I can search...  Inspiron results, GeForce results, Mobility results...  No results located for ATI PCI-e X1550 cards, let alone ATI in general.

Anyway, I used the instructions as they appear here, the (ATI proprietary) driver seems to install just fine, I have full 22" widescreen resolution and refresh support, WinE installs perfectly, and I can install and start GuildWars.  Trouble is, I have no 3D support, (and that appears to be ANY 3D support, hardware or otherwise) and the system all but locks up.  Everything APPEARS to remain running, and Alt+Tab allows me to switch between applications - sort of.

I say "sort of", because the Guild Wars application never minimizes, even if I move it to an adjacent workspace, which it will do, eventually.

Suggestions, anybody?  Please?

---

### Post by kshane on 2007-10-09
Just another week or so and the new proprietary Linux driver will be released.  It is supposed to have a **serious** improvement in 3D support.

Kevin

---

### Post by haemphyst on 2007-10-09
Should I wait then?  Just hold off until it becomes available?  Or should I continue looking for the answer?

---

### Post by cobelloy on 2007-10-11
I have just bought a x1550 too (standard pce, not pci-e) and the fglrx driver is installed and such, but no 3D - the onboard graphics (in my dell) are far superior 3D-wise, I would like to hear how you fare - I will post also with any other info.

also I get this with fglrxinfo:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


what does that top line mean?

---

### Post by overlord.gaurav on 2007-10-11
Well, you havent installed the driver correctly if you are getting the **mesa** issue.
Try this, reboot and run fglrxinfo again:
```
sudo mkdir -p /usr/X11R6/lib/modules/dri  
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
```

---

### Post by cobelloy on 2007-10-12
it had no effect, same output and 3d still doesnt work

---

### Post by cobelloy on 2007-10-12
well, I've had a win, the official ati package seems to get 3d going, and this is what I get with fglrxinfo:

cobelloy@cobelloy-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1550 Series
OpenGL version string: 2.0.6747 (8.40.4)

i read a post earlier that said to disable fglrx in etc/default/linux-restricted-modules-common if you install the official package (because it is not registered to the package manager like the deb files?)

anyway I did that too, and the few 3d games I have are all real nice now - and glxgears makes around 1000fps - I think thats about twice what it was with my onboard (intel) graphics

very pleased now :)

---

### Post by haemphyst on 2007-10-12
Well, it seems I do NOT have 3D or even proper drivers installed...  I am still getting the mesa issue as well (I hadn't checked that before).  This seems strange to me, as before I installed the proprietary driver, I couldn't get the resolution or refresh rate I have now...  I just thought it was correct finally.  :(  I so wanted this one to be a success...

What am I doing wrong or missing?  I have NEVER been able to get any (higher-end ATI) video card driver to work, and that is why I think I keep "falling back" to Windows.  I know that between WinE and Cedega I can have support for all of my forseeable application needs (I only play one game...) but I need 3D support.

WAAAHHH!!!!  Someone PLEASE help me!  I do SO want to leave Winblows!

Tried the above suggestions, and this what I get:

haemphyst@UBUNTU:~$ sudo mkdir -p /usr/X11R6/lib/modules/dri
haemphyst@UBUNTU:~$ sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri
ln: creating symbolic link `/usr/X11R6/lib/modules/dri/fglrx_dri.so' to `/usr/lib/dri/fglrx_dri.so': File exists
haemphyst@UBUNTU:~$

What does that mean?

---

### Post by overlord.gaurav on 2007-10-12
They [this page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), maybe it'll help.

---

### Post by kshane on 2007-10-12
Go here, [http://albertomilone.com/wordpress/?cat=12](http://albertomilone.com/wordpress/?cat=12) , Alberto Milone's Blog site and and download/install ***ENVY***.  It will detect your card and install the most recent driver from ATI or Nvidia.  It works like a charm and is very simple to use.  I get the dreaded Mesa 3D showing up some how every once in a while and I just start up Envy and it puts things back the way they should be again!

Kevin

---

### Post by cobelloy on 2007-10-12
oryou could try the official ati installer like I did, 

first download the package from here: [http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html"), you need to change its permissions by right click to make it executable

then edit etc/default/linux-restricted-modules-common and add fglrx to the disabled bit

then just type -- sudo ./ati-driver-installer-8.40.4-x86.x86_64.run, and the rest just happens

or I should say just happened for me, I have kubuntu 704 with kernel 2.6.17-50-generic on a x86 machine, i downgraded the kernel due to problems with my ide devices being managed as scsi devices and not working

---

