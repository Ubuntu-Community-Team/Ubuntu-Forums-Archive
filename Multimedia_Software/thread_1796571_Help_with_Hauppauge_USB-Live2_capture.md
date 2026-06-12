---
title: "Help with Hauppauge USB-Live2 capture"
date: 2011-07-04
forum: Multimedia Software
---

### Post by BitJunkie on 2011-07-04
I'm using Natty 64-bit and I'm trying to get the USB-Live2 capture device to work. I've searched around but can't find anything that works. Here's some info after I plug in the device.

Devices /dev/video1 and /dev/vbi0 are created, but are not removed when the device is unplugged.

None of the indicator lights are on. In Windows, a blue light comes on when it is plugged in and a green light comes on when it is capturing.

lsusb
```
Bus 002 Device 005: ID 2040:c200 Hauppauge
```

dmesg
```
[  527.450166] usb 2-2: new high speed USB device using ehci_hcd and address 5
[  527.684892] IR NEC protocol handler initialized
[  527.687105] IR RC5(x) protocol handler initialized
[  527.689167] IR RC6 protocol handler initialized
[  527.691502] IR JVC protocol handler initialized
[  527.693657] IR Sony protocol handler initialized
[  527.697092] lirc_dev: IR Remote Control driver registered, major 250 
[  527.699718] IR LIRC bridge handler initialized
[  527.718812] cx231xx v4l2 driver loaded.
[  527.718873] cx231xx #0: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:c200) with 5 interfaces
[  527.718876] cx231xx #0: registering interface 1
[  527.729811] cx231xx #0: can't change interface 3 alt no. to 3: Max. Pkt size = 0
[  527.739067] cx231xx #0: can't change interface 4 alt no. to 1: Max. Pkt size = 0
[  527.740181] cx231xx #0: Identified as Hauppauge USB Live 2 (card=9)
[  527.849888] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[  527.859014] cx231xx #0: Changing the i2c master port to 3
[  527.875187] cx25840 15-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #0)
[  527.894040] cx25840 15-0044:  Firmware download size changed to 16 bytes max length
[  529.942897] cx25840 15-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[  529.978644] cx231xx #0: cx231xx #0: v4l2 driver version 0.0.1
[  530.007767] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[  530.056392] cx231xx #0: video_mux : 0
[  530.056398] cx231xx #0: do_mode_ctrl_overrides : 0xb000
[  530.057261] cx231xx #0: do_mode_ctrl_overrides NTSC
[  530.064934] cx231xx #0: cx231xx #0/0: registered device video1 [v4l2]
[  530.064993] cx231xx #0: cx231xx #0/0: registered device vbi0
[  530.064997] cx231xx #0: V4L2 device registered as video1 and vbi0
[  530.065004] cx231xx #0: EndPoint Addr 0x84, Alternate settings: 5
[  530.065008] cx231xx #0: Alternate setting 0, max size= 512
[  530.065011] cx231xx #0: Alternate setting 1, max size= 184
[  530.065014] cx231xx #0: Alternate setting 2, max size= 728
[  530.065018] cx231xx #0: Alternate setting 3, max size= 2892
[  530.065021] cx231xx #0: Alternate setting 4, max size= 1800
[  530.065025] cx231xx #0: EndPoint Addr 0x85, Alternate settings: 2
[  530.065029] cx231xx #0: Alternate setting 0, max size= 512
[  530.065033] cx231xx #0: Alternate setting 1, max size= 512
[  530.065037] cx231xx #0: EndPoint Addr 0x86, Alternate settings: 2
[  530.065041] cx231xx #0: Alternate setting 0, max size= 512
[  530.065044] cx231xx #0: Alternate setting 1, max size= 576
[  530.066389] usbcore: registered new interface driver cx231xx
[  530.071318] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8
[  530.072166] cx231xx #0: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[  530.073502] cx231xx #0:  setPowerMode::mode = 48, No Change req.
[  530.074612] cx231xx #0: EndPoint Addr 0x83, Alternate settings: 3
[  530.074617] cx231xx #0: Alternate setting 0, max size= 512
[  530.074621] cx231xx #0: Alternate setting 1, max size= 28
[  530.074624] cx231xx #0: Alternate setting 2, max size= 52
[  530.074628] cx231xx: Cx231xx Audio Extension initialized
[  530.075250] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8
[  530.129963] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  530.134212] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  530.142293] cx231xx #0: can't change interface 2 alt no. to 0 (err=-71)
[  530.142299] cx231xx #0: failed to set alternate setting !
[  530.146541] cx231xx #0: can't change interface 2 alt no. to 1 (err=-71)
[  530.146546] cx231xx #0: failed to set alternate setting !
[  530.151041] cx231xx #0: can't change interface 2 alt no. to 1 (err=-71)
[  530.151046] cx231xx #0: failed to set alternate setting !
[  530.174539] cx231xx #0: can't change interface 2 alt no. to 1 (err=-71)
[  530.174544] cx231xx #0: failed to set alternate setting !
[  530.178784] cx231xx #0: can't change interface 2 alt no. to 1 (err=-71)
[  530.178787] cx231xx #0: failed to set alternate setting !
```

I've tried accessing the device using VLC, mplayer/mencoder, tvtime, kdenlive, and guvcview. VLC says it can't access /dev/video1, mplayer shows a green screen and says "v4l2: select timeout", kdenlive hangs at "Initializing" and guvcview shows a black screen. I'm stumped, any ideas?

---

### Post by cdvanhorn on 2011-07-06
Sorry, I don't think it works with the current version of Ubuntu, but it does look like it's being worked on (see the last comments in the following link, [http://www.kernellabs.com/blog/?p=1445]("http://www.kernellabs.com/blog/?p=1445")).

If you really want it to work you can try Ubuntu 10.04, which apparently works for some people.  I haven't tried Ubuntu 10.04.

---

### Post by BitJunkie on 2011-07-07
Thanks for the info. I'll follow the kernellabs thread and hopefully progress will continue to be made.

I only capture video occasionally, so I don't think it's worth going back to 10.04. But it's the only thing I need Windows for and I was hoping to cut that connection. 

Thanks again!

---

### Post by BitJunkie on 2011-07-25
It seems a regression bug has been fixed. I applied the change outlined at [http://www.mail-archive.com/linux-media@vger.kernel.org/msg34771.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg34771.html) and the USBLive 2 is working for me now, at least with mplayer/mencoder.

I may never have to boot Windows again...:D

---

