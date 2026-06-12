---
title: "Webcam not working in Quantal (Lenovo S10-2)"
date: 2013-03-04
forum: Multimedia Software
---

### Post by neonihilist on 2013-03-04
Hi, 

I recently installed Ubuntu 12.10 on the Gnome3 desktop environment. My webcam was working fine during the Ubuntu installation when it asked me to be snapped by my webcam or choose a picture instead. 

However, the webcam does not show on Skype 4.1.10, which i installed earlier today. The VIDEO DEVICE tab in skype options does not detect a webcam. Neither does Cheese and shows a blank screen. 

I don't even know if correct drivers for my cam are installed or not. Gnome3 does not have "hardware" in system settings and I cannot find any way to install additional hardware drivers.

I have a Lenovo S10-2 netbook with the following specs:

Intel® Atom™ CPU N280 @ 1.66GHz × 2 
Ram: 993.4 MiB
Graphics: unknown (On board?)
Ubuntu Partition: 14 GB
OS type: 32 bit

typing lsusb in the terminal gives me this output:

STARTS

Bus 005 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ENDS

No luck with several thread on ubuntuforums or askubuntu or [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) 

Downloaded this :[https://launchpad.net/ubuntu/quantal/+source/libwebcam](https://launchpad.net/ubuntu/quantal/+source/libwebcam) but again, don't know how to install it or is it even going to help.

I am a journalist and need to use Skype a lot for video interviews. I would be really grateful for any help to get me out of this mess.

Anybody???

---

### Post by neonihilist on 2013-03-04
[COLOR=#000000]Hi, [/COLOR]

[COLOR=#000000]I recently installed Ubuntu 12.10 on the Gnome3 desktop environment. My webcam was working fine during the Ubuntu installation when it asked me to be snapped by my webcam or choose a picture instead. [/COLOR]

[COLOR=#000000]However, the webcam does not show on Skype 4.1.10, which i installed earlier today. The VIDEO DEVICE tab in skype options does not detect a webcam. Neither does Cheese and shows a blank screen. [/COLOR]

[COLOR=#000000]I don't even know if correct drivers for my cam are installed or not. Gnome3 does not have "hardware" in system settings and I cannot find any way to install additional hardware drivers.[/COLOR]

[COLOR=#000000]I have a Lenovo S10-2 netbook with the following specs:[/COLOR]

[COLOR=#000000]Intel® Atom™ CPU N280 @ 1.66GHz × 2 [/COLOR]
[COLOR=#000000]Ram: 993.4 MiB[/COLOR]
[COLOR=#000000]Graphics: unknown (On board?)[/COLOR]
[COLOR=#000000]Ubuntu Partition: 14 GB[/COLOR]
[COLOR=#000000]OS type: 32 bit[/COLOR]

[COLOR=#000000]typing lsusb in the terminal gives me this output:[/COLOR]

[COLOR=#000000]STARTS[/COLOR]

[COLOR=#000000]Bus 005 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]

[COLOR=#000000]ENDS[/COLOR]

[COLOR=#000000]No luck with several thread on ubuntuforums or askubuntu or [/COLOR][https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)[COLOR=#000000] [/COLOR]

[COLOR=#000000]Downloaded this :[/COLOR][https://launchpad.net/ubuntu/quantal/+source/libwebcam](https://launchpad.net/ubuntu/quantal/+source/libwebcam)[COLOR=#000000] but again, don't know how to install it or is it even going to help.[/COLOR]

[COLOR=#000000]I am a journalist and need to use Skype a lot for video interviews. I would be really grateful for any help to get me out of this mess.[/COLOR]

[COLOR=#000000]Anybody???[/COLOR]

---

### Post by neonihilist on 2013-03-04
[COLOR=#000000]Hi, [/COLOR]

[COLOR=#000000]I recently installed Ubuntu 12.10 on the Gnome3 desktop environment. My webcam was working fine during the Ubuntu installation when it asked me to be snapped by my webcam or choose a picture instead. [/COLOR]

[COLOR=#000000]However, the webcam does not show on Skype 4.1.10, which i installed earlier today. The VIDEO DEVICE tab in skype options does not detect a webcam. Neither does Cheese and shows a blank screen. [/COLOR]

[COLOR=#000000]I don't even know if correct drivers for my cam are installed or not. Gnome3 does not have "hardware" in system settings and I cannot find any way to install additional hardware drivers.[/COLOR]

[COLOR=#000000]I have a Lenovo S10-2 netbook with the following specs:[/COLOR]

[COLOR=#000000]Intel® Atom™ CPU N280 @ 1.66GHz × 2 [/COLOR]
[COLOR=#000000]Ram: 993.4 MiB[/COLOR]
[COLOR=#000000]Graphics: unknown (On board?)[/COLOR]
[COLOR=#000000]Ubuntu Partition: 14 GB[/COLOR]
[COLOR=#000000]OS type: 32 bit[/COLOR]

[COLOR=#000000]typing lsusb in the terminal gives me this output:[/COLOR]

[COLOR=#000000]STARTS[/COLOR]

[COLOR=#000000]Bus 005 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]

[COLOR=#000000]ENDS[/COLOR]

[COLOR=#000000]No luck with several thread on ubuntuforums or askubuntu or [/COLOR][https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)[COLOR=#000000] [/COLOR]

[COLOR=#000000]Downloaded this :[/COLOR][https://launchpad.net/ubuntu/quantal/+source/libwebcam](https://launchpad.net/ubuntu/quantal/+source/libwebcam)[COLOR=#000000] but again, don't know how to install it or is it even going to help.[/COLOR]

[COLOR=#000000]I am a journalist and need to use Skype a lot for video interviews. I would be really grateful for any help to get me out of this mess.[/COLOR]

[COLOR=#000000]Anybody???[/COLOR]

---

### Post by neonihilist on 2013-03-05
> **neonihilist said:**
> [COLOR=#000000]Hi, [/COLOR]

[COLOR=#000000]I recently installed Ubuntu 12.10 on the Gnome3 desktop environment. My webcam was working fine during the Ubuntu installation when it asked me to be snapped by my webcam or choose a picture instead. [/COLOR]

[COLOR=#000000]However, the webcam does not show on Skype 4.1.10, which i installed earlier today. The VIDEO DEVICE tab in skype options does not detect a webcam. Neither does Cheese and shows a blank screen. [/COLOR]

[COLOR=#000000]I don't even know if correct drivers for my cam are installed or not. Gnome3 does not have "hardware" in system settings and I cannot find any way to install additional hardware drivers.[/COLOR]

[COLOR=#000000]I have a Lenovo S10-2 netbook with the following specs:[/COLOR]

[COLOR=#000000]Intel® Atom™ CPU N280 @ 1.66GHz × 2 [/COLOR]
[COLOR=#000000]Ram: 993.4 MiB[/COLOR]
[COLOR=#000000]Graphics: unknown (On board?)[/COLOR]
[COLOR=#000000]Ubuntu Partition: 14 GB[/COLOR]
[COLOR=#000000]OS type: 32 bit[/COLOR]

[COLOR=#000000]typing lsusb in the terminal gives me this output:[/COLOR]

[COLOR=#000000]STARTS[/COLOR]

[COLOR=#000000]Bus 005 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]

[COLOR=#000000]ENDS[/COLOR]

[COLOR=#000000]No luck with several thread on ubuntuforums or askubuntu or [/COLOR][https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

[COLOR=#000000]Downloaded this :[/COLOR][https://launchpad.net/ubuntu/quantal/+source/libwebcam](https://launchpad.net/ubuntu/quantal/+source/libwebcam)[COLOR=#000000] but again, don't know how to install it or is it even going to help.[/COLOR]

[COLOR=#000000]I am a journalist and need to use Skype a lot for video interviews. I would be really grateful for any help to get me out of this mess.[/COLOR]

[COLOR=#000000]Anybody???[/COLOR]



Got it. FN+ESC. Works like a charm. Quantal rocks with Gnome.

---

### Post by Mugatu on 2013-03-06
Try this:

[http://askubuntu.com/a/264461/18665](http://askubuntu.com/a/264461/18665)

---

### Post by varunendra on 2013-03-06
Stop posting multiple threads for the same question. Not only this dilutes community efforts to help, it is also against forums Code of Conduct -
> Do not cross post, or post the same thing in multiple locations.

I have merged your threads, as have been your other threads on wireless issue.

Please be aware that continuous behaviour of this kind may attract warnings/infractions from staff.

---

