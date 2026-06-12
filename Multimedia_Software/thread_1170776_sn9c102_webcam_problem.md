---
title: "sn9c102 webcam problem"
date: 2009-05-26
forum: Multimedia Software
---

### Post by fishwebby on 2009-05-26
Hello,

I'm having trouble getting my webcam working - I've read several other posts and tried many things, but still no luck (well a bit but not much)...

lsusb outputs the following:

```
Bus 002 Device 003: ID 0c45:6011 Microdia PC Camera (SN9C102)
```

[This page]("http://www.qbik.ch/usb/devices/showdev.php?id=2929") says that there is no driver available, but says if you go [here]("http://www.linux-projects.org/modules/mydownloads/singlefile.php?cid=7&lid=48") you can download a driver. I downloaded the sn9cxxx_2.13-1ubuntu1_i386.deb file from here, but when I try to install it, I get the message:

"Error: Dependency is not satisfiable: linux-image-generic (= 2.6.20.16.28.1)"

Not sure what that means or how to overcome it to be honest... I've installed v4l-conf (a suggestion from another post), which gives the output

```
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=0xcfffffff
/dev/video0 [v4l2]: no overlay support
```

When I try and run Canorama Webcam Viewer I get "Error - unable to capture image", however, as some other people have found, the camera does work in Ekiga (albeit just with red it seems). I'd like to get it working with Skype but I just get snow when I try and look at the webcam in there.

Does anyone have any ideas how I can try and get it working? Any help would be greatly appreciated!

Many thanks in advance
Dave

---

