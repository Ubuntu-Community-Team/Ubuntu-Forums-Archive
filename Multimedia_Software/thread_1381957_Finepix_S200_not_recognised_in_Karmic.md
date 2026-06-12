---
title: "Finepix S200 not recognised in Karmic?"
date: 2010-01-15
forum: Multimedia Software
---

### Post by Robbyx on 2010-01-15
I am trying to download my pictures from this digital camera. I can see that the proceedure should be:


   1. Created a new mount point: $ sudo mkdir /mnt/camera
   2. Mounted the camera: $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000

My camera is not on /dev/sda1. How do I find where it is? I have looked in nautilus at /dev but I can not tell which entry is receiving the camera.

Is there a command that will tell me what entry has opened as a result of connecting the camera to the usb port? If not what should I do. Fuji have just written to me to say: Unfortunately we do not guarantee that our camera will work with Ubuntu Karmic 9.1 (Linux), nor do we have any drivers available for this computer.

---

### Post by Robbyx on 2010-01-15
It seems that the camera is not being recognised because there was no difference shown up by the following:

# unplug the camera, then
dmesg > /tmp/without

# plug the camera in, then
dmesg > /tmp/with

# see if it's recognized
diff /tmp/with /tmp/without

Does anyone have a solution to a not recognised camera? The camera screen does say that it is connecting to USB.

---

### Post by Robbyx on 2010-01-15
I hope this is not going to be overlooked. Has anyone found a way to recognise the camera?

---

### Post by Robbyx on 2010-01-16
As no one has replied I have for the record used a card reader to transfer the files.

---

