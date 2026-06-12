---
title: "Logitech Quickcam Messenger webcam advice"
date: 2006-12-08
forum: Multimedia &amp; Video
---

### Post by chris_andrew on 2006-12-08
Hi, all.

I have just bought a Logitech Quickcam Messenger webcam.

Unfortunately, I have not been able to get any software to work with it.

The camera is seen as Logitech 046d:08da on Bus 001 Dev003.  I believe it ashould use driver spca5xx/LE.

uname -a:

Linux aslan 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

Any help would be most welcome.

Thanks,

Chris.

---

### Post by danielph on 2006-12-09
Mine is working "out of the box" - well at least I cant remember doing anything to get it working. 

Make sure the webcam is plugged in.

First install ekiga and see if it is working. Ekiga has a setup wizard which should detect the webcam

```
 sudo aptitude install ekiga  
```No  luck try

```
 dan[~]$ lsmod |grep quickcam
quickcam               75172  1 
videodev               10752  2 quickcam
usbcore               134912  6 snd_usb_audio,snd_usb_lib,quickcam,ehci_hcd,ohci_hcd

```If you cannot see it try 
```
modprobe quickcam
``` This will try and load the driver. try ekiga again

There is also an application called easycam2 which will detect and install your webcam. 

Last resort try:
  [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/), but I am pretty sure edgy has support for this camera and you shouldn't need to complile the module from source.

---

### Post by chris_andrew on 2006-12-09
quickcam wasn't listed under lsmod.  I modprobed quickcam, which seemed to work.  ow can I get quickcam to stay in mods, after this session?

BTW, Ekiga still doesn't see my device.  I'm hoping to sort the modprobe thing, reboot and see if the HAL picks it up.

Thanks,

Chris.

---

### Post by danielph on 2006-12-09
It should pick up the module on reboot and load it automatically. If it does not then you may need to edit /etc/modules and add "quickcam".

I have had problems with this webcam on other distros, but edgy and dapper both worked well. So, rest assured it can work. My only thought is that I may have a different model to you, so you may have to go down the source route after all.

mine is 
```
dan[~]$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

---

### Post by chris_andrew on 2006-12-09
I've just edited /etc/modules.  Will do a re-boot after a few jobs have finished, and see what happens.

Will let you know.

Thanks,

Chris.

---

### Post by budgie9 on 2006-12-09
My experience with this camera was more or less as yours.
I downloaded Easycam2, which got the correct drivers for me.
Then Camorama which shows the camera actually working with VL4 so something else was not correct with Ekiga.
In Ekiga I had to turn off the mic, which I did not need anyway, having a headset.
I also had to set the video channel in Ekiga to 0 before I could see any image.
I did download the ALSA mixer tools which allowed me to disable to audio from the camera. Then all worked fine.
Hope this helps youget you camera working.

---

### Post by chris_andrew on 2006-12-09
I added Easycam to my sources, but it kept falling-over.

I think I will build another PC, with a 2.6.18 kernel, that should support it.

Thanks,

Chris.

---

