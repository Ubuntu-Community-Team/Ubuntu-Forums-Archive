---
title: "DVICO Fusion hdtv USB dvb-t tv tuner nightmare!"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by henryhynd on 2007-05-05
Hi all,

Just like to start out by saying i'm new to ubuntu (running feisty on a Dell Inspiron 6000) and I'm really impressed so far. I have three issues to solve before i delete my windows XP partition and go full linux! one of my issues is the following.

As I have a laptop i naturally have a usb tv tuner (DVICO FusionHDTV USB DVB-T), it works great in windows but won't even register in device manager in feisty!

I'm pretty knowledgable with this sort of thing in windows, so i thought i'd go looking for drivers as thats probably the safe place to start, having found some drivers from [http://linuxtv.org/hg/~pascoe/v4l-dvb-test/?ca=7938e85a8396;type=gz](http://linuxtv.org/hg/~pascoe/v4l-dvb-test/?ca=7938e85a8396;type=gz), i couldn't figure out how to install them (being i'm a newbie).

having been looking around the net for hours and coming up empty for a solution to my woes, I thought id ask you guys if you know of a solution (its not for the usb dual, which i've been seeing a bit of in my travels, its the original usb dvb-t box from dvico) or could write a how-to for me?

thanks heaps guys(and girls), i hope to get a response soon!

Henry

---

### Post by Erlander on 2007-05-05
The Divco Fusion HDTV USB2 is recognised out of the box by Feisty.

In terminal if you enter

```
dmesg
```
you will se about two thirds of the way down that it is found "in the warm state".

I feel that Kaffeine is about the easiest application to get going and veiw live TV with.

From Synapatic search for and install Kaffeine.

Then in Synapatic search for Xine and install its ffmpeg codec.

Next open Kaffeine set up your DVB settings, search for channels and start watching.

If you have any trouble get back to me here and I'll see if I can help.

Rob

---

### Post by henryhynd on 2007-05-05
Thanks for replying so quickly, i really appreciate it!

i found that my tuner did infact come up in 'dmesg' but not in warm state. It is in cold, i've pasted the relevant section of 'dmesg' below:

"[   19.156000] dvb-usb: found a 'DViCO FusionHDTV DVB-T USB (TH7579)' in cold state, will try to load a firmware
[   19.220000] dvb-usb: did not find the firmware file. (dvb-usb-bluebird-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[   19.220000] dvb_usb_cxusb: probe of 5-5:1.0 failed with error -22
[   19.220000] usbcore: registered new interface driver dvb_usb_cxusb"


any ideas?

thanks again,
Henry

---

### Post by Erlander on 2007-05-05
Very strange.

Under Edgy I had to download the firmware but not under Feisty.  Can't imagine why it is different for you.

Download the dvb-usb-bluebird-01.fw from:[http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/) and copy the file to /lib/firmware

I had trouble with permissions not allowing me to write to /lib/firmware   You will need to use sudo or if you are a newbie like me gksudo nautilus will allow you to use a gui to do it.

Good luck.

Rob

---

### Post by henryhynd on 2007-05-06
As I write, i'm watching tv! Everything worked out great!

Thanks heaps for your help mate, i really appreciate it!

Cheers again,
Henry

---

### Post by bliffle on 2007-06-17
I have a similar situation with a Diamond HDTV100 USB dongle tuner. It doesn't showup in the 'dmesg' report.

---

