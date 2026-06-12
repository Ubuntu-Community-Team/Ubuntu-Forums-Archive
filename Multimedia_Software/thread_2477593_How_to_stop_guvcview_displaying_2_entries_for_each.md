---
title: "How to stop guvcview displaying 2 entries for each USB video device ?"
date: 2022-07-31
forum: Multimedia Software
---

### Post by elpidiovaldez5 on 2022-07-31
When I try to select a device in the guvcview video controls tab, I see a menu where there are two identical entries for each physical device.  Apparently selecting the first device of a given type results in video being displayed correctly, whereas selecting the second causes guvcview to hang.

I have a Logitech webcam and a USB Microscope.  It is the microscope that causes the problems - only a single instance of the webcam is in the device menu until I plug in the microscope, then both the webcam and microscope entries appear doubly.

I have googled the issue and now believe that the second entry is a virtual device giving meta data about the second (this [thread]("https://unix.stackexchange.com/questions/512759/multiple-dev-video-for-one-physical-device") gives an explanation). *v4l2-ctl* shows both devices:

```
paul@clio:~$ v4l2-ctl --list-devices
UVC Camera (046d:0994) (usb-0000:00:14.0-13):
        /dev/video0
        /dev/video1

Digital microscope: Digital mic (usb-0000:00:14.0-5.1.1):
        /dev/video2
        /dev/video3

```


I have two questions:

[LIST=1]
[*]Why do I only see the menu entries doubled up after I plug in the microscope ?
[*]Is there any way to prevent guvcview doing this annoying behaviour ?
[*]
[/LIST]

Many thanks.

---

### Post by #&amp;thj^% on 2022-07-31
> **elpidiovaldez5 said:**
> 

[LIST=1]
[*]Why do I only see the menu entries doubled up after I plug in the microscope ?
[*]Is there any way to prevent guvcview doing this annoying behaviour ?
[*]
[/LIST]

Many thanks.
The suggestion by"** beyOnd**" looked like a workable solution, from that same link you show

---

### Post by elpidiovaldez5 on 2022-08-02
I saw the suggestion by beyOnd, but I do not understand it.  I think he added a file to the */etc/udev/rules.d* folder called *99-cam.rules*.  In that file he put the text:

```
SUBSYSTEM=="video4linux", ATTRS{idVendor}=="eb1a", ATTRS{idProduct}=="299f", ATTR{index}=="0", MODE="0664", GROUP="video", SYMLINK+="cams/cam1"

SUBSYSTEM=="video4linux", ATTRS{idVendor}=="1908", ATTRS{idProduct}=="2311", ATTR{index}=="0", MODE="0664", GROUP="video", SYMLINK+="cams/cam2"
```

I don't understand where the hex numbers come from, or MODE 0664.  It seems to be creating the devices */dev/cams/cam1* and* /dev/cams/cam2* as symbolic links, but how will that stop guvcview finding the wrong devices.  Also will it break anything else ?

Sorry if that is a lot of questions, but the original suggestion seems aimed at people who are quite familar with the internals of Linux.

---

### Post by vifen on 2022-08-14
Hi, I wanted to know if you sound a solution for that ?

---

