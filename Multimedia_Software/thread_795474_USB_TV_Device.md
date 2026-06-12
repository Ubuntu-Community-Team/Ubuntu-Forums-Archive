---
title: "USB TV Device"
date: 2008-05-15
forum: Multimedia Software
---

### Post by rax_m on 2008-05-15
Hi all, 

So, I probably did a really silly thing by buying some generic usb TV device (Dany D-480i .. which I think uses Gadmei UTV380 hardware). 

Does anyone know how I can get this working under Ubuntu? 
I've installed tvtime but it can't see the device. 

Thanks
Rax

---

### Post by xc3RnbFO8P on 2008-05-15
First show the output of **lsusb** in Terminal

---

### Post by rax_m on 2008-05-18
Hi Ringi, 

Sorry for the slow reply, this weekend was a bit full.. 

Here's the output that is for the TV usb device:
```

Bus 005 Device 003: ID eb1a:50a3 eMPIA Technology, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Any ideas?

Thanks
Rax

---

### Post by xc3RnbFO8P on 2008-05-18
Try this:
[http://www.linuxforums.org/forum/ubuntu-help/111029-gadmei-utv-330-usb-tv-tuner.html]("http://www.linuxforums.org/forum/ubuntu-help/111029-gadmei-utv-330-usb-tv-tuner.html")

---

### Post by xc3RnbFO8P on 2008-05-18
delete (FF3b)

---

### Post by rax_m on 2008-05-18
Thanks.. I'm installing the required packages now. 

Hmm.. I just remembered I have a custom kernel for my sound and nvidia to work properly. Do you think compiling this module in will affect it?

Rax

---

### Post by xc3RnbFO8P on 2008-05-18
That I don't know, sorry.

---

### Post by rax_m on 2008-05-18
Well, I went ahead and installed the drivers, so far no side effects. 
However, I'm stuck with the following instructions from the post:

>  The em28xx accepts the parameter 'card=<n>' when it's loading, <n> is where you have to mention your device number from the driver device list. so my device is listed on 37th location in the list 


Do you an idea what driver list he might be referring to?

Cheers
Rax

---

### Post by xc3RnbFO8P on 2008-05-18
Just follow the instruction: 
> sudo modprobe em28xx card=37
Card <n> is 37

---

### Post by rax_m on 2008-05-19
I tried that, but it didn't work. I'm assuming because the device might be located at a different position on my hardware.

Guess I'll have to post a message on that forum. 

Cheers
Rax

---

### Post by xc3RnbFO8P on 2008-05-19
Show the output of **dmesg** in terminal

---

### Post by rax_m on 2008-05-22
sorry, been really busy at work and uni. I'll try and do this on the weekend. 

Cheers

---

### Post by rax_m on 2008-05-30
Hi

Sorry.. been bit hectic with work and university. 

The last bit of dmesg looks like this:

```
[ 8406.132000] usbcore: registered new interface driver snd-usb-audio
[ 8602.264000] Linux video capture interface: v2.00
[ 8602.320000] em28xx v4l2 driver version 0.0.1 loaded
[ 8602.320000] usbcore: registered new interface driver em28xx
[ 8652.632000] usb 5-2: USB disconnect, address 4
[ 8656.992000] usb 5-2: new high speed USB device using ehci_hcd and address 5
[ 8657.124000] usb 5-2: configuration #1 chosen from 1 choice
[ 8710.696000] usb 5-2: USB disconnect, address 5
[ 8748.892000] usbcore: deregistering interface driver em28xx
[ 8753.908000] Linux video capture interface: v2.00
[ 8753.928000] em28xx v4l2 driver version 0.0.1 loaded
[ 8753.928000] usbcore: registered new interface driver em28xx
[ 8763.424000] usb 5-2: new high speed USB device using ehci_hcd and address 6
[ 8763.556000] usb 5-2: configuration #1 chosen from 1 choice
rmistry@rmistry-laptop:~$ 


```

As you can see it doesn't show all of the lines as expected from the link you gave me earlier. 

Cheers
Rax

---

### Post by rax_m on 2008-05-30
Trying to run tvtime-scanner gives me:

```
 tvtime-scanner 
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/rmistry/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/rmistry/.tvtime/stationlist.xml: No existing PAL station list "Custom".
videoinput: Cannot open capture device /dev/video0: No such file or directory
rmistry@rmistry-laptop:~$ 

```

---

### Post by rax_m on 2008-06-01
bump

---

### Post by michaelAust on 2008-08-05
You could try following the steps in my thread

[http://ubuntuforums.org/showthread.php?t=869684](http://ubuntuforums.org/showthread.php?t=869684)

Your lsusb id is similar but not the same, maybe it will work.

---

### Post by rockstarsavin on 2010-06-04
I am also having similar problem?  I have bought a USB TV Box device  (Gadmei USB TV Box UTV 332E). But my ubuntu does not recognize it. While  it works perfectly on windows with its CD driver.

**I get nothing when i use [COLOR=DarkRed]lsusb[/COLOR] command.**

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Blue]Bus 001 Device 002: ID 1f71:3301  [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[SIZE=4][COLOR=Red]Please help !!!!!![/COLOR][/SIZE]

---

