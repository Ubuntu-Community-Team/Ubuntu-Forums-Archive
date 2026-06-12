---
title: "Webcam works in very special configurations, make it work always ?"
date: 2010-07-03
forum: Multimedia Software
---

### Post by Megra on 2010-07-03
Hello,

I have a "Logitech Quickcam Web"  Webcam which has very strange behaviors. It's an old Lego webcam, recognised as a logitech, which worked fine a few years ago, on Windows XP for example, and which doesn't on my freshly installed Ubuntu Lucid Lynx 10.04.

**_Testing material_:**
_OS_: Ubuntu 10.04
_Webcam_: ID 046d:0850 Logitech, Inc. QuickCam
_Software_: cheese
_Kernel_: Linux megra-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

_**First**_, it only works on some of my (desktop) computer USB ports. My ports are USB-2 and my webcam probably is USB-1, could it be a problem ? Strangely, on 6 ports, only 2 of them works, in this configuration:
Line 1:// OK     FAIL
Line 2:// FAIL   OK
Line 3:// OK     FAIL
Why those 3 ?
All of the USB ports are working, I tested them with a USB key, and everything seemed perfectly fine.

The error reported is:
> libv4l2: error turning on stream: Input/output error
Jul  4 00:58:14 megra-desktop kernel: [ 1228.037707] gspca: usb_submit_urb alt 1 err -28
Jul  4 00:58:14 megra-desktop kernel: [ 1228.060032] gspca: no transfer endpoint found_**Second**_, when I start/reboot my computer, the webcam will not work, whatever USB port it is plugged on. The error reported is the same as above:
> libv4l2: error turning on stream: Input/output error
Jul  4 00:58:14 megra-desktop kernel: [ 1228.037707] gspca:  usb_submit_urb alt 1 err -28
Jul  4 00:58:14 megra-desktop kernel: [ 1228.060032] gspca: no transfer  endpoint foundHowever, if I un-plug the webcam, and replug it in one of the "working" USB ports, the webcam starts working normally.
Why would I need to replug it ?

Here are some logs.
**$ sudo egrep -i 'usb|STV|gspca|pulseaudio|rtkit' /var/log/dmesg**
> [...]
[    6.423808] gspca: main v2.7.0 registered
[    6.450741] STV06xx: Probing for a stv06xx device
[    6.450744] gspca: probing 046d:0850
[    6.450747] STV06xx: Configuring camera
[    6.458626] STV06xx: vv6410 sensor detected
[    6.458630] STV06xx: Initializing camera
[    6.792689] gspca: probe ok
[    6.792706] STV06xx: Probing for a stv06xx device
[    6.792708] gspca: probing 046d:0850
[    6.792716] STV06xx: Probing for a stv06xx device
[    6.792717] gspca: probing 046d:0850
[    6.792731] usbcore: registered new interface driver STV06xx
[    6.792733] STV06xx: registered
[    6.995837] usbcore: registered new interface driver snd-usb-audio**When un-plugged: $ sudo tail -f -n 0 /var/log/syslog**
> Jul  4 00:40:48 megra-desktop kernel: [  181.749073] usb 4-3: USB disconnect, address 2
Jul  4 00:40:48 megra-desktop kernel: [  181.749135] STV06xx: Disconnecting the stv06xx device
Jul  4 00:40:48 megra-desktop kernel: [  181.749204] gspca: disconnect complete[B]When plugged in: $ sudo tail -f -n 0 /var/log/syslog
[/B]> Jul  4 00:41:02 megra-desktop kernel: [  195.360040] usb 4-4: new full speed USB device using ohci_hcd and address 3
Jul  4 00:41:02 megra-desktop kernel: [  195.584113] usb 4-4: configuration #1 chosen from 1 choice
Jul  4 00:41:02 megra-desktop kernel: [  195.587187] STV06xx: Probing for a stv06xx device
Jul  4 00:41:02 megra-desktop kernel: [  195.587190] gspca: probing 046d:0850
Jul  4 00:41:02 megra-desktop kernel: [  195.587192] STV06xx: Configuring camera
Jul  4 00:41:02 megra-desktop kernel: [  195.596016] STV06xx: vv6410 sensor detected
Jul  4 00:41:02 megra-desktop kernel: [  195.596021] STV06xx: Initializing camera
Jul  4 00:41:02 megra-desktop kernel: [  195.933053] gspca: probe ok
Jul  4 00:41:02 megra-desktop kernel: [  195.933104] STV06xx: Probing for a stv06xx device
Jul  4 00:41:02 megra-desktop kernel: [  195.933106] gspca: probing 046d:0850
Jul  4 00:41:02 megra-desktop pulseaudio[2087]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
Jul  4 00:41:02 megra-desktop pulseaudio[2087]: last message repeated 6 times
Jul  4 00:41:02 megra-desktop rtkit-daemon[1911]: Sucessfully made thread 2284 of process 2087 (n/a) owned by '1000' RT at priority 5.
Jul  4 00:41:02 megra-desktop rtkit-daemon[1911]: Supervising 4 threads of 1 processes of 1 users._**Finally**_, I have no idea why is it behaving like this. I need the webcam to work just after starting the computer, so unplugging and re-plugging the webcam everytime is not a viable option.

Any idea why is it behaving like this ? Any way to solve it ?
Thanks in advance :)


If it might help, my mods are: **$ lsmod | egrep 'v4l|vid|gspca'**
> gspca_stv06xx          27230  0 
gspca_main             25031  1 gspca_stv06xx
videodev               40518  1 gspca_main
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    12020  1 videodev

---

### Post by Megra on 2010-07-04
Some news on the problem, bad news of course, otherwise it woudn't be fun :)
Here is what fail :

1) The camera works perfectly, cheese displays it properly. We can stop cheese and start it over again and it still works (stop and start tried 8 times).
However, after some commands, the result is not sure, consider this command which take a JPG picture of what the camera sees :
$ streamer -d -c /dev/video0 -o outfile.jpeg

Launching it once, maybe twice or three times might work just fine, but after it might work (the picture is taken) but then an error appears in **/var/log/syslog**:

> Jul  4 21:26:18 megra-desktop kernel: [74911.569023] **hub 4-0:1.0: port 3 disabled by hub (EMI?), re-enabling...**
Jul  4 21:26:18 megra-desktop kernel: [74911.569028] usb 4-3: USB disconnect, address 13
Jul  4 21:26:18 megra-desktop kernel: [74911.570033] gspca: set alt 0 err -108
Jul  4 21:26:18 megra-desktop kernel: [74911.570072] STV06xx: Disconnecting the stv06xx device
Jul  4 21:26:18 megra-desktop kernel: [74911.570136] gspca: disconnect complete
Jul  4 21:26:18 megra-desktop kernel: [74911.920047] usb 4-3: new full speed USB device using ohci_hcd and address 14
Jul  4 21:26:19 megra-desktop kernel: [74912.144045] usb 4-3: configuration #1 chosen from 1 choice
Jul  4 21:26:19 megra-desktop kernel: [74912.146984] STV06xx: Probing for a stv06xx device
Jul  4 21:26:19 megra-desktop kernel: [74912.146987] gspca: probing 046d:0850
Jul  4 21:26:19 megra-desktop kernel: [74912.146989] STV06xx: Configuring camera
Jul  4 21:26:19 megra-desktop kernel: [74912.155941] STV06xx: vv6410 sensor detected
Jul  4 21:26:19 megra-desktop kernel: [74912.155946] STV06xx: Initializing camera
Jul  4 21:26:19 megra-desktop kernel: [74912.492991] gspca: probe ok
Jul  4 21:26:19 megra-desktop pulseaudio[2087]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
Jul  4 21:26:19 megra-desktop pulseaudio[2087]: last message repeated 6 times
Jul  4 21:26:19 megra-desktop rtkit-daemon[1911]: Sucessfully made thread 8516 of process 2087 (n/a) owned by '1000' RT at priority 5.
Jul  4 21:26:19 megra-desktop rtkit-daemon[1911]: Supervising 4 threads of 1 processes of 1 users.

After some searching, I saw that the cause could be that any of those of true:
 * (A) hardware is flaky 
 * (B) hardware getting hit by EMI (ElectroMagnetic Interference)
 * (C) the driver is flaky

(A : rejected) Hardware seems to work as cheese displays everything  without problems (taking picture/videos works too).
(B : rejected) Same as A, EMI cannot be reflected on some software and not others, it has just no sense.
(C : possibly) Has **streamer uses v4l2** (cheese might use something else ?? I don't think so), maybe the driver is flaky. Not especially v4l2 but some of the drivers it relies on... So **gspca_STV06xx** could be the "bad guy". But then, still why would some software fail and others not ??

This is strange ... definitely !

---

### Post by no2498 on 2010-07-05
see if this program helps you wxcam

read and install all of what the page tells you to
it does come in a deb file also


[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

