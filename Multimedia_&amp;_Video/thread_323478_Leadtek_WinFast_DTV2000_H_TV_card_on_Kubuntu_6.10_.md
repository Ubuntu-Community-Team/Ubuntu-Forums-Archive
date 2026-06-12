---
title: "Leadtek WinFast DTV2000 H TV card on Kubuntu 6.10 Edgy"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by iwan-zx on 2006-12-22
Hello,
For last few days I've been trying to make my new **Leadtek WinFast DTV2000 H** TV card working on **Kubuntu 6.10 Edgy**. This is a hybrid (analog / DVB-T) TV card with Conexant CX23881 / CX22702 chipsets.

I installed the newest kernel 2.6.19.1, which is said to have a support for DTV2000 H.

Tuner is connected to analog source (cable TV, signal : PAL-DK / europe-east).

My goal for the time beeing is to watch only analog programs witch this tuner, but when I try to find any channel using applications like *xdtv, kdetv, tvtime*, no channel is found.

It seems that software doesn't control the tuner in any way - when I set frequencies manually in application, frequency on the tuner doesn't change, there is still the same white noise on the screen.

Module cx8800 seems to work ok, there is also a /dev/video0 device on the system.
Card type is autodetected correctly (as type 51).

Do You have any idea what can be wrong?
Many thank's in advance :)

---

### Post by JDahl on 2006-12-29
I have the exact same problem; I am trying to use this card with analogue cable TV in Denmark
(Stofa TV).

I can confirm that card appears to be card seems to auto-detected correctly with kernel
2.6.19.1,  but I don't know how to chose between CABLE TV input and ANTENNA TV input.

Using xdtv and xawtv, I am able to change the tuner, and get a signal which is resembles
a picture. I experimented with combinations of PAL-BG, PAL-DK, east European and west European frequency table,  but so far I didn't manage to set it up correctly.

I also tried Mythtv 0.20,  but that didn't help either.  With mythtv there are several capture
cards settings you can chose that all seem to correctly identifed, e.g.,  V4L analog,  DTB-T, 
MPEG2 capture,  but I didn't get a signal with any of those either.

If anyone has experience setting up a tuner card with Ubuntu for cable TV in DK, it would
be great if you could write up a small howto on what device to use, frequency tables, PAL
etc.

---

