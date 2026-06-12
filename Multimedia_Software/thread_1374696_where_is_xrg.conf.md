---
title: "where is xrg.conf?"
date: 2010-01-07
forum: Multimedia Software
---

### Post by pbremner on 2010-01-07
Hi All
I am trying to load a driver for an Nvidia 103M video card in a Compaq Presario CQ61 notebook. When I install the default driver via the default method - system/admin/hardware drivers the result is 6 screens on the display.

I have seen threads about editing the xorg.conf file. When I try to do this I cannot locate this file on my system. Does anyone have any pointers for me? Thanks in advance. PS. I am running Karmic with all updates loaded.

---

### Post by Chronon on 2010-01-07
You should find it at "[FONT="Courier New"]/etc/X11/xorg.conf[/FONT]".

---

### Post by pbremner on 2010-01-07
Hi, thanks for quick reply. I checked the path you specified without luck. No file called xorg.conf there.

---

### Post by Chronon on 2010-01-07
I don't think it's used by default anymore.  If you create one the settings you put there should still be respected.

I have an application "NVIDIA X Server Settings" that allows me to configure the NVidia driver on my system.  It will then generate an appropriate xorg.conf --- though, I have found that I need to run the program as root or it doesn't have the appropriate permissions to create/edit the file.

---

### Post by pbremner on 2010-01-07
I will give it a try and report back. I assume i can use gedit and save it to the directory you specified.

---

### Post by wojox on 2010-01-07
Open your terminal and run:

```
sudo nvidia-xconfig
```

Then add 

```
 Option "ModeValidation" "NoTotalSizeCheck"
```

In Section "Device"

to get rid of the six screens.

---

### Post by Chronon on 2010-01-07
I added an edit that you might find helpful.  I often find direct editing of xorg.conf to be a bit arcane.  If you wish to directly create/edit this file then you need to run "gksudo gedit /etc/X11/xorg.conf".

---

### Post by Chronon on 2010-01-07
> **wojox said:**
> Open your terminal and run:

```
sudo nvidia-xconfig
```

Then add 

```
 Option "ModeValidation" "NoTotalSizeCheck"
```

In Section "Device"

Beautiful.  This is the advice that I was trying to stumble toward.  :)

---

