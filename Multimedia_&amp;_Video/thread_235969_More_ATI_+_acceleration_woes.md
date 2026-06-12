---
title: "More ATI + acceleration woes"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by evansmw on 2006-08-14
Hello all, I'm a new Linux user and yet another person who's having video issues with their ATI card and trying to get 3d acceleration working.

I'm running 64-bit Ubuntu 6.06 (Dapper) and am using a Sapphire Radeon X1800 XT pci-express card. I've tried installing the ati proprietary driver using the installer from the ati's website, as well as using apt-get and other various graphical program managing utilities. When I use dpkg-reconfigure xserver-xorg to change the driver to fglrx, or even when I edit xorg.conf manually, x seems to freeze or something after I reboot. It doesn't crash (where you get that error message that lets you see the various log files), it just seems to display a black screen and nothing more happens. fglrxinfo and glxinfo | grep rendering both tell me that it couldnt find RGB GLX visual. dmesg | grep fglrx gives me no output at all. Vesa seems to be the only driver that works for me. lspci | grep VGA gives me this:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7100.

Any ideas? Thanks in advance.

---

### Post by evansmw on 2006-08-14
Update: I am now running the fglrx drivers and they seem to be at least somewhat working. I somehow managed to get around the black-screen hang. But now, fglrxinfo still says that it can't find RGB GLX visual. dmesg | grep rendering shows this:

[  45.332010] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  45.333021] [fglrx] Maximum main memory to use for locked dma buffers: 1884 MBytes.
[45.333041] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[   46.646954] [fglrx:firegl_unlock] *ERROR* Process 4532 using kernel context 0

Also, my video card seems to be running really hard ( the fan's really whirring on it ), but I'm not doing anything graphically intense, I'm just sitting on the desktop with a web browser open typing this.

Maybe someone can help me figure this out? Thanks again in advance!

---

### Post by evansmw on 2006-08-14
Sorry, I keep thinking of things to add that might help: the ATI Control Panel now shows useful information. Before I got around the fglrx causing the hanging black screen, the ATI control panel just said that OpenGL was unavailable.

Now, it correctly identifies my card as a RADEON X1800, memory size 256 MByte. Driver version: 8.26.18. It still says that OpenGL is unavailable (the Vendor, Version, and Renderer fields are all unavailable.)

I realize that this driver is an older version, but it's the newer version that causes the black screen to hang.

I hope that someone can help me with this. Thanks, all.

---

