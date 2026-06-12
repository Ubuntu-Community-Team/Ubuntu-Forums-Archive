---
title: "How are Linux devices created? - webcam"
date: 2009-03-05
forum: Multimedia Software
---

### Post by Willem Ferguson on 2009-03-05
I have a Logitech E2500 webcam, NOT on the list of supported Linux webcam devices. There is an excellent website showing how to update the driver in order to get functionality ([http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/).The](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/).The) kernel module concerned is gspca.ko. Having done the modification and having installed the new version of gspca.ko, I cannot get a logical device associated with the module. Check the following procedute that I commented in capitals:

$ ls /lib/modules/2.6.24-23-generic/ubuntu/media/gspcav1/
gspca.ko                  # THE KERNEL MODULE IS THERE

$ sudo modprobe -v gspca  # NOW LOAD THE MODULE
insmod /lib/modules/2.6.24-23-generic/kernel/drivers/media/video/v4l1-compat.ko 
insmod /lib/modules/2.6.24-23-generic/kernel/drivers/media/video/v4l2-common.ko 
insmod /lib/modules/2.6.24-23-generic/kernel/drivers/media/video/videodev.ko 
insmod /lib/modules/2.6.24-23-generic/ubuntu/media/gspcav1/gspca.ko 

$ lsmod | grep gspca      # CONFIRM THAT IT IS LOADED
gspca                 643920  0 
videodev               29440  1 gspca
usbcore               146412  7 gspca,ndiswrapper,usbserial,hci_usb,ehci_hcd,uhci_hcd

$ ls /dev/video*          # BUT THERE IS NO ASSOCIATED LOGICAL DEVICE !!
ls: cannot access /dev/video*: No such file or directory

I understand too little to comprehend what the problem may be but it looks to me probably a basic lack of understanding of how Linux works.

I would appreciate any help. Kind regards.

---

