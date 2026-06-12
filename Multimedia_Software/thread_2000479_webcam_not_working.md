---
title: "webcam not working"
date: 2012-06-09
forum: Multimedia Software
---

### Post by lo.j on 2012-06-09
hi all.

i got a microsoft vx-6000 webcam, perfectly working with my old ubuntu installation.
now, on my new 12.04 with kernel 3.2 it does not working anymore.

this is (the interesting part of) my .config:
```
$ cat .config | grep -P '=[ym]$' | grep -i -P 'sn9|gspca|v4l|video' | sort
CONFIG_ACPI_VIDEO=m
CONFIG_USB_GSPCA=m
CONFIG_USB_GSPCA_SN9C2028=m
CONFIG_USB_GSPCA_SN9C20X=m
CONFIG_USB_SN9C102=m
CONFIG_USB_VIDEO_CLASS_INPUT_EVDEV=y
CONFIG_USB_VIDEO_CLASS=m
CONFIG_V4L_MEM2MEM_DRIVERS=y
CONFIG_V4L_USB_DRIVERS=y
CONFIG_VIDEO_CAPTURE_DRIVERS=y
CONFIG_VIDEO_DEV=y
CONFIG_VIDEO_MEDIA=y
CONFIG_VIDEO_OUTPUT_CONTROL=m
CONFIG_VIDEO_V4L2_COMMON=m
CONFIG_VIDEO_V4L2=m
CONFIG_VIDEO_V4L2_SUBDEV_API=y

```

this is my system log when plugging in the webcam:
```
kernel: [ 1438.836015] usb 7-3: new high-speed USB device number 3 using ehci_hcd
kernel: [ 1438.970848] usb 7-3: New USB device found, idVendor=045e, idProduct=00f4
kernel: [ 1438.970852] usb 7-3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
kernel: [ 1438.970855] usb 7-3: Product: USB20 Camera                           
kernel: [ 1438.971138] gspca_main: sn9c20x-2.14.0 probing 045e:00f4
kernel: [ 1439.030469] gspca_sn9c20x: OV9650 sensor detected
kernel: [ 1439.030545] input: sn9c20x as /devices/pci0000:00/0000:00:1a.7/usb7/7-3/input/input9
kernel: [ 1439.143475] 3:2:1: cannot get freq at ep 0x84
```

i also attached a screenshot of:
```
sudo xawtv -c /dev/video0
```

what else should i check?

thank you for any help...

---

### Post by lo.j on 2012-06-11
could i provide any other useful info?

---

### Post by HansdeGoede on 2012-06-11
Hi,

There is a known regression in the gspca driver in the 3.2 kernels caused by new usb bandwidth-negotiation code in 3.2, this is fixed in 3.3 you should file a bug in launchpad, pointing out that the following commits should be backported to fix this:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=ac97ecc886472e97ff22a81c298163d180d24605](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=ac97ecc886472e97ff22a81c298163d180d24605)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=18bef42c2d9a63e028261b88e9202b6d0d34292b](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=18bef42c2d9a63e028261b88e9202b6d0d34292b)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=66957b864646e2ea0aebc66d1173f39a63509a19](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=66957b864646e2ea0aebc66d1173f39a63509a19)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=d0d3435b212f88aebee6a06e002e4fd3b487a918](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=d0d3435b212f88aebee6a06e002e4fd3b487a918)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=1153f04dea315a95e14ef5376737f7fbe18282c3](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=1153f04dea315a95e14ef5376737f7fbe18282c3)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=5dae603d84ff5b6b24186b521f4353b3860b11e2](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=5dae603d84ff5b6b24186b521f4353b3860b11e2)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=2d39059a656c0d0f61cfee8225f3d222dac7f3ac](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=2d39059a656c0d0f61cfee8225f3d222dac7f3ac)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=51e23be28418cf836287615cf78b237af13ea1b3](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=51e23be28418cf836287615cf78b237af13ea1b3)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=eb3fb7c9633f79077c7c650efe0edec1840926da](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=eb3fb7c9633f79077c7c650efe0edec1840926da)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=d80dd5d036147e00a27e3c649aec64bf9e572e9b](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=d80dd5d036147e00a27e3c649aec64bf9e572e9b)

Note the first 2 may already be in 3.2, I'm not sure, in that case they can be skipped :)

Regards,

Hans

---

### Post by lo.j on 2012-06-18
> **HansdeGoede said:**
> There is a known regression in the gspca driver in the 3.2 kernels caused by new usb bandwidth-negotiation code in 3.2

hans, you were right!
it takes me some time to make my tests and i can confirm that it works with 3.0.x and 3.4.x.

thanks a lot!

---

