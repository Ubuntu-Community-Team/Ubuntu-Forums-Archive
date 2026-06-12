---
title: "ATI Radeon"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by TomBull on 2008-02-27
I have a new Asus motherboard M2A-VM and a Sapphire HD 3850 video card.
I have the restricted driver for ATI installed.
When I plug the monitor into the ATI card and reboot I get a command line login no gnome.
I am still wondering if this card is going to be much better than my on board video but I can't get it to work.
How do I get my video card to work?

---

### Post by Melcar on 2008-02-27
What driver are you using?  The one you get from the Restricted Driver Manager in Ubuntu is rather old and I don't think supports the HD3xxx cards.  You will have to install the latest 8.2 driver yourself. 

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html")

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

(use Method 2)

---

### Post by Yellow Pasque on 2008-02-28
You can get the driver package right from the command line with this

```
sudo wget --no-check-certificate https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-02-x86.x86_64.run

```

---

### Post by TomBull on 2008-02-29
I just installed the ATI drivers but still isn't working.

tommy@tommy-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7281 Release

---

### Post by Yellow Pasque on 2008-02-29
You need to edit /usr/bin/compiz
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

Also, see this (more editing of /usr/bin/compiz and /etc/X11/xorg.con)f:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)

If it still does not work, then give us the output of typing 'compiz' in the terminal

---

### Post by TomBull on 2008-03-01
I made the changes in compiz still doesn't work.
I'm getting frustrated.

tommy@tommy-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA:        Flags: bus master, VGA palette snoop, stepping, fast Back2Back, 66MHz, user-definable features, ?? devsel, latency 0
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:791e (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by Joeb454 on 2008-03-01
May sound stupid, but have you tried reconfiguring X?

---

### Post by TomBull on 2008-03-01
Honestly don't know how to reconfigure X.

---

### Post by Melcar on 2008-03-01
> **TomBull said:**
> I just installed the ATI drivers but still isn't working.

tommy@tommy-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: **[COLOR="Olive"]ATI Radeon X1200 Series[/COLOR]**
OpenGL version string: 2.1.7281 Release

You have the onboard graphics off, right?

---

### Post by TomBull on 2008-03-01
As far as I can tell there are two settings that affect the graphics in the bios.
Primary Display Adapter is set to PCIEx, and not to OnChip VGA.
However the onchip vga still works with it set this way.
Also I have to disable HDMI Support or I cannot see the screen when plugged into the graphics card.
With HDMI Support Off I cannot see the screen when monitor is plugged into the motherboard but I can see it when plugged into the graphics card.
Right now I have HDMI on and am using the onboard video, in order to test the graphics card I have to restart the computer and reset the HDMI to off and plug monitor into graphics card.

---

