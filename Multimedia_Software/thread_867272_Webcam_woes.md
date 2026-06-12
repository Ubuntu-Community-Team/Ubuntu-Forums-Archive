---
title: "Webcam woes"
date: 2008-07-22
forum: Multimedia Software
---

### Post by randomlogic on 2008-07-22
Hello all.  I've been hunting around for the solution to an unusual problem, but have gotten stuck.  The problem is my webcam.

I know that it works because I have been able to successfully get a clear picture with Ekiga.  My problem is that nothing else works.  Not cheese or camorama or flash websites that support webcams.

When I plug the webcam in, it successfully mounts, as shown:
crw-rw----+ 1 root video 81, 0 2008-07-22 17:40 /dev/video0

lsusb reports:
Bus 004 Device 004: ID 19ff:0102

lshw reports:```
              *-usb
                   description: Video
                   product: Dynex 1.3MP Webcam
                   vendor: Dynex
                   physical id: 1
                   bus info: usb@4:1
                   version: 1.00
                   serial: 080516_A_46071
                   capabilities: usb-2.00
                   configuration: driver=snd-usb-audio maxpower=500mA speed=480.0MB/s
```
When I start cheese, the webcam light goes on and off twice.  Then cheese crashes with:```
The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 47 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

camorama simply reports that it couldn't connect to device /dev/video0

Flash sites recognize the the webcam, but won't connect to it.

Does anyone have any clues as to why ekiga would work flawlessly with the webcam, but nothing else?  Any help would be appreciated.

Thank you.

---

### Post by randomlogic on 2008-07-23
I have additional information that may be helpful.  I started looking over the preferences in ekiga to find a clue as to why it could access the webcam while nothing else could.

I noticed that the video plugin it was using was V4L2.  When I switched to V4L, I lost the connection to the webcam.  When I switched back, the connection came back.

I'm thinking that this is an important clue.

---

### Post by cariboo on 2008-07-23
Could you show us the output of:

```
lsusb
```

Jim

---

### Post by randomlogic on 2008-07-23
Sure.  Here it is:
```
Bus 004 Device 007: ID 19ff:0102
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```
The first line is the webcam.  As I said, Video 4 Linux 2 has no problem with it.  I've found a link that may help: [http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html]("http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html"), but it looks like it might be a trick problem for a while - at least until more programs support v4l2.

---

### Post by randomlogic on 2008-07-23
Well, the Flash part of the problem is solved.  It seems that Flash Player 10 (beta 2) supports V4L2.  Ubuntu 8.10 already has a package that I was able to locate and install:
[http://packages.ubuntu.com/intrepid/flashplugin-nonfree]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree")cheese and camorama still don't recognize it, but at least I'm closer to a solution.

The Intrepid build of Flash 10 works, BTW.  (Just don't try to edit your settings.)

---

