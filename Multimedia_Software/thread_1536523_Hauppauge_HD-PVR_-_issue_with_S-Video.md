---
title: "Hauppauge HD-PVR - issue with S-Video"
date: 2010-07-22
forum: Multimedia Software
---

### Post by Mayfair on 2010-07-22
I have recently purchased a HD-PVR and attempting to use it under Linux.

HD PVR 49001 LF Rev E3
Model 1228 SL-1228-V3.3-UK

It works well under Windows XP using this driver HD-PVR_1_5_7_0_WHQL

I attempt to record from S-Video under linux. The problem is that after about minute the recording stops.

I'm using Ubuntu 9.04 with this kernel 2.6.28-15-generic

Install the drivers
 > 
$ mkdir v4ldrivers && cd v4ldrivers

$ hg clone v4l-dvb: log

$ cd v4l-dvb

$ make

$ sudo make instalload the driver and set S-Video as the input and the front RCA for audio

> 
$ sudo modprobe hdpvr default_video_input=1 default_audio_input=1 hdpvr_debug=7then I plug in the device

$ cat /var/log/messages

> Jul 11 10:44:35 dell kernel: [ 9514.856017] usb 1-5: new high speed USB device using ehci_hcd and address 9
Jul 11 10:44:35 dell kernel: [ 9515.048219] usb 1-5: configuration #1 chosen from 1 choice
Jul 11 10:44:36 dell kernel: [ 9515.247427] hdpvr 1-5:1.0: untested firmware version 0x12, the driver might not work
Jul 11 10:44:36 dell kernel: [ 9515.537180] hdpvr 1-5:1.0: device now attached to video0
$ dmesg

>  Jul 11 10:44:36 dell kernel: [ 9515.351934] hdpvr 1-5:1.0: magic request returned 8
Jul 11 10:44:36 dell kernel: [ 9515.367812] hdpvr 1-5:1.0: config call request for value 0x1700 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.383814] hdpvr 1-5:1.0: config call request for value 0x1500 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.407688] hdpvr 1-5:1.0: config call request for value 0x1200 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.423568] hdpvr 1-5:1.0: config call request for value 0x1300 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.440570] hdpvr 1-5:1.0: config call request for value 0x2900 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.460448] hdpvr 1-5:1.0: config call request for value 0x2a00 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.480450] hdpvr 1-5:1.0: config call request for value 0x2b00 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.500326] hdpvr 1-5:1.0: config call request for value 0x2c00 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.520203] hdpvr 1-5:1.0: config call request for value 0x2d00 returned 1
Jul 11 10:44:36 dell kernel: [ 9515.524390] hdpvr 1-5:1.0: control request returned 4
Jul 11 10:44:36 dell kernel: [ 9515.532201] hdpvr 1-5:1.0: control request returned 1
Jul 11 10:44:36 dell kernel: [ 9515.536712] hdpvr 1-5:1.0: control request returned 1
Jul 11 10:44:36 dell kernel: [ 9515.536716] hdpvr 1-5:1.0: allocating 64 buffers

$ ls -l /dev/

> crw-rw----+ 1 root video 81, 0 2010-07-11 10:44 video0
$ v4l2-ctl --device=/dev/video0 -l

> brightness (int) : min=0 max=255 step=1 default=134 value=134 flags=slider
contrast (int) : min=0 max=255 step=1 default=128 value=128 flags=slider
saturation (int) : min=0 max=255 step=1 default=128 value=128 flags=slider
hue (int) : min=0 max=255 step=1 default=128 value=128 flags=slider
sharpness (int) : min=0 max=255 step=1 default=128 value=128 flags=slider
audio_encoding (menu) : min=3 max=4 default=3 value=3 flags=update
video_encoding (menu) : min=2 max=2 default=2 value=2
video_bitrate_mode (menu) : min=0 max=1 default=1 value=1 flags=update
video_bitrate (int) : min=1000000 max=13500000 step=100000 default=6500000 value=6500000
video_peak_bitrate (int) : min=1100000 max=20200000 step=100000 default=9000000 value=9000000 flags=inactive
attempt to capture with

>  $ cat /dev/video0 > test1.tsthe blue LED illuminates, test1.ts increases in size

a short while later (about 1 minute) the blue LED goes off

test1.ts no longer increases in size

i use ctrl-c to stop the cat command

the file plays well with video and sound

> $ vlc test1.ts


$dmesg

>  11 10:48:59 dell kernel: [ 9778.463147] hdpvr 1-5:1.0: video signal: 720x480@30hz
Jul 11 10:49:02 dell kernel: [ 9781.999761] hdpvr 1-5:1.0: encoder start control request returned 0
Jul 11 10:49:03 dell kernel: [ 9782.272794] hdpvr 1-5:1.0: config call request for value 0x700 returned 1
Jul 11 10:49:03 dell kernel: [ 9782.272804] hdpvr 1-5:1.0: streaming started
Jul 11 10:49:03 dell kernel: [ 9782.272810] hdpvr 1-5:1.0: hdpvr_read:443 buffer stat: 64 free, 0 proc
Jul 11 10:49:05 dell kernel: [ 9785.194920] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 1 free, 63 proc
Jul 11 10:49:05 dell kernel: [ 9785.200381] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 2 free, 62 proc
Jul 11 10:49:06 dell kernel: [ 9785.213425] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 3 free, 61 proc
Jul 11 10:49:06 dell kernel: [ 9785.214426] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 4 free, 60 proc
Jul 11 10:49:06 dell kernel: [ 9785.215415] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 5 free, 59 proc
Jul 11 10:49:06 dell kernel: [ 9785.216778] hdpvr 1-5:1.0: hdpvr_submit_buffers:209 buffer stat: 0 free, 64 proc
Jul 11 10:49:06 dell kernel: [ 9785.238426] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 1 free, 63 proc
Jul 11 10:49:06 dell kernel: [ 9785.238478] hdpvr 1-5:1.0: hdpvr_submit_buffers:209 buffer stat: 0 free, 64 proc
Jul 11 10:49:06 dell kernel: [ 9785.256297] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 1 free, 63 proc
Jul 11 10:49:06 dell kernel: [ 9785.256340] hdpvr 1-5:1.0: hdpvr_submit_buffers:209 buffer stat: 0 free, 64 proc
Jul 11 10:49:06 dell kernel: [ 9785.277425] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 1 free, 63 proc
Jul 11 10:49:06 dell kernel: [ 9785.277466] hdpvr 1-5:1.0: hdpvr_submit_buffers:209 buffer stat: 0 free, 64 proc
Jul 11 10:49:06 dell kernel: [ 9785.295938] hdpvr 1-5:1.0: hdpvr_read:503 buffer stat: 1 free, 63 proc
Jul 11 10:49:06 dell kernel: [ 9785.295982] hdpvr 1-5:1.0: hdpvr_submit_buffers:209 buffer stat: 0 free, 64 proc
Jul 11 10:49:27 dell kernel: [ 9806.717074] hdpvr 1-5:1.0: hdpvr_submit_buffers:209 buffer stat: 0 free, 64 proc
Jul 11 10:51:16 dell kernel: [ 9915.603635] hdpvr 1-5:1.0: config call request for value 0x800 returned 1
Jul 11 10:51:16 dell kernel: [ 9915.603646] hdpvr 1-5:1.0: transmit worker exited
Jul 11 10:51:17 dell kernel: [ 9916.916149] hdpvr 1-5:1.0: used 0 urbs to empty device buffers
I attempt to capture once more


> 

$ cat /dev/video0 > test2.psthe blue LED does not illuminate and the test2.ps remains at zero size


$ dmesg

> Jul 11 10:51:16 dell kernel: [ 9915.603635] hdpvr 1-5:1.0: config call request for value 0x800 returned 1
Jul 11 10:51:16 dell kernel: [ 9915.603646] hdpvr 1-5:1.0: transmit worker exited
Jul 11 10:51:17 dell kernel: [ 9916.916149] hdpvr 1-5:1.0: used 0 urbs to empty device buffers
Jul 11 11:05:43 dell kernel: [10782.567065] hdpvr 1-5:1.0: video signal: 720x480@30hz
Jul 11 11:05:43 dell kernel: [10782.570936] hdpvr 1-5:1.0: encoder start control request returned 0
Jul 11 11:05:53 dell kernel: [10792.584092] hdpvr 1-5:1.0: config call request for value 0x700 returned -110
Jul 11 11:05:53 dell kernel: [10792.584100] hdpvr 1-5:1.0: streaming started
Jul 11 11:05:53 dell kernel: [10792.584106] hdpvr 1-5:1.0: hdpvr_read:443 buffer stat: 64 free, 0 proc
Jul 11 11:05:53 dell kernel: [10792.584166] hdpvr 1-5:1.0: hdpvr_submit_buffers:209 buffer stat: 0 free, 64 proc
$ ctrl-c


$ dmesg

>  Jul 11 11:10:44 dell kernel: [11083.632072] hdpvr 1-5:1.0: config call request for value 0x800 returned -110
I hard reset the device then start again but the problem repeats. I will be grateful for any help.

---

### Post by wkulecz on 2010-07-22
> Jul 11 10:44:36 dell kernel: [ 9515.247427] hdpvr 1-5:1.0: untested firmware version 0x12, the driver might not work

Perhaps this is the problem.

Contacting the driver maintainer might be the place to start.

---

### Post by djb61230 on 2010-07-27
That warning message is normal.

The problem is that you are using "cat".  I have seen this same behavior.  I am writing my own mythtv replacement (I probably will release it at some point) and I discovered this problem.  I think your system gets "busy" and it cannot read fast enough and the "connection" gets confused.  At least this is my guess.

Someone over at avsforum.com posted some code which works because it has code to "recover" from these over or under runs.  Here is the post:

[http://www.avsforum.com/avs-vb/showthread.php?p=15037025#post15037025]("http://www.avsforum.com/avs-vb/showthread.php?p=15037025#post15037025")

It does work but you have to compile it.  Something like this should work:

gcc -o capture capture.c

This assumes you take the code from that post and save it in a file called capture.c

---

