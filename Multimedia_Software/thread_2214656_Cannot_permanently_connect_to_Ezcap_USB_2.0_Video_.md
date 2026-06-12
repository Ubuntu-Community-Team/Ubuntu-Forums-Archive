---
title: "Cannot permanently connect to Ezcap USB 2.0 Video Capture Device"
date: 2014-04-02
forum: Multimedia Software
---

### Post by peterthebike on 2014-04-02
I have an Ezcap USB 2.0 Video Capture Device and use it to connect to a webcam in a bird nestbox.

lsusb shows it as:
```
Bus 002 Device 002: ID eb1a:5124 eMPIA Technology, Inc.
```

The only way I can use the device is to:
```
sudo modprobe em28xx card=9
echo eb1a 5124 | sudo tee /sys/bus/usb/drivers/em28xx/new_id
```

Then I can use the webcam on /dev/video1.

Is there a way I can stop having to do the 2 commands above each time to use the webcam please?

---

