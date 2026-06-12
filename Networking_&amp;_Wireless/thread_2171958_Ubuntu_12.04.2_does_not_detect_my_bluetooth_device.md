---
title: "Ubuntu 12.04.2 does not detect my bluetooth device"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by Abhishek_K._Pandey on 2013-09-02
Hello all.
My laptop is Dell Inspiron 3521 and I am using Ubuntu 12.04.2
The problem is that Ubuntu is not detecting my Bluetooth device. Its an inbuilt device and has a hardware lock as well as soft lock feature.
I remember, when I installed Ubuntu initially, it used to detect my BT, though it doesn't used to search devices. But, now, after updating Ubuntu, it does not detect BT at all. I have tried turning it on-off several times, but no success.

---

### Post by Homayoun_Shahri on 2013-09-30
> **Abhishek_K._Pandey said:**
> Hello all.
My laptop is Dell Inspiron 3521 and I am using Ubuntu 12.04.2
The problem is that Ubuntu is not detecting my Bluetooth device. Its an inbuilt device and has a hardware lock as well as soft lock feature.
I remember, when I installed Ubuntu initially, it used to detect my BT, though it doesn't used to search devices. But, now, after updating Ubuntu, it does not detect BT at all. I have tried turning it on-off several times, but no success.


Here are steps necessary to get bluetooth working in Inspiron 3521:
1- Download, compat-wireless-3.6.8-1-snpc.tar.bz2. You might have done that to get your wifi working. Edit the file in drivers/bluetooth/ath3k.c, and these two lines: under AR3012 sections
[FONT=arial]{ USB_DEVICE(0x0CF3, 0x0036) },
[/FONT][FONT=arial]{ USB_DEVICE(0x0CF3, 0x0036), .driver_info = BTUSB_ATH3012 },

The above two lines tell the vendor and device ID of Atheros bluetooth, can come from the output of lsusb:
[/FONT][FONT=arial]Bus 001 Device 012: ID 0cf3:0036 Atheros Communications, Inc.[/FONT][FONT=arial]

2- Rebuild the package and install. When you reboot, ath3k, and btusb drivers will be loaded.

3- Now you need to install the firmware. Get them from: You need both files. Once you get them, please strip the leading ar3k_ from the filenames, before copying. You can also look at comment #23 in: [/FONT][https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1219660](https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1219660)[FONT=arial]
[/FONT][FONT=arial]http://kernel.ubuntu.com/git?p=ubuntu/linux-firmware.git;a=blob;f=ar3k/AthrBT_0x31010000.dfu;h=935beb392a53979668bf7da5e4acb62ea7db80fe;hb=HEAD and [http://kernel.ubuntu.com/git?p=ubuntu/linux-firmware.git;a=blob;f=ar3k/ramps_0x31010000_40.dfu;h=ef3d79dce757751b47507074d9ef9da1b0ad35ed;hb=HEAD](http://kernel.ubuntu.com/git?p=ubuntu/linux-firmware.git;a=blob;f=ar3k/ramps_0x31010000_40.dfu;h=ef3d79dce757751b47507074d9ef9da1b0ad35ed;hb=HEAD) and put them into /lib/firmware/ar3k

4- Reboot and your bluetooth should work. Test it with
hcitool dev
hcitool scan

You still need to do a bit of work to autoconnect, etc.

Good luck.

[/FONT]

---

### Post by Homayoun_Shahri on 2013-09-30
Forgot to mention that it is a good idea to install the quantal package, as I was experiencing unpredicted freezes due to conflicts between video driver and kernel.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[COLOR=#333333][FONT=monospace]sudo apt-get install --install-recommends linux-generic-lts-quantal xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal[/FONT][/COLOR]

---

### Post by Homayoun_Shahri on 2013-09-30
The links to firmware file locations are broken above. Here are the correct links:

[http://kernel.ubuntu.com/git?p=ubuntu/linux-firmware.git;a=blob;f=ar3k/AthrBT_0x31010000.dfu;h=935beb392a53979668bf7da5e4acb62ea7db80fe;hb=HEAD](http://kernel.ubuntu.com/git?p=ubuntu/linux-firmware.git;a=blob;f=ar3k/AthrBT_0x31010000.dfu;h=935beb392a53979668bf7da5e4acb62ea7db80fe;hb=HEAD)[COLOR=#333333][FONT=Ubuntu Mono] and
[/FONT][/COLOR][http://kernel.ubuntu.com/git?p=ubuntu/linux-firmware.git;a=blob;f=ar3k/ramps_0x31010000_40.dfu;h=ef3d79dce757751b47507074d9ef9da1b0ad35ed;hb=HEAD](http://kernel.ubuntu.com/git?p=ubuntu/linux-firmware.git;a=blob;f=ar3k/ramps_0x31010000_40.dfu;h=ef3d79dce757751b47507074d9ef9da1b0ad35ed;hb=HEAD)

---

### Post by Abhishek_K._Pandey on 2013-10-15
That's awesome buddy. It has solved things, and my bluetooth devices are working like a charm now. Thanks a lot.. :D
I request admin to mark it as answer, as I can't see any option to do that myself..

---

### Post by Homayoun_Shahri on 2013-10-21
> **Abhishek_K._Pandey said:**
> That's awesome buddy. It has solved things, and my bluetooth devices are working like a charm now. Thanks a lot.. :D
I request admin to mark it as answer, as I can't see any option to do that myself..

Glad to hear that it all worked for you!

---

