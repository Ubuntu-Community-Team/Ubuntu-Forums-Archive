---
title: "trust wb3420n not recognized"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by zielony on 2008-02-15
Hi,
I have a problem with my camera trust wb3420n.

when I plug it in and lsusb:
Bus 002 Device 007: ID 145f:013c 

So it is not recognized by system.. but I have tried to install gspca and modprobe it...
but with no results - /dev/video is not created :(

I have tried to edit gspca_core.c to add my camera there if 145f and 013c is plugged in.. but unfortunately it didn't worked.

Can anyone help?

---

### Post by linuxwizard on 2008-02-16
When you ran the command > lsusb > this was all you got > Bus 002 Device 007: ID 145f:013c > nothing else after the c ? Have you tried using the webcam with any appls. ? Like Ekiga see if it works/detected ?

---

### Post by zielony on 2008-02-17
lsusb before plugging the camera: (with only mouse plugged in)
```
zielony@R2D2:~$ lsusb 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 014: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

lsusb after plugging the camera:
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 016: ID 145f:013c  
Bus 002 Device 014: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

First I thought that it is a problem because system can't recognize what am I plugging in into usb (it is impossible to find the 145f:013c on the supported by usb devices list([http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids))).

But I found that it is quite easy to edit gspca_core.c (which is in gspca package([http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz))) to add there what should happened (which exactly module should be loaded and with what options) if 145f:013c is found.

I remember that few days ago it worked because if I did modprobe gspca and plugged in the camera and see what dmesg | tail is saying there was said that gspca module is using (and /dev/video and video0 and video1 were created(but camorama couldn't run because something was wrong with that /dev/video))... but today - I don't know why - it's not working....

p.s. of course in windows it is working.. I have an .exe file which is a driver to that camera... simply - I have sure that the camera is ok

---

### Post by linuxwizard on 2008-02-17
Searching around can't find anything on  Bus 002 Device 016: ID 145f:013c. To see what driver you may need. In your first post you didn't state that it did work could you see yourself and what app. were you using ? But you still don't know if you are using the correct driver for that cam. Have you tried using Ekiga to see if webcam works/detected ? You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by zielony on 2008-02-17
> In your first post you didn't state that it did work 
because it didn't work...
there was a time(few days ago) when I have done sth to the gspca_core.c and modprobe it and I was happy because when I plugged in the camera - dmesg show me that gspca driver is being used to work with that camera.. and then /dev/video was created but it didn't working (camorama won't start, ekiga didn't have /dev/video or anything else to choose..)

now ekiga is still telling me that there are not video devices to choose

p.s.linuxwizard - thanks for trying to help me - I have faith that we will figure it out :)

---

### Post by linuxwizard on 2008-02-17
When you open Ekiga are you getting any error messages ? If you go here >>Open Ekiga > Edit > Preferences > Video > Video Devices > Video Plugin can you change settings ?

---

### Post by zielony on 2008-02-17
I think that ekiga is not the key here - it is more important to have module (like modified gspca) which would be used when that camera is plugged in... dmesg | tail shows me only:
```
root@R2D2:/home/zielony/camera/gspcav1-20071224# dmesg | tail
[43296.284000] usb 2-2: new full speed USB device using uhci_hcd and address 44
[43296.520000] usb 2-2: configuration #1 chosen from 1 choice
[43296.800000] usb 2-2: USB disconnect, address 44
[43300.332000] usb 2-2: new full speed USB device using uhci_hcd and address 45
[43300.568000] usb 2-2: configuration #1 chosen from 1 choice
[43301.840000] usb 2-2: USB disconnect, address 45
[43303.844000] usb 2-2: new full speed USB device using uhci_hcd and address 46
[43304.072000] usb 2-2: configuration #1 chosen from 1 choice
[43304.360000] usb 2-2: USB disconnect, address 46
[43306.652000] usb 2-2: new full speed USB device using uhci_hcd and address 47

```



p.s. i really don't think that it is important... but here You have - my ekiga screenshot :)

---

### Post by linuxwizard on 2008-02-17
We are not working together very well. I ask questions not getting an answer I am trying to help you.  We don't even know if the driver is the correct one to use. Maybe someone else will offer some help & suggestions. Good Luck

---

### Post by zielony on 2008-02-18
> If you go here >>Open Ekiga > Edit > Preferences > Video > Video Devices > Video Plugin can you change settings ?
the answer is in the attachment in my previous post...
and the answer is NO - I can't change settings (it means I can't choose any video devices)...

---

