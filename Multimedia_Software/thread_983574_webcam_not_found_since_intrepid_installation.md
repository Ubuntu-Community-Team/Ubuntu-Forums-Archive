---
title: "webcam not found since intrepid installation"
date: 2008-11-15
forum: Multimedia Software
---

### Post by rudeboyskunk on 2008-11-15
So I checked out the other threads on this topic, and it seems that for people in my particular situation there is no solution (or is there...?).

In Ubuntu Hardy, my generic webcam worked fine (I don't even know what type it is).  I plugged it in, and camera-monitor showed it to be working right away, it worked fine in cheese and skype and everything else, no problem, right out of the box, you get the idea.

Then I did a clean install of Intrepid.

No program will detect it.  Any program that would actually explain something just says "no device connected to /dev/video0" or something along those lines.

I tried my fiancee's webcam, a Logitech Quickcam, and it works great, but the quality is terrible (my webcam's quality is way better, despite being some generic thing with no name).

I've installed just about every package that all of the "linux webcam howto" manuals list, and nothing works.

Any ideas?

---

### Post by rudeboyskunk on 2008-11-16
*bump*

---

### Post by Berduchwal on 2008-11-16
I have the same issue!

I only used it in skype so nothing complicated but still.

It work out of the box and now it does not.
```

Nov 16 21:13:02 marcin-laptop kernel: [18033.020047] usb 4-1: new full speed USB device using uhci_hcd and address 2
Nov 16 21:13:02 marcin-laptop kernel: [18033.230165] usb 4-1: configuration #1 chosen from 1 choice
Nov 16 21:13:02 marcin-laptop kernel: [18033.581565] Linux video capture interface: v2.00
Nov 16 21:13:02 marcin-laptop kernel: [18033.605580] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
Nov 16 21:13:02 marcin-laptop kernel: [18033.606784] usb 4-1: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x0AC8:0x303B)
Nov 16 21:13:03 marcin-laptop kernel: [18033.683945] usbcore: registered new interface driver zc0301
```

It looks like it actually has driver loaded but still it can not be detected by skype.

this 8.10 is buggies realise every so far my webcam, microphone and graphic card stopped working properly this is dreadful.

I wish I could downgrade next time I will think twice before any "upgrade"

---

### Post by arunsub on 2008-11-16
I too have issues with my webcams with Ubuntu 8.10. I have a built in webcam in my laptop and a USB Logitech Quickcam in my desktop. Ubuntu 8.04 detected them correctly and gave the right name under the webcam list. Skype, AMSN etc worked perfectly and the quality was good. After I did a clean install of Ubuntu 8.10 in my laptop and an upgrade in my desktop, Ubuntu 8.10 shows both webcams as USB webcam, without the webcam name. AMSN doesn't recognizes the webcam. Skype works fine with the webcam, but the video is quite dark. I need to switch 4-5 lights on to get a decent brightness. I couldn't find a way to adjust the brightness. I'm not sure what went wrong with Ubuntu 8.10 and why it went backwards as far as webcam is concerned.

---

### Post by rudeboyskunk on 2008-11-19
*bump*

---

### Post by rhenium3 on 2008-11-23
I too am having a problem with this, is there any solution?  I want my webcam back :(

---

### Post by irtysh on 2008-11-25
I've got  0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam. It worked from the box on 8.04. but failed after upgrade to 8.10. I've found a solution here  

[http://janimo.blogspot.com/2008/11/making-vimicrozstara4tech-webcam-work.html]("http://janimo.blogspot.com/2008/11/making-vimicrozstara4tech-webcam-work.html")

Thanks to Janimo, saved me from downgrade. :) 

I did these steps (all as root!):
1) Install  moreutils package. It's in the repos
2) Add the line 
```
blacklist zc0301
```
 in the /etc/modprobe.d/blacklist file 
3) Add the line 
```
gspca_zc3xx
``` 
in the end of the /etc/modules file.
4) Run 
```
xxd /lib/modules/2.6.27-10-generic/kernel/drivers/media/video/gspca/gspca_zc3xx.ko |sed '/^000a370:/ s/1b30/3b30/' |xxd -r | sponge /lib/modules/2.6.27-10-generic/kernel/drivers/media/video/gspca/gspca_zc3xx.ko
```
If your kernel isn't 2.6.27-10 change it according to your kernel version.
5) Reboot.

The 4th step must be done after every kernel upgrade. Don't forget to change the kernel version in the code.

Both cheese and skype work flawlessly again!
Hope it'll help you too :)

---

### Post by kkady32 on 2008-11-26
sory but to me not work :((
Ubuntu Intrepid 64 Z-STAR ZC0303 Webcam

---

### Post by rg_stephens on 2008-11-26
Here's a solution to the brightness problem:

[http://forum.skype.com/index.php?showtopic=106357](http://forum.skype.com/index.php?showtopic=106357)

I can't get this code to work. I'm using the correct kernel version (I think) but it gives me the following error:

xxd: /lib/modules/2.6.24-21-generic/kernel/drivers/media/video/gspca/gspca_zc3xx.ko: No such file or directory
error opening output file: No such file or directory

---

### Post by irtysh on 2008-11-26
> **rg_stephens said:**
> Here's a solution to the brightness problem:

[http://forum.skype.com/index.php?showtopic=106357](http://forum.skype.com/index.php?showtopic=106357)

I can't get this code to work. I'm using the correct kernel version (I think) but it gives me the following error:

xxd: /lib/modules/2.6.24-21-generic/kernel/drivers/media/video/gspca/gspca_zc3xx.ko: No such file or directory
error opening output file: No such file or directory

Please check out your kernel version first:
```
uname -r
```
And then make sure you change it in both places in the code: in the beginning and in the 'sponge' command. 
As far as I remember 2.6.24 kernel was in Hardy. My webcam worked fine on Hardy without any problem. Intrepid started with 2.6.27-7 and the latest one is 2.6.27-10.
And you need to get root privileges to run the code. You can use sudo or just open root-terminal:
```
gksu /usr/bin/x-terminal-emulator
```
and run the code there.
Good luck!

---

### Post by rg_stephens on 2008-11-26
I ran the code and rebooted, but the video still doesn't work. I'm getting nothing but static on my webcam.

---

### Post by rudeboyskunk on 2008-11-27
Ran the code, rebooted, and it works great!  Thanks a ton.  Sucks that it'll have to be redone after every kernel upgrade, though.

---

### Post by irtysh on 2008-11-27
That guy, Janimo, he's sent his patch to kernel developers. Hope they'll fix the problem some day. This regression is really disappointing. 

> rg_stephens  	
I ran the code and rebooted, but the video still doesn't work. I'm getting nothing but static on my webcam. 

Are you sure your webcam is exactly 'ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam'? You can check it with 
```
lsusb
```

---

### Post by rg_stephens on 2008-12-01
I just rebooted in an older kernel, the camera works fine!! Guess I'll do this until the bugs get worked out.

> Are you sure your webcam is exactly 'ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam'? You can check it with 
```
lsusb
```

Actually it's not. I didn't really understand what I was doing. Here's the result:

beto@beto-laptop:~$ lsusb
Bus 004 Device 003: ID 106c:3711 Curitel Communications, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:0928 Logitech, Inc. Quickcam Express
Bus 001 Device 001: ID 0000:0000

---

### Post by El Viejo Lobo on 2009-02-22
I found out that no suggested solution worked for me, I tried lots of 
them. My way out is good but I have to reboot then click ESC   choose the other kernel no the one that is  th e first 2.6.27.xxx but the second one that is 2.6.24.xx
Any time that I whont to use my skype and the webcam I reboot in this way and have no problem. I am waiting to Ubuntu 9.04 to see this problem solved and hope that there will not be some new bug like this.

---

### Post by sadeghi on 2009-03-16
thanks for instructions, my zc0303 webcam now work in intrepid. but only in "webcam" application, i doesn't work in ekiga or skype(in skype it just shows flickering) or camocamara. Is there any way to have in working in skype and ekiga?

thanks in advance

---

