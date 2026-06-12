---
title: "What USB TV/DVB video devices work?"
date: 2011-01-21
forum: Multimedia Software
---

### Post by wkulecz on 2011-01-21
What USB TV/DVB video devices actually work on Ubuntu?

I'm specifically interested in 10.04 and analog NTSC capture. HDTV would not be totally useless, but I'd prefer a cheaper device without it for now.

There is a "master list" at:

[http://www.linuxtv.org/wiki/index.php/Em28xx_devices#Boards](http://www.linuxtv.org/wiki/index.php/Em28xx_devices#Boards)

But there is precious little information about mapping these devices to products you can actually buy.

I have a Hauppauge 950Q and it works, but its not very flexible in capture sizes (i.e. apparently 720x480 is fine, but 640x480 is apparently not)  If I can only have one capture size, it needs to be 640x480.

---

### Post by Chronon on 2011-01-21
Why not transcode the program afterward to the dimension you want?

---

### Post by BicyclerBoy on 2011-01-21
DVB has nothing to do with capture size...
You are thinking of analogue input capture card for STB 'problems' or old analogue tuner cards.

DVB tuners stream mpeg2-ts datastream.
This is not captured/encoded by the tuner card.
Typically MPEG4/10-H264AVC & AAC are used.

Haupaggue have released an HDMI input HD capture card.
This will encode & AFAIK it will stream mpeg2-ts.

---

### Post by wkulecz on 2011-01-25
> I'm specifically interested in 10.04 and analog NTSC capture.

Doesn't anyone read before they post anymore?

---

### Post by wkulecz on 2011-02-16
There is no conveinent place to find this info, but I've found a capture only USB dongle that seems to work well in 10.04

Kworld 2800D.  Its avaible at Fry's and Newegg so its pretty easy to find now that you know it works.  Its standard definition video only, no tuner, and works well with gstreamer, tvtime, etc.

---

