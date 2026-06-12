---
title: "No Sound with WinTV-PVR-USB2"
date: 2009-01-31
forum: Mythbuntu
---

### Post by lingenfr on 2009-01-31
** This really isn't solved, but with some help (not from here) I was able to isolate the problem to my XBOX/XBMC/xbmcmythtv frontend **

As the subject says... I did quite a lot of research and found the workaround for the bug in the current kernel to get it working at all, but I still don't have sound. I am not quite sure what to try. I tried alsamixer and everything was turned up. I ran a couple of commands.

linghome@MYTHTV-BACKEND:~$ cat /sys/class/pvrusb2/sn-7365660/ctl_volume/cur_val
58981

linghome@MYTHTV-BACKEND:~$ dmesg | grep pvrusb2
[   10.900110] usbcore: registered new interface driver pvrusb2
[   10.900207] pvrusb2: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[   10.900215] pvrusb2: Debug mask is 31 (0x1f)
[   11.130351] tuner' 3-0043: chip found @ 0x86 (pvrusb2_a)
[   11.166723] tuner' 3-0061: chip found @ 0xc2 (pvrusb2_a)
[   11.217525] msp3400' 3-0040: MSP3445G-B8 found @ 0x80 (pvrusb2_a)
[   11.277914] saa7115' 3-0021: saa7115 found (1f7115d0e100000) @ 0x42 (pvrusb2_a)
[   11.457945] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk
[   11.457953] pvrusb2: Mapping standards mask=0xb700 (PAL-M/N/Nc;NTSC-M/Mj/Mk)
[   11.457959] pvrusb2: Setting up 6 unique standard(s)
[   11.457965] pvrusb2: Set up standard idx=0 name=PAL-M
[   11.457971] pvrusb2: Set up standard idx=1 name=PAL-N
[   11.457977] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   11.457985] pvrusb2: Set up standard idx=3 name=NTSC-M
[   11.457993] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   11.457999] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   11.458010] pvrusb2: Initial video standard guessed as NTSC-M
[   11.458032] pvrusb2: Device initialization completed successfully.
[   11.458448] pvrusb2: registered device video1 [mpeg]
[   11.460069] pvrusb2: registered device radio0 [mpeg]
[633113.936497] msp3400' 3-0040: MSP3445G-B8 found @ 0x80 (pvrusb2_a)
[633227.983241] pvrusb2: Device being rendered inoperable
[633227.983476] pvrusb2: unregistered device video1 [mpeg]
[633227.983564] pvrusb2: unregistered device radio0 [mpeg]
[633227.987219] pvrusb2: Attempted to execute control transfer when device not ok
[633237.570287] tuner' 3-0043: chip found @ 0x86 (pvrusb2_a)
[633237.606338] tuner' 3-0061: chip found @ 0xc2 (pvrusb2_a)
[633237.669073] saa7115' 3-0021: saa7115 found (1f7115d0e100000) @ 0x42 (pvrusb2_a)
[633237.862956] msp3400' 3-0040: MSP3445G-B8 found @ 0x80 (pvrusb2_a)
[633237.886001] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk
[633237.886009] pvrusb2: Mapping standards mask=0xb700 (PAL-M/N/Nc;NTSC-M/Mj/Mk)
[633237.886015] pvrusb2: Setting up 6 unique standard(s)
[633237.886023] pvrusb2: Set up standard idx=0 name=PAL-M
[633237.886029] pvrusb2: Set up standard idx=1 name=PAL-N
[633237.886034] pvrusb2: Set up standard idx=2 name=PAL-Nc
[633237.886039] pvrusb2: Set up standard idx=3 name=NTSC-M
[633237.886045] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[633237.886050] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[633237.886057] pvrusb2: Initial video standard guessed as NTSC-M
[633237.886072] pvrusb2: Device initialization completed successfully.
[633237.886864] pvrusb2: registered device video1 [mpeg]
[633237.888114] pvrusb2: registered device radio0 [mpeg]

I noticed that there was other relevant information in dmesg, so I have attached a complete dmesg. If you have a fix or ideas on troubleshooting, please post.

---

### Post by lingenfr on 2009-02-07
bump

---

### Post by danbodoh on 2009-02-07
How is your audio and video connected?  Perhaps the problem is in the connections to the pvr usb 2?

---

### Post by lingenfr on 2009-02-07
> **danbodoh said:**
> How is your audio and video connected?  Perhaps the problem is in the connections to the pvr usb 2?

It connects with a USB cable, so the video wouldn't work if that were the case.

---

