---
title: "Problem with USB Logitech QuickCam video device"
date: 2010-11-24
forum: Multimedia Software
---

### Post by deesto on 2010-11-24
Just added an old Logitech QuickCam USB device to my 10.10 64-bit machine.  `lsusb` sees it:
```
Bus 001 Device 006: ID 046d:08f5 Logitech, Inc. QuickCam Messenger Communicate
```

The system sees it:
```
$ dmesg |grep -i STV
[   21.608447] STV06xx: Probing for a stv06xx device
[   21.608450] STV06xx: Configuring camera
[   21.608451] STV06xx: st6422 sensor detected
[   21.608452] STV06xx: Initializing camera
[   21.864698] input: STV06xx as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.3/input/input7
[   21.869233] usbcore: registered new interface driver STV06xx
[   21.869237] STV06xx: registered
```

The device light is on (blue), which makes me think things are working.  But I can't get an image from the device: everything either comes up black or throws an error.

This post:
[http://ubuntuforums.org/showpost.php?p=8505723&postcount=4](http://ubuntuforums.org/showpost.php?p=8505723&postcount=4)

... says using an older compatability mode should help:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
```

But this results in "Error: Unable to capture image."  What else can I try?

---

### Post by no2498 on 2010-11-24
see if it comes on in cheese

cheese webcam booth is the full name of it

look in sound&video if its installed


sudo apt-get install cheese

---

### Post by luca64bit on 2010-11-24
same problem. it doesn't work with cheese either. thanks in advance to the community

---

### Post by no2498 on 2010-11-25
ok try xawtv its in the repose

ive had to try both retry cheese

---

### Post by luca64bit on 2010-11-26
I'm sorry, but unfortunately it doesn't work.

---

### Post by deesto on 2010-12-03
> **no2498 said:**
> ok try xawtv its in the repose

ive had to try both retry cheese

Cheese sees the video device (/dev/video0) and allows me to use it to take a photo, but the photo comes out completely black.  Trying to record video seems to hang Cheese and the connection to the device is closed.

xawtv seems to do almost the same thing: finds the video device (displayed as STV06xx), takes black photos, won't record a movie ("error [init]").

---

### Post by no2498 on 2010-12-04
if your getting that far try diff programs
type webcam in the package manager
you can also test it in/with vlc media player

open vlc click media open capture device play

hope this helps

---

### Post by no2498 on 2010-12-04
try the preload for cheese

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by deesto on 2010-12-06
> **no2498 said:**
> try the preload for cheese

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheesePlease see my first post in the thread.

---

### Post by deesto on 2010-12-06
> **no2498 said:**
> if your getting that far try diff programs
type webcam in the package manager
you can also test it in/with vlc media player

open vlc click media open capture device play

hope this helpsThanks; I've got most of the "webcam" applications installed and have tried most of them, I think.

VLC doesn't have a pre-filled value for the capture device in the capture dialog.  When I plug in `/dev/video0` there I get:
```
Your input can't be opened:
VLC is unable to open the MRL 'v4l2:///dev/video0'. Check the log for details.
```

However, when I do this, Camera Monitor pops up and says that the camera is on, and it turns off when I close VLC.  I see this in `messages`:
```
Dec  6 08:53:27  kernel: [1034483.606071] gspca: found int in endpoint: 0x82, buffer_len=1, interval=16
Dec  6 08:53:27  kernel: [1034483.606711] gspca: found int in endpoint: 0x82, buffer_len=1, interval=16
Dec  6 08:53:27  kernel: [1034483.606717] gspca: bandwidth not wide enough - trying again
Dec  6 08:53:27  kernel: [1034483.630755] gspca: found int in endpoint: 0x82, buffer_len=1, interval=16
Dec  6 08:53:27  kernel: [1034483.631481] gspca: found int in endpoint: 0x82, buffer_len=1, interval=16
Dec  6 08:53:27  kernel: [1034483.631491] gspca: bandwidth not wide enough - trying again
```

---

### Post by deesto on 2010-12-06
Solved.  I had the camera plugged into a USB hub, and I guess Ubuntu/the kernel didn't like that.  I unplugged it from there and plugged it directly into a USB port, and all is well.  That was frustrating and kind of stupid, but at least the solution was simple. 	:rolleyes:

---

