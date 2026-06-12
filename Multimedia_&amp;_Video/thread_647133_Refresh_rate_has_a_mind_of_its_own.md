---
title: "Refresh rate has a mind of its own"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by Pethegreat on 2007-12-22
I am trying to use my monitor's full 1280x1024 resolution. I set it to 1280x1024 at 60 hertz. I know those settings will work with my monitor. I apply the changes and tells me to reboot., I reboot and get an out of range message. It says vertical is 75 hertz. I set it for 60, what happened? Is there a command line input I can use to set up the monitor my self? I used a reconfigure command to get my desktop back, and it has it some funky modes. 

I have an envision monitor from 2005 with an ATI x1650 video card.

---

### Post by z0mbie on 2007-12-22
You need to make sure refresh rates are right in** /etc/X11/xorg.conf** according to your displays manufacturer:
```

Section "Monitor"
    Identifier     "Generic Monitor"
[B]    HorizSync       28.0 - 80.0
    VertRefresh     48.0 - 75.0[/B]
    Option         "DPMS"
EndSection
```

*Notice the Horizontal and Vertical refresh rates. Check your display's manual. 

You can set these parameters with this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

[SIZE="4"][COLOR="Red"]Before you decide to edit xorg.conf, make a backup of it by:[/COLOR][/SIZE]
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by Pethegreat on 2007-12-23
I attempted to add the new refresh rates, and the 1280x1024 resolution. I get an error that won't allow me to save the changes. I have no idea how to get to the xorg files as root so I can get it to stick. 

The other command you told me to use only allows me to choose my video card chip manafacturer. I set that, and it closes out. I get this message 

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071223192352

```

---

