---
title: "Screen turns black when I click on Desktop"
date: 2009-02-07
forum: Multimedia Software
---

### Post by kuriozux on 2009-02-07
Hi I have a Sony Vaio with intel 1.7 mhz, 1gb ram, 120 gb hd, Intel GMA 950 video card. It only has Ubuntu, which I have nicely customized and dont want to re-install.

Whenever I drag mouse on Desktop the area becomes black and I cant see any menu or open windows. Everything has been fine until I rebooted today.

Please help.

Thanks!

---

### Post by redroad55 on 2009-02-07
I do not know if this applies to you but give it a read , that's all I could find for now .. Post back ..Best to you

> UBUNTU FAMILY 8.10+ USERS ONLY


LAPTOP TOUCHPAD

Using a laptop? If your cursor shoots off all over the place when you type and seemingly clicks on things without your consent, have no fear, you can disable it's click function while typing in a few simple steps. First of all, execute the following command in the terminal:

gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

Next, copy and paste the following text into the empty document:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
</match>
</device>
</deviceinfo>

Ubuntu/Xubuntu Users: Navigate to "System > Preferences > Sessions" ("Applications > Settings > Autostart Applications" in Xubuntu) and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot.

Kubuntu Users: Create a text document in your home directory called "syndaemon", then open it with a text editor and add the following lines to it:

#!/bin/sh
syndaemon -i 1 -d -t -K

Close and save the file, then move it to the autostart folder with:

mv syndaemon ~/.kde/Autostart

Finally, make the file an executable script with the following command:

chmod u+x ~/.kde/Autostart/syndaemon

Why isn't it enabled by default for laptop users? Well, it's insecure. If you share your laptop with mean geeks, they could disable your touchpad.


PRE-UBUNTU FAMILY 8.10 USERS ONLY


LAPTOP TOUCHPAD

Using a laptop? If your cursor shoots off all over the place when you type and seemingly clicks on things without your consent, have no fear, you can disable it's click function while you're typing by opening your terminal and (carefully) doing the following:

gksudo gedit /etc/X11/xorg.conf

Next, find the section concerning your touchpad and copy the bold text below into your Xorg configuration file, so it looks similar to the example below:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "true"
EndSection

Make sure it all looks okay and that the "EndSection" text is in the right place, then close and save.

Ubuntu/Xubuntu Users: Navigate to "System > Preferences > Sessions" ("Applications > Settings > Autostart Applications" in Xubuntu) and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot.

---

### Post by kuriozux on 2009-02-07
> **redroad55 said:**
> I do not know if this applies to you but give it a read , that's all I could find for now .. Post back ..Best to you


thanks for your response, but that's not my issue. I seem to have some random issue that no one sems to understand. Maybe I'll just start over.

---

### Post by redroad55 on 2009-02-07
Try booting live cd to determine if it might be a hardware problem with touch pad..Post back

---

