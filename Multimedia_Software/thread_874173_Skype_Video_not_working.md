---
title: "Skype Video not working"
date: 2008-07-29
forum: Multimedia Software
---

### Post by lashi on 2008-07-29
G'day.

Anyone else had this problem with Skype video (2.0.0.72): 

[ 1660.951599] ioctl32(skype:10173): Unknown cmd fd(13) cmd(80685600){t:'V';sz:104} arg(f6355ff4) on /dev/video0
[ 1660.951876] ioctl32(skype:10173): Unknown cmd fd(13) cmd(803c7601){t:'v';sz:60} arg(f635605c) on /dev/video0


I'm running 2.6.22-14-generic, with Logitech WebCam, identified as: 
[ 1035.872873] Linux video capture interface: v2.00
[ 1035.898457] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[ 1036.475735] usbcore: registered new interface driver gspca
[ 1036.475741] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[ 1036.577139] usbcore: registered new interface driver snd-usb-audio


I'm on Heron Hardy 8.04, and I've tried camorama, and the cam works perfectly there. I'm on x86-64.

---

