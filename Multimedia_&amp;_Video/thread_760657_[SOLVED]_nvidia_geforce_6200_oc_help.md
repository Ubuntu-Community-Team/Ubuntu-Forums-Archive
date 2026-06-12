---
title: "[SOLVED] nvidia geforce 6200 oc help"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by tad1073 on 2008-04-20
which driver do I need for this card? It is installed now but I disabled it through bios because of black screen of death.

---

### Post by ajgreeny on 2008-04-20
You could try re-enabling it in BIOS and rebooting ubuntu, but you may not get a GUI; it will depend on the graphic card on the motherboard in your system.  If you do get a GUI you can go to the System>>Administration>>Restricted Drivers Manager and enable the proprietary nvidia driver.

If that doesn't work, you may need to edit the /etc/X11/xorg.conf file to get the open source nv driver running for a GUI, then use the Restricted Driver Manager.  You can do the edit manually or better use sudo dpkg-reconfigure xserver-xorg and chose nv or nvidia (I can't remember what shows) when you get to the graphics card part.  Accept the defaults for the rest.  Good luck.

---

### Post by ajgreeny on 2008-04-20
You could try re-enabling it in BIOS and rebooting ubuntu, but you may not get a GUI; it will depend on the graphic card on the motherboard in your system.  If you do get a GUI you can go to the System>>Administration>>Restricted Drivers Manager and enable the proprietary nvidia driver.

If that doesn't work, you may need to edit the /etc/X11/xorg.conf file to get the open source nv driver running for a GUI, then use the Restricted Driver Manager.  You can do the edit manually or better use ```
sudo dpkg-reconfigure xserver-xorg
``` and chose nv or nvidia (I can't remember what shows) when you get to the graphics card part.  Accept the defaults for the rest.  Good luck.

EDIT:  Don't know why, but I tried to edit and put the code into code tags but somehow got a completely new post added instead of a simple edit

---

### Post by tad1073 on 2008-04-20
with the card enabled and the monitor plugged into it I get the black screen of death after the boot splash. So I removed the and am on the onboard video until I can get this figured out. I need more help.

I get no gui after the boot splash

---

### Post by tad1073 on 2008-04-20
I got gui now but my screen resolution is at 800x600.

```
sudo dpkg-reconfigure xserver-xorg
doesn't take me to my screen resolution cofig area
```

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

```
:~$ lspci
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:01.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
00:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:04.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 4f)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
01:04.0 SCSI storage controller: LSI Logic / Symbios Logic 53c895a (rev 01)
01:05.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
01:06.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
01:07.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller

```

I got my display to 1024x768 but I use 1280x1024 

```
sudo dpkg-reconfigure xserver-xorg
doesn't take me to my screen resolution cofig area
```

compiz is not working

I need help

---

### Post by tad1073 on 2008-04-20
bump

---

### Post by tad1073 on 2008-04-20
I got my screen resolution where I want it, now compiz is not working. I try enabling through appearence>visual effects>extra but it will not enable for some reason

---

