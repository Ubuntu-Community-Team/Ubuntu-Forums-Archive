---
title: "Error Configuring X.org"
date: 2009-01-05
forum: Multimedia Software
---

### Post by Lanserr on 2009-01-05
I've been trying to get my Radeon 9200 Graphics Card Running in ubuntu 8.10 intrepid, and I was following this documentation: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), but when I went to restart the X Server I got the following error

```

(EE) Problem parsing the config file
(EE) Error parsing the config file
```

the following is my xorg.conf:
```
Section "Device"
        Identifier      "Radeon 9200 Pro"
        Driver          "ati"
        BusID           "PCI:1:4:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
        Device          "Radeon 9200 Pro"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
                Virtual         1024 768
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

and my PCI bus point:
```
01:04.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

```

more info as I'm not sure what's pertinent:
```
ray@ray-desktop:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

```

any help would be great

---

### Post by wolfen69 on 2009-01-05
to reset your config file, try: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then ```
sudo reboot
```

---

### Post by Lanserr on 2009-01-05
> **wolfen69 said:**
> to reset your config file, try: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then ```
sudo reboot
```

I tried what you said, and the error goes away but then my xorg.conf is reset to:
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

and I'm back to square zero

---

### Post by wolfen69 on 2009-01-05
are you using DVI or VGA out to the monitor?

---

### Post by wolfen69 on 2009-01-05
also, have you gone to system>administration>hardware drivers and installed the driver from there?

---

### Post by Lanserr on 2009-01-06
whenever I do it just says "no proprietary drivers in use" :(

thanks for helping though

---

### Post by Lanserr on 2009-01-06
oh and I just saw your other comment. I know my card is vga, but I'm not sure what I'm using. How do I find out?

edit*
my actual cable is a vga one, but I'm not sure if you're asking about that or a setting

---

### Post by wolfen69 on 2009-01-06
another way you can install the driver is to go to system>administration>software sources and make sure universe repo is enabled. then open terminal and ```
sudo apt-get install envyng-gtk
``` this app will download and install the ATI driver.

---

### Post by Lanserr on 2009-01-06
I installed envy and retried the old xorg.conf and got the error again. :(

I tried seeing it would autodetect with
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and it just configured it back to the 
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```
configuration

---

### Post by Lanserr on 2009-01-06
Okay I figured out what you were trying to get me to do and got envy to install ati drivers and got this error on the restart:
```
(ee) no devices detected
```

---

