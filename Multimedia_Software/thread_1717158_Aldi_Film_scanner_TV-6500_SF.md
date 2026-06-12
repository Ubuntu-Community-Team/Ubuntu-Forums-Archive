---
title: "Aldi Film scanner TV-6500 SF"
date: 2011-03-29
forum: Multimedia Software
---

### Post by Vicb on 2011-03-29
Hi, I'm a complete newbie... and not too technical. I've bought a Film scanner from Aldi, Called a "traveller TV-6500 sf" It comes only with windoze drivers.  Can anyone help me make it work on Linux. I have Ubuntu 11.04. All up to date! :-) I have Xsane installed, which works fine with my flatbed scanner. It does not even "see" the film scanner. It's plugged into a usb port(tried several) and lights up, so assume that the hardware is ok.

Any help, much appreciated.

Vic

---

### Post by MattTastic on 2011-03-29
> **Vicb said:**
> Hi, I'm a complete newbie... and not too technical. I've bought a Film scanner from Aldi, Called a "traveller TV-6500 sf" It comes only with windoze drivers.  Can anyone help me make it work on Linux. I have Ubuntu 11.04. All up to date! :-) I have Xsane installed, which works fine with my flatbed scanner. It does not even "see" the film scanner. It's plugged into a usb port(tried several) and lights up, so assume that the hardware is ok.

Any help, much appreciated.

Vic

Hey Vic, bought the same one myself just a few hours ago for my Mom for mothers day. I just plugged it in to see if it worked on the off chance. It isn't recognise automagickally but these things rarely are.

All I can add to this is the terminal output, it's gonna be pretty similar for you...

> 
Bus 001 Device 004: ID 0ac8:3370 Z-Star Microelectronics Corp.


Which of course tells us absolutely nothing really. I'm not sure where to start with this one really myself, so I suppose we'll have to wait and see what other people recommend.

---

### Post by MattTastic on 2011-03-29
Funny story, I happened on this web article after booting into windows...

[http://www.theinquirer.net/inquirer/news/1047633/one-writes-linux-drivers-235-usb-webcams](http://www.theinquirer.net/inquirer/news/1047633/one-writes-linux-drivers-235-usb-webcams)

There is one interesting quote
> 
After finding the chipset used by the webcam and writing to both the chipset manufacturer and the webcam builder and receiving no reply whatsoever, I was on my own. I asked on the newsgroups, and was told that the ZC0301 chipset, manufactured by "Z-Star Corp" -a firm now apparently going by the name Vimicro Corp- was on the "Linux (in)compatibility list".

Read more: [http://www.theinquirer.net/inquirer/news/1047633/one-writes-linux-drivers-235-usb-webcams#ixzz1I1wQGAtK](http://www.theinquirer.net/inquirer/news/1047633/one-writes-linux-drivers-235-usb-webcams#ixzz1I1wQGAtK) 
The Inquirer - Computer hardware news and downloads. Visit the download store today.


---

### Post by tferenc on 2011-03-30
I spotted this French page  [http://forum.ubuntu-fr.org/viewtopic.php?id=432181]("http://forum.ubuntu-fr.org/viewtopic.php?id=432181")

Checking syslog I see the following lines

uvcvideo: Found UVC 1.00 device 338 Camera (0ac8:3370)
uvcvideo: No streaming interface found for terminal 3.
input: 338 Camera as /devices/pci0000:00/0000:00:02.2/usb1/1-3/1-3:1.0/input/input6

Does this help anyone? I am still investigating

---

### Post by gpokorny on 2011-03-31
Hi, I have bought the the same "scanner" today, and I found out that it is in fact not a scanner but a webcam, hence Simple Scan or xane won't work. I got it running with Cheese. You can scan your dias by shooting photos with Cheese. My Ubuntu 10.04LTS detects the webcam without any additional driver installation. In the Cheese preferences I have selected the device "338 Camera" and I can also change the resolution there. I hope this info helps!

---

### Post by gaboro on 2011-04-01
Hiya,

I also have this scanner, it will be recognised as a webcam w/o a problem.
But the picture shows up in blue. Could someone recommend a setting for cheese to have the right colours? I have played along with the settings but no optimal solution found yet.

---

### Post by MattTastic on 2011-04-01
Well ride me sideways, it's a webcam. Who would of thunk it.

---

### Post by Vicb on 2011-04-03
Thank you for your help.

All works. :-)

---

### Post by Vicb on 2011-04-03
> **gaboro said:**
> Hiya,

I also have this scanner, it will be recognised as a webcam w/o a problem.
But the picture shows up in blue. Could someone recommend a setting for cheese to have the right colours? I have played along with the settings but no optimal solution found yet.

Yeah, I have that too. Was just going to play with it in Gimp, but that would be a pain as I have about 300 of 'em to do! So if anyone can come up with a simple and easy way of setting it up to work, I'd be grateful.

Vic

---

### Post by Vicb on 2011-04-03
> **Vicb said:**
> Yeah, I have that too. Was just going to play with it in Gimp, but that would be a pain as I have about 300 of 'em to do! So if anyone can come up with a simple and easy way of setting it up to work, I'd be grateful.

Vic

Also, the image seems a little blurry.. Is that a limitation of the device ?

---

### Post by nobody23 on 2011-04-09
I think, I know why its blurry. 
I also tested the device on a windowsxp and therefore you can install a program. this calibrates the scanner. so the pictures are not blurry anymore and the colors fit too.

anyone an idea how to calibrate the device on ubuntu 10.10?

---

### Post by GrandTheft on 2011-12-15
Hereby reviving this thread.

Has anyone found a solution to calibrate the thing under linux?

Best regards,
gt

---

### Post by hashimoto on 2011-12-18
> **GrandTheft said:**
> Hereby reviving this thread.

Has anyone found a solution to calibrate the thing under linux?

Best regards,
gt

Since it is a webcam in principle, maybe the following could help:
[http://www.techytalk.info/webcam-settings-control-ubuntu-linux/](http://www.techytalk.info/webcam-settings-control-ubuntu-linux/)

---

### Post by quietpinguin on 2012-01-21
I have a HAMA slide/negative scanner that has the same linux kernel registration as the Aldi device.

[SIZE=-1][FONT=sans-serif]Applications such as cheese, qtv4l2test utility, etc..         only show the blue (or is it cyan) channel...

Has, anyone solved this problem when using the Aldi film scanner?
        
        Output from demsg is:
        [11606.340366] usbcore: registered new interface driver uvcvideo
        [11606.340370] USB Video Class driver (1.1.1)
        [11615.475060] usb 2-1: new high speed USB device number 10         using ehci_hcd
        [11615.632870] usb 2-1: New USB device found, idVendor=0ac8,         idProduct=3370
        [11615.632874] usb 2-1: New USB device strings: Mfr=1,         Product=2, SerialNumber=3
        [11615.632878] usb 2-1: Product: 338 Camera
        [11615.632880] usb 2-1: Manufacturer: Vimicro Corp.
        [11615.632882] usb 2-1: SerialNumber: MI1320_SOC
        [11615.644454] uvcvideo: Found UVC 1.00 device 338 Camera         (0ac8:3370)
        [11615.647265] input: 338 Camera as         /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/input/input17[/FONT][/SIZE]

---

### Post by quisnox on 2012-08-25
I have Hama Slide/Film scanner too. Currently running Windows, but planning to move to Linux (Debian or Ubuntu).

What's new here? Does this ****** scanner work in newest Ubuntu 12.04.1 LTS ?

---

### Post by quisnox on 2012-09-07
Bump!

It's importatnt :/ I need to scan my negatives

---

### Post by oldos2er on 2012-09-07
Please start a new thread: "If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

