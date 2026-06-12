---
title: "cannot connect with the USB modem"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by DependencyHell on 2011-07-29
Hi all!

I've just spent 2 days of extensive lurking how to solve this problem. Namely, i have ZTE usb modem, model MF626 T. The sofware provided with it works only under windows. What i tried first was to download hso.ko module (copied to the /lib/modules/`uname r`/kernel/drivers/usb/serial/). Then i downloaded hsolinkcontrol and HSOconnect.  Unfortunately, i didn't get those /dev/ttyHS* ports that should appear. Only /dev/ttyUSB*. I blacklisted option module. Then changed occurences of ttyHS* to ttyUSB* in .py sources for HSOconnect. what i get is the popup interface GUI that has "connect" button disabled. Then i tried to set up connection via gnome-ppp. The usb modem was automatically detected as /dev/ttyUSB1. But when i supply telephone number that i got with the stick, i get message after "Sending: ATM1L3DT*99*" ->"no carrier found". Then i tried to copy the other two modules i found on the net-airprime.ko and usbserial.ko. I've renamed the option.ko and old usbserial.ko in order to use them later if needed. And also i've put in /etc/udev/rules.d/
some scripts i've found on net, used to mount and unmount ZTE modem. None of all that worked, and somehow i have the feeling i've messed up everything. What i just posted above is the sum of everything i googled out. I would be very glad if someone would help me out with this.:) I usually like to spend some time lurking and googling, but this is simply taking too much time...:icon_frown:

---

### Post by gradinaruvasile on 2011-07-29
Have you tried sakis3g?

I used it with a few modems including a zte 110 and some modems that were unrecognized by the kernel and all worked.

Some modems are not automatically switched (this is the method that presents the operating system the modems modem capabilities instead of the included flash disk that contains the windows drivers) - this means that you have no /dev/tty/ttyUSBxx device created. In this case you have to switch the modem from within sakis3g or supply usb-modeswitch with some special options - example with an obscure huawei modem (-v is the vendor, -p is the device taken from lsusb, -H is Huawei-specific switching method, used only with Huawei modems): 

```

usb_modeswitch -v 12d1 -p 1011 -H
modprobe -v usbserial vendor=0x12d1 product=0x1011

```

Your modem is listed as working too:

[http://forum.sakis3g.org/smf/index.php?topic=87.0](http://forum.sakis3g.org/smf/index.php?topic=87.0)

Download here:

[http://www.sakis3g.org/#downloading](http://www.sakis3g.org/#downloading)

the full version, unpack it where you want and run it - i recommend running it in a terminal with the following options (the graphical version leaves behind tons of processes after terminated):

```

sakis3g --interactive --console

```

First make sure network-manager is stopped and no modem-manager is running.
Run the above command replacing the path to the script or with ./ if run from the current folder.
Choose setup modem then connect.
If asked for password and user and you dont need them for the connection (most cases), just enter anything (one letter is suffice) and press enter (DO NOT leave those fields blank!)

I have a script made that uses alacarte to make a tray icon for it:

```

#!/bin/bash
alltray --show --sticky --skip-taskbar "xfce4-terminal -T Broadband_connect -I $HOME/.local/share/icons/sakis3g.png  --disable-server -e 'sakis3g --console --interactive'"

```

Note - i have it made in xfce environment, you must replace the xfce4-terminal with gnome-terminal (or the graphical terminal emulator of your choice) and its subsequent options with their equivalents.
Also, the sakis3g.png icon is in a location i have it, you should locate it and modify the script accordingly if needed.

---

### Post by DependencyHell on 2011-07-29
Thank you very much gradinaruvasile!! It works, and i am absolutely delighted...
Cheers!

---

