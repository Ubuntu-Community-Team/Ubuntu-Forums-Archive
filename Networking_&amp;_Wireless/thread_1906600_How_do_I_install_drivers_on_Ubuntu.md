---
title: "How do I install drivers on Ubuntu"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by richztech on 2012-01-09
I have recently installed ubuntu on my pc and I am tryin to access the internet. My built in wireless card hasnt been working for quite some time now. So I bought a usb wifi thing. On the installation cd I have the linux drivers for it, the only problem is that I dont know how to install them. Please help.

---

### Post by TBABill on 2012-01-09
The easiest way may be to plug the USB device into the machine, open a terminal and type in ```
lsusb
```and provide the output back here for review (paste it here). That command is LSUSB in lowercase and it lists your USB devices. The chipset is what is important to determine what driver it needs and you may not need the driver on the CD at all, depending on the device.

---

### Post by richztech on 2012-01-09
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129  
 Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

---

### Post by richztech on 2012-01-10
Does that help? Or do you need more information?

---

### Post by TBABill on 2012-01-11
Can you open a terminal and try ```
sudo modprobe rt73usb
```If you get any errors please post them. If it still does not work can you enter ```
lsmod
``` and paste the output here.

---

### Post by IWantFroyo on 2012-01-11
Try plugging in an Ethernet cable and running the "Additional Drivers" application. This should get you the proper drivers.

I would advise against using the drivers that are on the disc, because there's no guarantee they will work. You can try installing them (first tell us what file type they are so we can help you) if Additional Drivers doesn't help.

---

### Post by TBABill on 2012-01-11
The RT73 driver is included in ubuntu without the need for additional drivers. I think this is a configuration problem...could be wrong.

---

### Post by IWantFroyo on 2012-01-11
> **TBABill said:**
> The RT73 driver is included in ubuntu without the need for additional drivers. I think this is a configuration problem...could be wrong.

Interesting. I didn't know that.

Did some Googling:
[s][http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/](http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/)[/s]

[s]This might fix it.[/s]

Edit: Wrong card type. Thank you, TBABill.

---

### Post by TBABill on 2012-01-11
That driver is not the correct driver for the device the OP listed! That link provides info for the RTL8192SU driver....has nothing to do with this card. > Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

---

### Post by IWantFroyo on 2012-01-11
> **TBABill said:**
> That driver is not the correct driver for the device the OP listed! That link provides info for the RTL8192SU driver....has nothing to do with this card.

My bad. Google brought up that result, and as I copied and pasted, I didn't recognize the difference.

Anyhow, finding out what types of files on the disc is probably the best thing to do right now.
If they are .deb files, you can use "sudo dpkg -i" or install via the Ubuntu Software Center. If they are a compressed format, like .bz2, you should uncompress it (it will make a copy by itself), and look for a .sh file.

---

### Post by richztech on 2012-01-12
Hello all, I appreciate all the help but nothing has worked so far. The type of file the driver is in is "tar.gz"

---

### Post by nothingspecial on 2012-01-12
Double click it and extract it. There **should** be either a README or INSTALL file in there with instructions.

---

### Post by richztech on 2012-01-12
Thats the problem, there is a read me pdf file that has windows and mac instructions but no linux instructions

---

