---
title: "Can't adjust the volumes of USB Doro212 phone"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by encompass on 2006-08-02
I purchased a usb phone to use for skype and ekiga because my sound card was not working with them.
This is the phone:
lsusb: Bus 001 Device 004: ID 0451:1020 Texas Instruments, Inc.
Device name: Doro 212lPC <--could be a pipe not an l
Here is a screen shot of the information
[http://84.249.13.146/screenshot.png](http://84.249.13.146/screenshot.png)
it will show the picture if my computer is on.
Additionaly, I notice a few things:
***When I try to restart alsa to see what errors I get I get this when the unit is plugged in.

```
encompass@tabby:~$ sudo /etc/init.d/alsa-utils restart
Password:
 * Shutting down ALSA...  * warning: 'alsactl store' failed with error message 'alsactl: get_control:158: Cannot read control '2,0,0,Tone Control - Treble,0': Invalid argument'...  amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
                                                                         [fail]
 * Setting up ALSA...  * warning: 'alsactl restore' failed with error message 'No state is present for card D212IPC'... amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
amixer: Mixer hw:1 load error: Invalid argument
                                                                         [ ok ]
encompass@tabby:~$

```
and no errors when it isn't pluged in.
I also notice it has an error about saving the state of this sound card on exit.

***The unit has a volume control button, but does that same as my keyboard, that is, it adjusts the main volume.
When atempting to adjust the volume manually using the volume control it seems to kindof well... sometiems it show the device and sometimes it doesn't.  It is marked as usb sound device when it is there.
And when it is... it almost locks up.  Showing nothing but the window with no file menu or anything... I can close it, it gives a small delay then closes.

***The device does work, I can use it at my skype phone, but the volume from the speaker is at full and the volume of the Mic is not very high.  So I can't use it as a phone.

Lastly,
my dmesg on the subject...
> [4294678.588000] usb 1-1: new full speed USB device using ohci_hcd and address 3
[4294678.907000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00301bb400007106]
[4294679.276000] usb 1-2: new full speed USB device using ohci_hcd and address 4
[4294679.672000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[4294679.805000] usb 2-1: config 1 has an invalid interface number: 1 but max is  0
[4294679.805000] usb 2-1: config 1 has no interface number 0
...
...
[4294685.315000] usbcore: registered new driver snd-usb-audio
[4294685.317000] usbcore: registered new driver hiddev
[4294685.341000] input: ??Welltech Computer Doro 212IPC as /class/input/input3
[4294685.341000] input: USB HID v1.00 Device [??Welltech Computer Doro 212IPC] o n usb-0000:00:13.0-2

Have any idea on how to get it working with the volume control or perhaps just manually setting the volume to one state for ever would be great.:-k


This should work in Feisty now... I will report if I still get problems.

---

### Post by Tulams on 2007-06-01
I have exactly the same unit and exactly the same problem.

If you have a solution I would be very interested.

Be gentle on me though as I am a complete newbie.

Cheers

---

