---
title: "Share USB drive in Ubuntu Server?"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by j_freshman on 2010-12-21
I have a server with a shared internal drive (not the same one that the system is on) and a 500GB external hard drive that is connected via USB and used for backing up and archiving. Right now I have a somewhat lean GNOME setup so that I can use Webmin to share the external. Having a GUI running on the machine is pointless and a waste of memory, however, since it's headless. I just want a command line server that I can maintenance from my Windows 7 laptop with puTTY.

Could someone please describe for me how I would go about sharing the USB drive over my LAN without a GUI/Webmin?

Thanks!

---

### Post by slooow on 2010-12-21
Just mount it on the command line. Something like
```
sudo mount /dev/sdXX /mnt/<MOUNTPOINT_FOR_USB_DRIVE>
```
With 
```
dmesg | grep usb
```
you can find out where the USB drive is attached and replace the XX.
Since it is a server the usb drive is probably permanently attached. In this case I would add it to the /etc/fstab.

---

### Post by j_freshman on 2011-01-01
Thank you for your help! I've been beginning to delve into setting up samba, setting up a static IP, etc. with a standard ubuntu server installation and, now that i am ready to try this, i entered
```
dmesg | grep usb
``` and am not sure what I'm looking at. I understand that I'm being shown all references to USB devices, but I'm lost in it.


...Learning to ditch a GUI is frustrating, but I do like it.


EDIT: i attached a picture of the output
[IMG]http://lh5.ggpht.com/_Q2VEMjftoUc/TR-pmn-3UHI/AAAAAAAAAWc/vSRRZ6MyunU/downsized_0101111708.jpg[/IMG]

---

### Post by spiky001 on 2011-01-01
Try ```
sudo fdisk -l
```

---

### Post by j_freshman on 2011-01-01
thanks spiky! i'm still a long way from having this 'true' server be as functional as it was with GNOME (due to my unfamiliarity with CL,) but at least now i'm one step closer.

---

