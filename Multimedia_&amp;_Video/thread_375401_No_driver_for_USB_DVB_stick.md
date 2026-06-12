---
title: "No driver for USB DVB stick"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by pljones on 2007-03-03
When I got a laptop, it came with a free USB DVB stick, called "MSI PC-TV Mega Sky 580".  It looks like the kernel has recognised the keypad support but not the receiver itself - I've nothing under /dev/dvb.

I'm guessing this is a proprietry, windows-only driver issue, given the "Cls=ff(vend.)" in /proc/bus/usb/devices:
```
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0db0 ProdID=5581 Rev= 1.02
S:  Manufacturer=PC-DTV Receiver
S:  Product=PC-DTV Receiver
S:  SerialNumber=00000001
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=3072 Ivl=125us
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=01 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
```

Is there any chance this is going to work under Linux?

<edit>
Well, according to [the v4lwiki](http://www.linuxtv.org/v4lwiki/index.php/USBVideo), "MSI Mega Sky 580 Both versions are supported. (0db0:5580/1 Micro Star International)".  I shall have to investigate further...
</edit>

<edit>
Right, tracked the em28xx driver down.  It's not in the kernel yet and doesn't compile against 2.6.20 yet.
</edit>

<edit>
Tracked down a patch to the Hg repository to get the em28xx driver to compile against 2.6.20.

But now I'm stuck.
</edit>

---

### Post by pljones on 2007-03-04
Sorry to bump ;)

I've got the v4l repo building cleanly against 2.6.20 and "make insmod" does pretty much what's expected.  However, plugging in the device causes nothing much to happen.

I've no /dev/dvb

/dev/video0 exists.  v4l-info /dev/video0 reports on the vivi driver (a camera).

None of the "HOWTOs" really seems appropriate - I feel like I know so little I don't know what questions to ask!

---

### Post by Mr. J007K4 on 2007-03-13
It seems that we have the same stick. I got mine working with the help of this thread: 
[http://ubuntuforums.org/showthread.php?t=319727](http://ubuntuforums.org/showthread.php?t=319727)

---

### Post by pljones on 2007-04-14
Sorry, never said "thanks": Thanks! :)

---

