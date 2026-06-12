---
title: "Newer Logitech QuickCam for Notebooks doesn't work"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by argotnaut on 2007-06-19
FYI, I just bought a Logitech QuickCam for Notebooks (NOT the Pro model) because it seemed to be supported by the GSPCA driver. However, this newer model doesn't work. lsusb shows:

```
Bus 001 Device 003: ID 046d:08dd Logitech, Inc. 

```

It doesn't look like it's finding the built-in microphone, either -- I don't see any other devices here, and my ALSA mixer doesn't show anything but the built-in soundcard.

Back to the store it goes ... :/

---

### Post by shizow on 2007-11-21
i just bought the same camera
[http://www.logitech.com/index.cfm/notebook_products/webcams/devices/2989&cl=us,en](http://www.logitech.com/index.cfm/notebook_products/webcams/devices/2989&cl=us,en)

did anyone succed in installing it?
i searched the whole web
[http://thread.gmane.org/gmane.linux.drivers.quickcam.general/2661/](http://thread.gmane.org/gmane.linux.drivers.quickcam.general/2661/)
[https://answers.launchpad.net/ubuntu/+question/12072](https://answers.launchpad.net/ubuntu/+question/12072)
[http://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/002034.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/002034.html)

but there is no succes anywhere?

someone now send a camera to mxhard the programmer of GSPCA
[http://forums.quickcamteam.net/archive/index.php/thread-22.html](http://forums.quickcamteam.net/archive/index.php/thread-22.html)
[http://lists-archives.org/spca50x-devs/01305-need-help-with-a-new-logitech-webcam.html](http://lists-archives.org/spca50x-devs/01305-need-help-with-a-new-logitech-webcam.html)

so we have to wait!!

---

### Post by scottslinux on 2008-04-15
I have this camera and it is not supported by the gspca driver.  It works with cheese and works with problems in skyps.  The image is good in skype but then after several minutes it breaks down.  This can be fixed by stopping and starting the image with skype.  Hard to say if that problem is the linux-uvc driver or if it is a primary skype problem.

Went out and purchased a new camera that works very well under kubuntu with gspca.

 Re: Logitech QuickCam Communicate STX
Okay... I along with many others have been suffering from the incompatibility of linux and current webcams on the market. I am running kubuntu on a thinkpad 2.6.22-14 ... Embarrassed though I am I will admit that I have purchased three different webcams with miserable results. I installed the latest gspca driver and updated the linux-uvc driver. And still nothing..then I was given an old camera -a labtec by logitech and it functioned fairly well but with low resolution. There was hope...so with renewed enthusiasm I went back to the Ubuntu forum and found a post recommending the Logitech Quickcam Communicate STX ---which btw is avail now at best buy! The problem was that all of the old camera which were compatible are not currently for sale. The communicate STX is a new cam and avail now. It works flawlessly with camorama and skype though the former requires addition of color correction filter. easily done. Excellent microphone function. It jsut works completely!
Just wanted to pass this info on as it seems the end of a long journey and many here have helped me. Just giving back.

Thanks
Scott

---

### Post by andy80 on 2008-05-22
> **scottslinux said:**
> I have this camera and it is not supported by the gspca driver.  It works with cheese and works with problems in skyps.  The image is good in skype but then after several minutes it breaks down.  This can be fixed by stopping and starting the image with skype.  Hard to say if that problem is the linux-uvc driver or if it is a primary skype problem.

Went out and purchased a new camera that works very well under kubuntu with gspca.
Scott

I've just bought the same camera (046d:08dd) and: 

- it doesn't work with cheese
- it hangs Ekiga
- it works bad with skype too (after several minutes it breaks down).

I think I'll take it back to the shop too :(

Webcam support under Linux simply SUCKS! :(

p.s: I'm using Ubuntu 8.04 and this is the output when I plug it:

```
May 22 17:30:00 noteboontu kernel: [30833.002321] usb 1-2: new full speed USB device using uhci_hcd and address 2
May 22 17:30:00 noteboontu kernel: [30833.194563] usb 1-2: configuration #1 chosen from 1 choice
May 22 17:30:00 noteboontu kernel: [10873.225353] Linux video capture interface: v2.00
May 22 17:30:01 noteboontu kernel: [10873.304759] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
May 22 17:30:01 noteboontu kernel: [10873.308744] usbcore: registered new interface driver gspca
May 22 17:30:01 noteboontu kernel: [10873.308750] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
May 22 17:30:02 noteboontu kernel: [10873.520614] usbcore: registered new interface driver snd-usb-audio
May 22 17:30:19 noteboontu pulseaudio[6125]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
May 22 17:30:19 noteboontu pulseaudio[6125]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.

```

---

### Post by cilaes on 2008-07-21
same prob here... still no fix?

---

