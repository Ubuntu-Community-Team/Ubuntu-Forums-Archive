---
title: "Problems with LIRC0 missing"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by pluto1209 on 2007-06-08
Hi,

I'm a newbie running Ubuntu 7.04 and MythTv with a PVR-150 card installed, in general everything is working fine, I can watch and record TV, however, sometimes my Lirc0 device is missing, either right after reboot or some times it disappears after a while.
So far I've figured out to fix it by booting into my Windows XP, let it start up, and then reboot back to Ubuntu and I get the Lirc0 back. I made be able to live with this issue, if I can just find another workaround than booting into Windows XP, so any suggestions are welcome. Also if anyone have similar problem, and know the solution to it, I would like that as well :D

-Pluto

Here is some info

This is what I see sometimes right after reboot
[INDENT]ls /dev/lirc*
/dev/lircd[/INDENT]

I should see
[INDENT]ls /dev/lirc*
/dev/lirc0  /dev/lircd
[/INDENT]

Here is some printouts that I thought I would capture
$ dmesg | grep ivtv
[   15.345730] ivtv:  ==================== START INIT IVTV ====================
[   15.345734] ivtv:  version 0.10.1 (tagged release) loading
[   15.345736] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   15.345738] ivtv:  In case of problems please include the debug info between
[   15.345740] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   15.345743] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   15.345805] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   15.346361] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   16.018341] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   16.241106] ivtv0: Encoder revision: 0x02050032
[   16.241109] ivtv0: Recommended firmware version is 0x02060039.
[   16.304439] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   16.304440] ivtv0: reopen i2c bus for IR-blaster support
[   16.386384] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   16.586699] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   20.636124] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   20.690183] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   20.690441] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.690736] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.690906] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   21.052115] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   21.052240] ivtv:  ====================  END INIT IVTV  ====================
[   32.876384] lirc_pvr150: ivtv i2c driver #0: no devices found

Looks to me that the device is not responding or hanging right after reboot, but I've never seen this issue in Windows. Perhaps ivtv can't initialize my card correctly :confused:

#lsmod | grep lirc
lirc_pvr150            19636  0 
lirc_dev               15988  1 lirc_pvr150
ivtv                  134544  1 lirc_pvr150
i2c_core               22656  9 lirc_pvr150,i2c_ec,wm8775,cx25840,tuner,ivtv,nvidia,i2c_algo_bit,tveeprom

---

