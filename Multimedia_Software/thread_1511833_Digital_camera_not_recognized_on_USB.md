---
title: "Digital camera not recognized on USB"
date: 2010-06-17
forum: Multimedia Software
---

### Post by spmurphy on 2010-06-17
Previously I could plug my EOS 20D into the USB and f-spot would pop up and let me import photos. This was on 9.10. On a clean install of 10.04, it's as dead as a doornail and coughs the following into syslog:

```
Jun 17 14:45:38 simon-watery kernel: [ 1001.365978] usb 2-1.3.1.4: new high speed USB device using ehci_hcd and address 15
Jun 17 14:45:38 simon-watery kernel: [ 1001.501854] usb 2-1.3.1.4: configuration #1 chosen from 1 choice
Jun 17 14:45:38 simon-watery kernel: [ 1001.856874] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:38 simon-watery kernel: [ 1001.876874] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:38 simon-watery kernel: [ 1001.915624] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:38 simon-watery kernel: [ 1001.995625] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:39 simon-watery kernel: [ 1002.155611] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:39 simon-watery kernel: [ 1002.475612] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:40 simon-watery kernel: [ 1003.115525] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:41 simon-watery kernel: [ 1004.395630] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:43 simon-watery kernel: [ 1006.955903] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:45:49 simon-watery kernel: [ 1012.075732] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 64 rq 4 len 80 ret -110
Jun 17 14:46:20 simon-watery kernel: [ 1043.485630] usb 2-1.3.1.4: usbfs: USBDEVFS_CONTROL failed cmd f-spot rqt 192 rq 12 len 1 ret -110

```

If I spin up f-spot and try to import, it complains about corrupt data after a significant dead in the water type pause.

The camera is fine, it still does exactly what it did on the machine next to me which is still running 9 (or 8, I forget).

Has anyone seen this or got any suggestions as to how/where to fault find it?

---

### Post by spmurphy on 2010-06-22
bump, anyone else seen this?

---

### Post by philip5 on 2010-06-22
The EOS 20D (and most EOS cams) use the libgphoto2 lib on Linux for handling the communication with your camera. Why it worked before I don't know but try to update those libs and see if it helps. You have them on my PPA if you want the packages. For source code go to:  [http://www.gphoto.org](http://www.gphoto.org)

Hope this helps.

---

### Post by spmurphy on 2010-06-22
The versions numbers (installed to current) are different but I didn't see anything in the notes about fixes for this kind of problem, but it's worth a try.

Thank you

---

