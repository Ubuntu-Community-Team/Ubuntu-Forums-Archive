---
title: "Webcam"
date: 2005-11-23
forum: Multimedia &amp; Video
---

### Post by sp_ubuntulinux on 2005-11-23
Ubuntu is detecting my webcam automatically but Gnome meeting isn't displaying live video feed from my webcam. Any ideas? Please help.:???: :confused:

---

### Post by Teroedni on 2005-11-23
Can you name the brand and model?

Where does you see that ubuntu regognice your card . Does ubuntu state your webcam in hal or lshw?.

---

### Post by sp_ubuntulinux on 2005-11-23
I have Logitech Quickcam Messenger.

The output displayed when I enter lshw is as follows-

*-usb
                   description: Audio device
                   product: Camera
                   vendor: Logitech, Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-2.00 audio-control
                   configuration: driver=snd-usb-audio maxpower=100mA speed=12.0MB/s

The output displayed when I enter lsusb is-

Bus 001 Device 003: ID 046d:08f0 Logitech, Inc.

So Ubuntu is detecting it but it dosen't work in any of the programs which use a webcam.:???: :???: :???: :???: :confused: :confused: :confused: :confused:

---

### Post by gentoo42 on 2005-11-23
I have a logitech communicate stx(i think) webcam, it shows up as the same thing, i think this is just linux detecting the usb audio portion of it, i.e. the microphone in the camera.  the actual camera part probably needs drivers of some sort.  i haven't looked into it much yet.  you might check this thread:
[http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+webcam](http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+webcam)

---

