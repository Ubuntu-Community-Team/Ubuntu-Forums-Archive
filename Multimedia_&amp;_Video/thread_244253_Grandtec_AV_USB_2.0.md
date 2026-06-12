---
title: "Grandtec AV USB 2.0"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by Paul_UK on 2006-08-26
I have a "Grandtec AV USB 2.0" USB video input/capture device.  Does anyone know if it is possible to use these with Ubuntu 6.06?  The website at [www.grand.com.tw](www.grand.com.tw) only has Windows drivers, as expected.  Camorama gives an error saying "Could not connect to video device (/dev/video0)".

it's not a big deal if I can't get it to work as I only need to use it for something at work for a couple of weeks.  But it would be better if I didn't have to boot into Windows XP to do it (especially since I've been telling people how good Ubuntu is!).

Thanks!

---

### Post by garton on 2006-10-12
> **Paul_UK said:**
> I have a "Grandtec AV USB 2.0" USB video input/capture device.  Does anyone know if it is possible to use these with Ubuntu 6.06?  The website at [www.grand.com.tw](www.grand.com.tw) only has Windows drivers, as expected.  Camorama gives an error saying "Could not connect to video device (/dev/video0)".

it's not a big deal if I can't get it to work as I only need to use it for something at work for a couple of weeks.  But it would be better if I didn't have to boot into Windows XP to do it (especially since I've been telling people how good Ubuntu is!).

Thanks!

Did you ever find a solution to this? I have a device just like it that I'm trying to bring to life under Ubuntu 6.06.

---

### Post by Paul_UK on 2006-10-14
No.  No responses here as you can see, and I couldn't find anything with Google.  So this seems to be another thing that Windows can do but Linux can't.  :(

---

### Post by garton on 2006-10-16
As I understand it, the chip itself within the device (called SAA7113H) is supported in linux. There may be a way to make the em2880 module handle this device, which it does not do right now.

---

