---
title: "Argos webcam not working  with camorama"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by madsmaddad on 2008-02-22
I have a cheap webcam from Argos. It is recogniz:(:(ed by gutsy:

 7911.397581] usb 2-2: new full speed USB device using ohci_hcd and address 2
[ 7911.607447] usb 2-2: configuration #1 chosen from 1 choice
[ 7911.702786] Linux video capture interface: v2.00
[ 7911.745788] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[ 7911.747165] usb 2-2: SN9C10[12] PC Camera Controller detected (vid:pid 0x0C45                                      :0x602A)
[ 7911.792101] usb 2-2: HV7131D image sensor detected
[ 7911.926947] usb 2-2: Initialization succeeded
[ 7911.926991] usb 2-2: V4L2 device registered as /dev/video0
[ 7911.926997] usb 2-2: Optional device control through 'sysfs' interface disabl                                      ed
[ 7911.927028] usbcore: registered new interface driver sn9c102


But Camorama says 'could not connect to video device /dev/video0. 

Can anyone advise me where the link is missing?

---

### Post by linuxwizard on 2008-02-22
Camorama does not support v4l2. Try using Ekiga. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

