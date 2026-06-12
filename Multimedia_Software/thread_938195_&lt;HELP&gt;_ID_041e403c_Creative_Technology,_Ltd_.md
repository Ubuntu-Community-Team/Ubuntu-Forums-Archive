---
title: "&lt;HELP&gt; ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra"
date: 2008-10-04
forum: Multimedia Software
---

### Post by Paulzy on 2008-10-04
I'm looking for a way to use my **ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra** on Ubuntu Hardy Hedron. I've seen many posts on other sites but they are over 2 years old and are no longer relevant. Has anyone had any success in getting **ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra **to work on Ubuntu?

I have the following apps installed: **EasyCam2, Cheese, Camera Monitor,** and **Ekiga** and none work. *lsusb* will show the cam connected but the light is not on and none of the software recognizes it. I often get the */dev/video device not found* error. And I did *ls /dev* and there is no */dev/video* listed.

I've read and there is no information on getting this installed.
I've found some information, but it was not relevant to Hardy Hedron.

My NVIDIA GeForce 7600 GS has the NVIDIA drivers installed under "Harware Drtivers". But that does not seem related to the */dev/video* issue.

What do I need to do to get Ubuntu to recognize my **ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra ** and a */dev/video *listing?

Thanks in advance. :popcorn:

---

### Post by mindoms on 2008-10-04
I had no luck so far helping people with webcam problems on this forum, but maybe this time :)

please plug your webcam in. if it is already plugged, plug it out, then in again.
then run the following in a terminal and post the output:
```

dmesg | tail -n20
ls -l /dev/video*

```

---

### Post by Paulzy on 2008-10-07
Here is my output. BTW, what is the deal with the ACPI message? I keep getting it.
> pauljc@PJCI:~$ dmesg | tail -n20
[  431.606490] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  437.599319] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  443.592071] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  449.584864] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  455.577651] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  461.570448] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  467.563238] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  473.556031] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  479.548823] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  485.541623] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  491.534415] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  497.527205] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  502.121209] usb 5-6: USB disconnect, address 7
[  503.519992] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  506.867341] usb 5-6: new high speed USB device using ehci_hcd and address 9
[  507.008968] usb 5-6: configuration #1 chosen from 1 choice
[  509.512775] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  515.505575] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  521.498375] ACPI: Unable to turn cooling device [f7c48f18] 'on'
[  527.491187] ACPI: Unable to turn cooling device [f7c48f18] 'on'
pauljc@PJCI:~$ ls -l /dev/video*
ls: cannot access /dev/video*: No such file or directory
pauljc@PJCI:~$ sudo ls -l /dev/video*
[sudo] password for pauljc: 
ls: cannot access /dev/video*: No such file or directory
pauljc@PJCI:~$ lsusb
Bus 005 Device 009: ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra
Bus 005 Device 006: ID 067b:2506 Prolific Technology, Inc. 
Bus 005 Device 005: ID 03f0:0f07 Hewlett-Packard 
Bus 005 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 2525:8911  
Bus 001 Device 001: ID 0000:0000  
pauljc@PJCI:~$ 


---

### Post by Raiser on 2010-01-24
Hello,

I managed to make this webcam recognized, but the output is blank screen.

[http://ubuntuforums.org/showthread.php?p=8717167#post8717167](http://ubuntuforums.org/showthread.php?p=8717167#post8717167)

---

