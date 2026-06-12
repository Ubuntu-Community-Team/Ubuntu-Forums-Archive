---
title: "USB DAC not recognized"
date: 2014-01-16
forum: Multimedia Software
---

### Post by Ruben_Henriksen on 2014-01-16
Hi, I am running Kubuntu 13.10 (64 bit), and I'm trying to get an NAD USB DAC working.

By running the command "lsusb" in the terminal with and without the DAC connected, I found that the DAC is listed as:
Bus 004 Device 003: ID 17ae : 0004

Do anyone have suggestions to what I should try to get this DAC working? There is a Windows driver available for this, I assume this won't be of any help.


Thanks for any help!

---

### Post by Bucky Ball on 2014-01-16
*Thread moved to **Multimedia & Video**.*

You might have more luck here.

I have subscribed to this thread and will watch with interest as, though I can't really help you, I am currently asking similar questions about a Digidesign Mbox 2 Mini on another thread. Good luck. ;)

---

### Post by Ruben_Henriksen on 2014-01-20
Thanks Bucky Ball :)

I did some more research and found this at NAD's webpage:[INDENT]**FOR MAC USERS**

[COLOR=#686868][FONT=Helvetica]Minimum Mac OS X Snow Leopard (version 10.6) and later versions include USB Audio 2.0 drivers and therefore it is not necessary to install the NAD USB 2.0 Audio driver. Ensure the Sound device of your Mac is set to "NAD USB Audio 2.0"
[/FONT][/COLOR]

[/INDENT]
Perhaps this might be useful to solve this problem. From what I know, osx is unix based, so perhaps the same driver is made for ubuntu? I have not been able to find this driver, but I'm not experienced in looking for linux drivers.
If there is no linux driver available, I think the osx driver should be more similar to what I need than the windows driver, and I might attempt to adapt this driver if necessary to get this working.

---

### Post by Yellow Pasque on 2014-01-20
Windows or Mac drivers are of no help...

The best place to ask if the kernel supports this device is here: [https://lists.sourceforge.net/lists/listinfo/alsa-user](https://lists.sourceforge.net/lists/listinfo/alsa-user)

---

### Post by Bucky Ball on 2014-01-20
Do you know the exact model of the device? I looked for the USB id but didn't turn up anything.

---

### Post by Ruben_Henriksen on 2014-01-21
The device is a NAD MDC DAC 2 ( [http://nadelectronics.com/products/hifi-mdc-modules/MDC-DAC-2](http://nadelectronics.com/products/hifi-mdc-modules/MDC-DAC-2) ).
I will try to ask at alsa about the kernel support, if I have to go deep into the problem to solve this, then it will probably be some time until I have enough free time.

---

### Post by Ruben_Henriksen on 2014-01-21
I was able to get the device working :D

By looking closer in the console, I discovered that the command "~$ cat /proc/asound/cards" returns[INDENT]0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 SB073x
 1 [Audio          ]: USB-Audio - NAD USB Audio
                      NAD Electronics NAD USB Audio at usb-0000:00:1a.1-1, full speed[/INDENT]
This made me believe that the problem might not be a driver, "lsubs -t" reveals that the device uses the driver "snd-usb-audio". This made me search for problems related to configuring a sound device instead, I found that "pactl stat" returns another unit as default sink, "pactl list sinks" returns a list of devices that include the one I want to use, so using "pacmd set-default-sink" I was able to change to the correct device.

This was sufficient to get the device working, but it still does not show up in the audio hardware setup.


Thanks for all help on this problem!

---

