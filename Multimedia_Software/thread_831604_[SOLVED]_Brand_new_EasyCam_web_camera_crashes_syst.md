---
title: "[SOLVED] Brand new EasyCam web camera crashes system"
date: 2008-06-17
forum: Multimedia Software
---

### Post by AndThenWhat on 2008-06-17
So, I just bought my girlfriend and I web cams from Target so we can communicate when she goes to Lebanon.  The thing is when I plug it in and try to use XawTV or anything else it crashes the whole system (Kernel Freezes I guess?).  Anyways, I am pretty sure this is because I need a driver for it, but I don't know where to get one.  (In case it is possible to extract the driver from CD I have the CD, but it is for Windows)

**lsusb:**

```
Bus 002 Device 002: ID 093a:2460 Pixart Imaging, Inc.
```

**dmesg:**

```
[ 1926.263345] usb 2-2: USB disconnect, address 2
[ 1928.018623] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 1928.083350] usb 2-2: configuration #1 chosen from 1 choice
[ 1928.085207] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. (PAC207)

```

Just FYI it says EasyCam For Desktop on the box and it is made by GE (General Electric) and the Model No: 98063 Rev. 3

---

### Post by AndThenWhat on 2008-06-17
Anybody?

---

### Post by brigit on 2008-06-20
I have the same webcam, or at lest the numbers match 093a:2460. I've not been able to get it working, although I've tried reinstalling the gspca driver which it looks like should work for it, as dmesg says USB GSPCA camera found. (PAC207), and this web sight [http://hardware4linux.info/component/28709/](http://hardware4linux.info/component/28709/) seams to think it should work for a similer cam, still no joy though. 
I'm running kubuntu 7.10, I've tested it useing skype, cheese, XawTV, & Camorama
Also see this page [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) where they say useng 7.04 "Using skype 2.0.0.27. Had to upgrade gspca driver to latest version to work. Also added options to /etc/modprobe.d/options to improve color. Options were: gamma=3, OffRed=32, OffBlue=0, OffGreen=32."

---

### Post by AndThenWhat on 2008-06-20
Okay, I solved the problem with my EasyCam.  Since your USB serial matches mine, that means we have the exact same version of the camera. 

What I did was compiled the source code that I have attached.  Then I installed aMSN and went into the "Edit Audio and Video Settings," which you can do by pressing CTRL+N.  After that, it just magically started working. 

(You may need to restart after compiling the source code)

---

### Post by witeczek on 2008-06-28
> **AndThenWhat said:**
> What I did was compiled the source code that I have attached.

What did you do here? The README says:

Trying a v4l app
================
goes to gspcagui directory
be sure to have libsdl installed with the header


There is no gspcagui in the attached file? Where I can take it from? (google did not help).

---

### Post by AndThenWhat on 2008-06-29
Just download the file that I attached and then "cd" to that directory in the terminal.  After that type the following in the terminal:

```

tar xvzf gspcav1-20071224.tar.gz
cd gspcav1-20071224
sudo make
sudo make install

```

---

### Post by willz06jw on 2008-10-19
Hmm strange when I do this it gives me an "error 2" when I try to make the source code

I am using Ubuntu Intrepid if that matters.

Thanks,
Will

---

### Post by woodenfox on 2008-11-23
The new updated file can be found in the Medibuntu repositorys for intrepid:  Just search Synaptic for GSPCA and the source is available to compile.

---

