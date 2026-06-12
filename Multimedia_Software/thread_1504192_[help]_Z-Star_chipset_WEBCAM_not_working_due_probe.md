---
title: "[help] Z-Star chipset WEBCAM not working due probe fail"
date: 2010-06-07
forum: Multimedia Software
---

### Post by 3esmit on 2010-06-07
Hello community,

I'm having troubles using this not so new webcam. I didnt found any thread that have a problem like mine. In older kernel versions the webcam started working compiling and installing zc3xx module, but as far as I googled and lsmod this module now comes with default kernel. As I can see, the module itself recognizes the webcam, but fails in the process.
Does someone have some idea of fixing? Should I report it to launchpad (and so, which section?)? [B]

System information:[/B]

_lsusb_
Bus 004 Device 003: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam

_dmesg_
[ 5242.330027] usb 4-2: new full speed USB device using uhci_hcd and address 3
[ 5242.532166] usb 4-2: configuration #1 chosen from 1 choice
[ 5242.535083] gspca: probing 0ac8:307b
[ 5243.403985] zc3xx: probe 2wr ov vga 0x7628
[ 5243.536974] zc3xx: probe 3wr vga 1 0x4001
[ 5243.737971] zc3xx: probe sensor -> 0006
[ 5243.737977] zc3xx: Unknown sensor 0006
[ 5243.738004] zc3xx: probe of 4-2:1.0 failed with error -22

_uname -r_
2.6.32-22-generic

_lsmod | grep zc3xx_
*Module                      Size         Used by*
gspca_zc3xx         49253  0 
gspca_main           25031  1     gspca_zc3xx



Thank you.

---

### Post by no2498 on 2010-06-08
try this

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

in/on 910 and up cheese webcam booth is/should be loaded
look for it in sound & video

if it came on try it in cheese

hope this helps

---

### Post by 3esmit on 2010-06-12
> **no2498 said:**
> try this

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

in/on 910 and up cheese webcam booth is/should be loaded
look for it in sound & video

if it came on try it in cheese

hope this helps

Thank you for the help, but v4l1 grabs the /dev/video* that is not build due to gspca fail.

I give up and I will buy another webcam. End of history. If you also have that problems, well, I really dont get the solution and It should be working but its not, its a kernel's module problem, and the only way to fix it is by changing it code and recompiling, which I really dont have the time to learn it and try it.

---

