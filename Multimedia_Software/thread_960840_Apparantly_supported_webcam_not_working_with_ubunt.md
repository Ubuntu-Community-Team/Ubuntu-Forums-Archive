---
title: "Apparantly supported webcam not working with ubuntu"
date: 2008-10-27
forum: Multimedia Software
---

### Post by iamlost on 2008-10-27
Hi,
I have just bought a webcam which i thought would work straight out of the box on ubuntu but it doesn't seem to work.
The webcam is a Technika one from Tesco.
I typed in lsusb and got: 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 093a:262a Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  

I'm hoping somebody can help me

---

### Post by knedlyk on 2008-11-16
I bought the same shi*&%t in Tesco and don't know what to do with it. Apparently we have to wait a positive answer from developers. I tried to make it work under Itrepid but it appeared that Intrepid is far from being ideal and has serious problem with libv4l libraries.  Currently there is an open bug [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918) . You can be lucky trying to make your camera work using latest libv4l libraries from [https://edge.launchpad.net/~lool/+archive](https://edge.launchpad.net/~lool/+archive) and start cheese, camorama or skype exporting LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so . Can you post your results here pls?

---

### Post by soldersplash on 2009-02-16
I have the same camera, ID 093a:262a Pixart Imaging, Inc., Technika from Tesco's. Initially the camera was not recognised at all. No /dev/video*, nothing in DMESG etc.. I followed instructions from here [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC) and now I have /dev/video0 and from DMESG :-

[22624.303385] usbcore: registered new interface driver uvcvideo
[22624.303807] USB Video Class driver (v0.1.0)
[22629.723261] usb 1-7: new full speed USB device using ohci_hcd and address 6
[22629.926608] usb 1-7: configuration #1 chosen from 1 choice
[22629.929569] gspca: probing 093a:262a
[22629.959055] gspca: probe ok

Thought camera would now work but test in Skype just gives green screen..
Test using luvcview shows garbage and the following output:
me@my-box:~$ luvcview /dev/video0 
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
 format asked unavailable get width 640 height 480 

Stop asked
 Clean Up done Quit 

Anyone got any ideas where from here?

(I am running Ubuntu desktop edition 8.04 32 bit x86, kernel is 2.6.24-23-generic)

---

### Post by knedlyk on 2009-02-18
Hello,

Finally I have made this camera work under intrepid. I have made the following steps:

1. Download and install libv4l from [https://edge.launchpad.net/%7Elool/+archive/ppa/+sourcepub/463709/+listing-archive-extra](https://edge.launchpad.net/%7Elool/+archive/ppa/+sourcepub/463709/+listing-archive-extra)

2. Next make sure that it works with cheese, camorama and skype:

$ LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so cheese
$ LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so camorama
$ LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so skype

Camorama doesn't work for me, cheese and skype work well.

3. Replace /usr/bin/skype:

$ sudo mv /usr/bin/skype /usr/bin/skype.orig
$ sudo mcedit /usr/bin/skype

Add the following lines to the new skype script:

#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype.orig &

Save and make it executable. Now you can start skype as usual. 

Hope it will help.

---

### Post by soldersplash on 2009-02-20
Hi knedlyk,
Yeah, hope it helps someone.....
I am sticking with Hardy for now so this doesn't help me.
The bug [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918) appears to relate to a newer kernel than is normal for Hardy. The libv4l package at "1. Download and install libv4l from https://edge.launchpad.net/%7Elool/+...-archive-extra" is for Intrepid and I am reluctant to try installing that to Hardy.

Any one else got any ideas for this in Hardy?

Iamlost (the OP), did you find anything out elsewhere or get anywhere at all with this?

Thanks all,

---

### Post by knedlyk on 2009-02-21
Hello, but [there is package for hardy]("https://edge.launchpad.net/~lool/+archive/ppa/") also:

```
deb http://ppa.launchpad.net/lool/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/lool/ppa/ubuntu hardy main
```


BTW, why you didn't try compile driver from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) ?

---

### Post by soldersplash on 2009-02-21
Hello knedlyk,
Thank you for posting this link but I followed it and can still only find Intrepid package. Do you think I am doing something wrong?

Thanks,

---

### Post by soldersplash on 2009-02-21
Hi knedlyk,
Just seen your edit re: Compile from mxhaard.
Have just downloaded src thanks.
Been a long day and I'm going to bed now.
Will try compile/install soon.
Thanks, will let you know how I get on.

---

### Post by soldersplash on 2009-02-22
Hi knedlyk (and anyone else who is reading..),

I have done the following now.
Got "gspcav1-20071224.tar.gz" as previously stated. - OK
Moved "gspcav1-20071224.tar.gz" to /usr/src/. - OK
Unpacked using "tar xvfz gspcav1-20071224.tar.gz". - OK
Had a look through source code for my camera's device ID, Not listed.
Added my cameras device ID to "gspca_core.c" in "static __devinitdata struct usb_device_id device_table[] = {" and added my cameras model number in "spcaDetectCamera(struct usb_spca50x *spca50x)". - OK, I think...
Ran "make". - OK, no error or warning messages.
Ran "sudo make install". - OK, no errors or warnings.
Check old "gspca" module not loaded. - OK.
Plug in camera and check "dmesg | tail", output follows.
[43019.039861] usb 1-7: new full speed USB device using ohci_hcd and address 3
[43019.243749] usb 1-7: configuration #1 chosen from 1 choice
[43019.427763] Linux video capture interface: v2.00
[43019.436961] gspca: disagrees about version of symbol video_devdata
[43019.436973] gspca: Unknown symbol video_devdata
[43019.437371] gspca: disagrees about version of symbol video_unregister_device
[43019.437375] gspca: Unknown symbol video_unregister_device
[43019.437520] gspca: disagrees about version of symbol video_device_alloc
[43019.437523] gspca: Unknown symbol video_device_alloc
[43019.437572] gspca: disagrees about version of symbol video_register_device
[43019.437576] gspca: Unknown symbol video_register_device
[43019.437840] gspca: disagrees about version of symbol video_usercopy
[43019.437843] gspca: Unknown symbol video_usercopy
[43019.437891] gspca: disagrees about version of symbol video_device_release
[43019.437895] gspca: Unknown symbol video_device_release
[43019.486597] gspca: main v2.4.0 registered
[43019.490324] gspca: probing 093a:262a
[43019.516577] gspca: probe ok
[43019.516875] usbcore: registered new interface driver pac7311
[43019.517103] pac7311: registered

Looks like the new "gspca" module gets loaded but with errors :(
,my camera is recognised  :)
,the right driver is loaded for it's chipset. :D

I try Ekiga just to see if any o/p from camera. Nope.
Ekiga gives error message on startup about USB device.

"dmesg | tail" has no new messages at this point.

Any ideas how to fix the "gspca: disagrees about version of symbol foo_bar" errors? :?

Cheers and thanks for interest,


Edit<
I tried the LD_PRELOAD=... from earlier post, it fails. I don't have v4l2. I see the following from "lsmod" exert follows:-
gspca_pac7311          11648  0 
gspca_main             25344  1 gspca_pac7311
videodev               44288  1 gspca_main
v4l1_compat            14852  1 videodev

I tried to use aptitude to get libv4l2 but nothing there from normal repositories.

Maybe this info is useful?
>/Edit

---

### Post by mehturt on 2010-01-06
Hello knedlyk,
is the .so to be preloaded v4l2convert.so or v4l2compat.so?
What I see in my Intrepid is v4l2convert.so.

---

### Post by frisket on 2010-06-07
> **mehturt said:**
> Hello knedlyk,
is the .so to be preloaded v4l2convert.so or v4l2compat.so?
What I see in my Intrepid is v4l2convert.so.

Has anyone ever got this camera to work in Karmic? I bought it a couple of years ago and it worked fine in Ubuntu 8.10 after I had added every webcam-related package I could find (eventually one of them must have contained the right library). But on "upgrade" to Karmic is seems that gspca support got dropped on the floor...

---

