---
title: "Connecting photo camera through usb"
date: 2017-11-18
forum: Multimedia Software
---

### Post by karel2 on 2017-11-18
Formerly, when I plugged USB into my Nikon 5700, there was created a pseudo-disk for it. /dev/sdc or such; and I could *mount /dev/sdc1 /mnt_pictures* or such and all was fine.
Now, instead, I am greeted by a pop-up that allows to either "Open with Files" or "Eject". Now I am a command-line guy so I do not like to handle my pictures through this gui thingy. But I could live with it, except for the fact that, when approaching the pictures on the camera through the file manager, I cannot even remove them. Apparently due to a lack of rights.

How can I get Ubuntu (still at 14.04.5, but religiously patched) back to its previous behaviour?

Apologies if the matter was already discussed, pointers welcome.

---

### Post by karel2 on 2017-11-18
Some additional info: when I plug in the camera, this comes up in /var/log/syslog:

Nov 18 21:01:39 wiske kernel: [116461.786528] usb 2-1.6: new high-speed USB device number 20 using ehci-pci
Nov 18 21:01:39 wiske kernel: [116461.880626] usb 2-1.6: New USB device found, idVendor=04b0, idProduct=022e
Nov 18 21:01:39 wiske kernel: [116461.880631] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 18 21:01:39 wiske kernel: [116461.880634] usb 2-1.6: Product: NIKON DSC COOLPIX P610
Nov 18 21:01:39 wiske kernel: [116461.880637] usb 2-1.6: Manufacturer: NIKON
Nov 18 21:01:39 wiske kernel: [116461.880639] usb 2-1.6: SerialNumber: 000040004808
Nov 18 21:01:39 wiske mtp-probe: checking bus 2, device 20: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6"
Nov 18 21:01:39 wiske mtp-probe: bus: 2, device: 20 was not an MTP device
Nov 18 21:01:39 wiske colord: Device added: sysfs-NIKON-NIKON_DSC_COOLPIX_P610
Nov 18 21:01:39 wiske colord: Device added: sysfs-(null)

---

### Post by kainblock on 2017-11-18
Thats a GUI Solution but you will use GUI one last time and after that auto mounting will stop. 
[https://askubuntu.com/questions/89244/how-to-disable-automount-in-nautiluss-preferences](https://askubuntu.com/questions/89244/how-to-disable-automount-in-nautiluss-preferences)

---

### Post by karel2 on 2017-11-19
Hm. Thanks - but I do not want auto-mounting to stop, I want it to begin!
That said, I looked into editing the "dconf" both through the GUI and from the command line. The options referred to in that link are not present.

---

### Post by shantiq on 2017-11-20
maybe [read the answers here]("https://unix.stackexchange.com/questions/52054/mounting-usb-camera-on-ubuntu") Karel


PS   to modify your fstab
```
sudo gedit /etc/fstab
```

Looks like you need to add first 2 line here then run &#10124; in your terminal:

&#10122; ```
 usbdevfs  /proc/bus/usb  usbdevfs  devmode=0666,noauto 0 0
```

&#10123; ```
 /dev/sda1 /media/usb auto rw,user,noauto 0 0
```

* then mount the camera by issuing*

&#10124; ```
 mount /dev/sda1
```


*I have not tried this myself as i use a camera on an iphone which is a different story* but it looks as this might work ...

---

### Post by Holger_Gehrke on 2017-11-20
The messages from the log read like the camera is not set up as a mass storage device. Check the USB settings on the camera. If it's set to PTP (Picture Transfer Protocol), then that's the reason it doesn't get mounted. You can transfer pictures from a camera using PTP in programs that use libptp like gphoto, but if you want to just mount the camera and copy the files it needs to be set to mass storage.

Holger

---

### Post by acefromspace on 2017-11-22
Another way is to use a usb card reader. Remove the storage card from camera and insert it into the card reader. Not what you asked for, but that's how I do it.

---

