---
title: "Using Windows Asio Drivers with Jack"
date: 2011-07-04
forum: Multimedia Software
---

### Post by Schlaefer on 2011-07-04
Hi,

i know, that jack does support Asio with the -a option. But is it also possible to use Windows Asio drivers?
I was wondering if I could for example use this mixer, because it's not listed in the ALSA SoundCard Matrix but has Asio drivers for Windows:
[http://www.behringer.com/EN/Products/2442FX.aspx](http://www.behringer.com/EN/Products/2442FX.aspx)

---

### Post by gordintoronto on 2011-07-04
> **Schlaefer said:**
> But is it also possible to use Windows Asio drivers?...

To the best of my knowledge, that is not possible. 

Have you exhausted all possible Google searches?

When the device is plugged in to your computer, what does the (accessories/Terminal) command:
lsusb
produce?

I found this quote: "I can't see any need for using ASIO on Linux - ALSA is low latency already."

---

