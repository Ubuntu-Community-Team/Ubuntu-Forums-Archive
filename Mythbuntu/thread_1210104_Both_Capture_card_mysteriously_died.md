---
title: "Both Capture card mysteriously died"
date: 2009-07-11
forum: Mythbuntu
---

### Post by krazymad on 2009-07-11
Both my PVR 250 cards all of a sudden just died.  Tuner 0 was happily recording at 2 hour show and 39 minutes (5:39am) into it, it flickered for 2 seconds then just static/snow.  When I use tuner 0 now, its just static/snow, same with tuner 1.  Its as if someone unplugged my cable.



**_My troubleshooting steps in the order I did them_**

**Tested cable connection**
Input is analog cable.  
I tested the cable by connecting a TV to the cable itself and verified there is still video and sound, so I know it isn't the cable.  The static/snow did get just slightly darker when I disconnected the cable from the capture cards.

**Tested capture cards**
I tested the tuners manually by running:
"cat /dev/video0 > ~/test.mpg" then "mplayer -vo xv ~/test.mpg" result was static/snow.
"cat /dev/video1 > ~/test.mpg" then "mplayer -vo xv ~/test.mpg" result was static/snow.

**Rebooted**
I come from the world of windows, so of course when something goes wrong, you reboot to fix it.  I rebooted my whole linux box and when it came back up I tested the capture cards again, still static/snow.

**Root**
I then tried testing out the capture cards as root, hoping I'd get lucky and for whatever reason it was a permissions issue, nope.  Running the manual tuner testing as root still produced just static/snow.

**dmesg**
I ran "dmesg | grep ivtv" and got this output:
myth@home:~$ dmesg | grep ivtv
[   40.702228] ivtv:  Start initialization, version 1.1.0
[   40.702320] ivtv0: Initializing card #0
[   40.702322] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   40.723181] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   40.820037] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   41.131767] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   41.356745] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   43.140949] msp3400 2-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[   43.216937] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   43.216949] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   43.216961] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   43.216972] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   43.216984] ivtv0: Registered device radio0 for encoder radio
[   43.216986] ivtv0: Initialized card #0: Hauppauge WinTV PVR-250
[   43.217042] ivtv1: Initializing card #1
[   43.217045] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   43.244820] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   43.251201] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   43.360991] saa7115 3-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #1)
[   43.627431] msp3400 3-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #1)
[   43.685937] ivtv1: Autodetected Hauppauge WinTV PVR-250
[   43.722704] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   43.722728] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   43.722749] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   43.722769] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   43.722771] ivtv1: Initialized card #1: Hauppauge WinTV PVR-250
[   43.723281] ivtv:  End initialization
[   71.039537] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   71.236549] ivtv0: Encoder revision: 0x02060039
[  129.739588] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[  129.938646] ivtv1: Encoder revision: 0x02060039
myth@home:~$ 

After which I tried testing the cards manually again, got nothing but static /snowagain.

**lspci**
I ran lspci -v and got this:
05:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 250
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at dc000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

05:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 250
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>


**Logs**
I checked all the logs (system, daemon.log, debug, kern.log, messages, user.log) for any errors or anything for around 5:39am (time it went from happily recording picture/sound and died to static/snow) and don't see any entries for that time.
[B]
Anyone have any ideas??[/B]

---

### Post by andrewc6l on 2009-07-11
I don't know much about the PVR 250, but is there a chance it has lost a table that maps channels to frequencies somewhere? My capture cards have something like that, and if you're not tuning to the right frequency you just get snow.

VLC lets you specify the frequency directly:
[http://www.videolan.org/doc/streaming-howto/en/ch10.html](http://www.videolan.org/doc/streaming-howto/en/ch10.html)

Also, if broadcasters in your region are messing about with digital transmission, you might find stations changing frequency. Sometimes digital-capable TVs will mask this, so check with an analog TV to make sure the station really is on the air. (I'm assuming you're using OTA - if you're capturing cable, make sure you haven't changed to use antenna instead of cable frequencies.)

---

### Post by krazymad on 2009-07-11
> **andrewc6l said:**
> I don't know much about the PVR 250, but is there a chance it has lost a table that maps channels to frequencies somewhere? My capture cards have something like that, and if you're not tuning to the right frequency you just get snow.

VLC lets you specify the frequency directly:
[http://www.videolan.org/doc/streaming-howto/en/ch10.html](http://www.videolan.org/doc/streaming-howto/en/ch10.html)

Also, if broadcasters in your region are messing about with digital transmission, you might find stations changing frequency. Sometimes digital-capable TVs will mask this, so check with an analog TV to make sure the station really is on the air. (I'm assuming you're using OTA - if you're capturing cable, make sure you haven't changed to use antenna instead of cable frequencies.)


Good ideas, but I'm running analog cable as in the input.

---

