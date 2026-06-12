---
title: "How to change video card from NV to ATI?"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by kvonb on 2006-06-27
Before I trash my system and do a clean install; wasting months of work, does anyone know how to successfully change video cards?

I want to remove my nvidia gf2 and install an ati 9200se.  I've tried as many of the guides that I can find, the driver is installed and working:

-----------------------------------------------------------
$ dmesg | grep fglrx
[   51.323684] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   51.326455] [fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[   51.326852] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0
-----------------------------------------------------------


But I stilll get:

-----------------------------------------------------------
$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!
-----------------------------------------------------------


I'm tired, have a headache, and I'm going to bed before I smash my computer!!!!

Help would be greatly appreciated.

Regards,  Kev ](*,)

---

### Post by ajgreeny on 2006-06-27
I wish you better luck than I have had trying to get the fglrx driver installed for my ati 9200se.  Ihave spent hours looking at the various threads on this forum and still can not get it to work.  Luckily I try these thing out on a separate partition install of dapper and keep with the ati linux driver on my main working system.

If you manage to get fglrx to work with the card, please let me know how, and then I can waste even more hours trying it out again.

---

### Post by kvonb on 2006-06-27
I got my 9200se working on a CLEAN install of Dapper and a CLEAN xorg.conf, so I know it can be done.  Unfortunately I need to do it on a "DIRTY" system and haven't had much luck so far.

Try the following (when you have time) and see if it works for you.
If you need the libGL mentioned, let me know and I can e-mail it to you.

This is what I did:
------------------------------------------------------------------------------------------------------
Enable "universe" and "multiverse" in Synaptic
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo gedit /etc/default/linux-restricted-modules-common
Change DISABLED_MODULES="" to DISABLED_MODULES="fglrx"
sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
Download the ATI driver installer from [www.ati.com](www.ati.com) (I used 8.25.18-x86)
Make a folder for this work, I used ~/ati-install and move the downloaded file into it, this will make it easier later
Change to the new folder: cd ~/ati-install
chmod +x ati-driver-installer-8.25.18-x86.run
./ati-driver-installer-8.25.18-x86.run --buildpkg Ubuntu/dapper
sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.25.18-1_i386.deb
sudo dpkg -i fglrx-control_8.25.18-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
## and now for the trick part ##
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
Download older libGL.so from:
[http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2) (right click and save as)
Move the downloaded libGL.so.1.2 to ~/ati-install
sudo mv /usr/lib/libGL.so.1.2 /usr/lib/old-libGL.so.1.2
sudo cp ./libGL.so.1.2 /usr/lib/
sudo cp ./libGL.so.1.2 /usr/lib/fglrx/
Check /usr/lib/libGL.so.1 link and make sure it points to /usr/lib/libGL.so.1.2
Reboot
------------------------------------------------------------------------------------------------------
Test:
Run: fglrxinfo
If all went well, you should see a version of the following:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9xxx Generic
OpenGL version string: 2.0.5814 ( 8.25.18 )

Run: fgl_glxgears
This will give you a good framerate. TIP: make the window smaller to get a higher framerate! 

Hope you have some joy!

Regards,  Kev :)

---

### Post by kvonb on 2006-07-03
OK, after a complete re-install this is what I did:

This is an extremely "dirty" process, I don't bother to backup the old libs, just delete them and setup the new stuff.  I suggest you BACKUP everything BEFORE trying this, I will NOT accept responsibility for destroying or losing ANY data.

USE AT YOUR OWN RISK!!!!!

The following can be copied, pasted, and run as is, or download the attached file, change it to executable: chmod +x ati-install.txt, the run it: ./ati-install.txt.

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
modprobe agpgart
modprobe -r fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
mkdir ~/ati-install
cd ~/ati-install
wget http://www.ground-impact.com/libGL.so.1.2
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
sudo rm /usr/lib/libGL.*
sudo cp ./libGL.so.1.2 /usr/lib/
sudo cp ./libGL.so.1.2 /usr/lib/fglrx/
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
sudo rm /usr/lib/fglrx/libGL.so.1.xlibmesa
sudo ln -s /usr/lib/fglrx/libGL.so.1.2 /usr/lib/fglrx/libGL.so.1.xlibmesa
sudo gedit /etc/X11/xorg.conf

```
look for the following section and make it the same:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        Option	    "UseInternalAGPGART" "no"
EndSection

```
sudo gedit /etc/modules
```

add the following lines:

	agpgart
	fglrx
	dri

REBOOT

```
fglrxinfo
``` You should now see ATI not MESA, if you do: bang head on desk and use the big "hammer" method!  OR re-install Dapper from scratch then try again!

For updating or re-installing the driver, try apt-get --reinstall for the apt-get install lines at the top of this.  I haven't tried this, but it might work.

I did this whole process after updating my kernel and it worked, don't forget that each time you update your kernel you will have to do ALL this again!

Regards,  Kev :)

---

