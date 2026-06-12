---
title: "Yet another Logitech Webcam problem. No /dev/video1"
date: 2009-04-20
forum: Multimedia Software
---

### Post by ncmncm on 2009-04-20
Hi all,

I am aware that there are several issues with the Quickcams. Read most of what is available on the net but still cant resolve this.


My USB Logitech Quickcam messenger STX is listed when I  type 

```
lsusb
```

> Bus 003 Device 005: ID 04cf:8819 Myson Century, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 0458:006a KYE Systems Corp. (Mouse Systems) 
**Bus 002 Device 004: ID 046d:08f5 Logitech, Inc. QuickCam Messenger **Communicate
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0430:0005 Sun Microsystems, Inc. Type 6 Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

However, it when I  type 

```
ls -la /dev/video*
```

I get>  crw-rw----+ 1 root video 81, 0 2009-04-20 07:55 /dev/video0

This is my Pinnacle PInnacle PCTV video card and Cheese correctly points it out.

Somehow my quickcam is not listed as a video. 
Can someone please help me configure this as  a video?

---

### Post by MaindotC on 2009-04-20
I'm not sure about configuring it because I use the Skype-approved webcam but can you try using a web service like uStream and see if it can properly interact w/ your cam?  It may be a work-around until you figure out the problem.

---

### Post by ncmncm on 2009-04-20
Still does not work !

---

### Post by MaindotC on 2009-04-20
Yikes - sorry to hear that.  Ok, well let's see if Ubuntu is naming it when you plug it in.  Remove the cam, open up your syslog, then plug in the cam and look for syslog to react.  Does it say anything about a new device being connected and a name for it?

---

### Post by ncmncm on 2009-04-20
> **strAlan said:**
> Yikes - sorry to hear that.  Ok, well let's see if Ubuntu is naming it when you plug it in.  Remove the cam, open up your syslog, then plug in the cam and look for syslog to react.  Does it say anything about a new device being connected and a name for it?

Looks like Logitech Quickcam Communicate (with built in Mic) is being recognised as a pure audio device
```

Apr 20 20:29:36 ubuntu kernel: [17660.536038] usb 3-3: new full speed USB device using ohci_hcd and address 5
Apr 20 20:29:36 ubuntu kernel: [17660.735077] usb 3-3: configuration #1 chosen from 1 choice
Apr 20 20:29:37 ubuntu pulseaudio[6171]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 22050 Hz.
Apr 20 20:29:37 ubuntu pulseaudio[6171]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
```

---

### Post by yahs on 2009-04-20
Hi,

I have a Logitech Quickcam STX, which works with 8.04, 8.10 and Jaunty.

I have posted my results below yours for the commands you ran

ls -la /dev/video*

Yours: crw-rw----+ 1 root video 81, 0 2009-04-20 07:55 /dev/video0

Mine:  crw-rw----+ 1 root video 81, 0 2009-04-20 21:11 /dev/video0

lsusb

Yours:  Bus 002 Device 004: ID 046d:08f5 Logitech, Inc. QuickCam Messenger Communicate

Mine:   Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX

My webcam is plugged into a USB port and I don't have a TV card.

Have you tried running gstreamer-properties from a terminal?

---

### Post by ncmncm on 2009-04-20
The  thing is, the webcam does not show up in the video device list. 
As mentioned in the first post, only the  Pinncale TV card shows up.

What should I do the  configure the webcam as a video device?

---

### Post by yahs on 2009-04-20
As my webcam gives this info

crw-rw----+ 1 root video 81, 0 2009-04-20 21:11 /dev/video0

I would have thought that 

crw-rw----+ 1 root video 81, 0 2009-04-20 07:55 /dev/video0

refers to your webcam???

Any chance you can temporarily disable your TV card and try again?

What happens when you run gstreamer-properties?

---

