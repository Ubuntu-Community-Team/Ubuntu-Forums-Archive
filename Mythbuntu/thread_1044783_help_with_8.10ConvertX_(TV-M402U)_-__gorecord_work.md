---
title: "help with 8.10/ConvertX (TV-M402U) -  gorecord works but no video"
date: 2009-01-19
forum: Mythbuntu
---

### Post by mixersoft on 2009-01-19
Here's what I've done so far:
[LIST]
[*] downloaded Go7007 patched driver from [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Installation]("http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Installation")
[*] applied patches 4,5,6 from [http://home.comcast.net/~bender647/go7007/]("http://home.comcast.net/~bender647/go7007/")
[*] compiled and installed Go7007 driver
[*] load the driver using:
```

sudo fxload -t fx2 -D /proc/bus/usb/00X/00X -I /lib/firmware/ezusb/hpi_PX-TV402U.hex

```
[/LIST]

The driver loads properly, and gorecord works properly using the following command.
```

gorecord -input 2 -duration 5 -tvchan ntsc-cable:9 test-video.avi

```
But I get no video from Mythbuntu, just green noise. When I open the MythTV backend setup to the Capture Card Setup, it finds the video device on /dev/video0. But in the log window, I see:

```

Can't open DVB frontend (/dev/dvb/adapter0/frontend0)
DiSEqCDevTree, Warning: No device tree for cardid 1

```

everything used to work when I was running some version of 8.04.
What should I do? Gotta get this working before the superbowl.

---

### Post by mixersoft on 2009-01-19
Update: this is what I see in the MythTV Setup Terminal window when I open the capture card setup for the GO7007:

```

Couldn't get handle
eno: No such file or directory (2)
Can't open DVB frontend (/dev/dvb/adapter0/frontend0)
DiSEqCDevTree, Warning: No device tree for cardid 1

```

---

### Post by mixersoft on 2009-01-25
it turns out I needed to create a recording profile for mythtv to tune the convertx properly. Now I can record video using Intrepid, but the volume is very low.

---

