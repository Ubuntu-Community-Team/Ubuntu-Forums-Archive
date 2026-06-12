---
title: "pwc recognizes Sotec Afina Eye instead of Philips"
date: 2009-05-12
forum: Multimedia Software
---

### Post by cudeso on 2009-05-12
Hi,

After the upgrade to Jaunty the pwc module does not recognize my Philips PWC720 webcam. Dmesg says :

```
[ 6693.560185] usb 1-3.5: new full speed USB device using ehci_hcd and address 6
[ 6695.381795] usb 1-3.5: configuration #1 chosen from 1 choice
[ 6695.400135] pwc: Sotec Afina Eye USB webcam detected.
[ 6696.573044] pwc: Registered as /dev/video0.
```

and lsusb
```
Bus 002 Device 002: ID 04cc:8116 Philips Semiconductors Camera
```

Nor camorama or amsn recognizes the webcam. Does anyone know how I can get pwc to recognize and use the philips drivers instead of those for sotec?

Thanks

---

