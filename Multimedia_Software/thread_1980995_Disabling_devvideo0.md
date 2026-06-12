---
title: "Disabling /dev/video0"
date: 2012-05-16
forum: Multimedia Software
---

### Post by Lokie538 on 2012-05-16
Hello,

I have been looking around for a way to disable a video device through terminal. I have to webcams video0 and video1 which I need to disable through a script and re-enable at a later time.

Any suggestions?

Thanks in advance.

---

### Post by matt_symes on 2012-05-16
Hi

> **Lokie538 said:**
> Hello,

I have been looking around for a way to disable a video device through terminal. I have to webcams video0 and video1 which I need to disable through a script and re-enable at a later time.

Any suggestions?

Thanks in advance.

If it's a uvcvideo device then unload the uvcvideo module.

```
matthew@matthew-Aspire-7540 ~ % ls /dev/vid*
/dev/video0
matthew@matthew-Aspire-7540 ~ % sudo modprobe -r uvcvideo
[sudo] password for matthew: 
matthew@matthew-Aspire-7540 ~ % ls /dev/vid*             
zsh: no matches found: /dev/vid*
matthew@matthew-Aspire-7540 ~ % sudo modprobe  uvcvideo 
matthew@matthew-Aspire-7540 ~ % ls /dev/vid*           
/dev/video0
matthew@matthew-Aspire-7540 ~ %
```

That is one way for a uvc compatible video device.

Kind regards

---

### Post by Lokie538 on 2012-05-16
Thanks for the reply.

What about if the device is in use and I only want to disable one of the two video devices?

Sorry to be a pain.

---

### Post by matt_symes on 2012-05-16
Hi

What exactly do you mean by disable ?

You can find out what has a lock on a video device node using lsof and terminate that program.

Kind regards

---

### Post by Lokie538 on 2012-05-16
> **matt_symes said:**
> Hi

What exactly do you mean by disable ?

You can find out what has a lock on a video device node using lsof and terminate that program.

Kind regards

Ok ill give you a quick run down on what Im trying to achieve and why. I have got zoneminder installed and its monitoring an IP camera and 2 web-cams. One of these web-cams is in my bedroom, where I don't want it to be functioning while I am home (as its my bedroom). So basically I want to create a perl script that checks if my phone or laptop is ping-able on the local network and if it is, turn one of the two webcams off.

I had a look at some zone minder documentation and couldn't find a command to just turn a monitor off, so now I am investigating how to disable one of the two webcams through ubuntu itself.

Any help towards my goal would be appreciated, but I will continue my search on google in the meanwhile.

---

### Post by matt_symes on 2012-05-16
Hi

What about unbinding the USB driver from the webcam ?

I do not know whether this will work with a webcam but you should be able to test it quickly. I am also not sure how it will affect zoneminder as i have never used it.

You can find the devices using the uvcvideo driver with....

```
ls -l /sys/bus/usb/drivers/uvcvideo/
```

That is a small L above.

Here is mine. I have one webcam highlighted with 2 functions.

```
matthew@matthew-Aspire-7540 ~ % ls -l /sys/bus/usb/drivers/uvcvideo/                        
total 0
[COLOR="Red"]lrwxrwxrwx 1 root root    0 May 16 17:25 2-5:1.0 -> ../../../../devices/pci0000:00/0000:00:13.2/usb2/2-5/**2-5:1.0**
lrwxrwxrwx 1 root root    0 May 16 17:25 2-5:1.1 -> ../../../../devices/pci0000:00/0000:00:13.2/usb2/2-5/**2-5:1.1**[/COLOR]
--w------- 1 root root 4096 May 16 17:24 bind
lrwxrwxrwx 1 root root    0 May 16 17:22 module -> ../../../../module/uvcvideo
--w------- 1 root root 4096 May 16 17:22 new_id
--w------- 1 root root 4096 May 16 17:22 remove_id
--w------- 1 root root 4096 May 16 16:55 uevent
--w------- 1 root root 4096 May 16 17:24 unbind
matthew@matthew-Aspire-7540 ~ %
```

The bus identifiers are highighted in bold.

Unbind the device from the driver module with

```
echo '2-5:1.0' | sudo tee /sys/bus/usb/drivers/uvcvideo/unbind
```

and rebind the device with

```
echo '2-5:1.0' | sudo tee /sys/bus/usb/drivers/uvcvideo/bind
```

You will have a adjust yours with the correct bus identifier.

Kind regards

---

