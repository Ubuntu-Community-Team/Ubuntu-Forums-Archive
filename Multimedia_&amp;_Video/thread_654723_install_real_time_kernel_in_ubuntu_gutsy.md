---
title: "install real time kernel in ubuntu gutsy"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by ZeldaFan on 2007-12-31
How do I install the real time kernel in ubuntu gutsy. I don't have ubuntu studio installed and I don't want to go through an ubuntu studio installation to get the kernel. Is there a way I can just install that kernel and get an option to use it in my grub menu? I wanted it to help speed up my video conversion times with avidemux. 
Also is the real time kernel fully functional or is it pretty buggy? Quite simply, will it mess up my computer? I am using a laptop by the way if that makes a difference at all (but I don't care about the battery life with the RT kernel though, because it'll be connected to AC power when I use it).

---

### Post by logos34 on 2007-12-31
> sudo apt-get install linux-rt

I can't hibernate or suspend using the -rt kernel (x64), but maybe you'll have better luck.  IT sure runs faster.

---

### Post by steveneddy on 2008-01-04
> **logos34 said:**
> I can't hibernate or suspend using the -rt kernel (x64), but maybe you'll have better luck.  IT sure runs faster.

I have the very same opinion of the -rt kernel.

Runs great and very snappy.

But no suspend, and I use suspend lots at work AND home.

:popcorn:

---

### Post by ZeldaFan on 2008-01-06
Yea rt kernel worked fine with me, but I didn't try the suspend option. Don't really use it anyway.

---

### Post by rjmoerland on 2008-05-21
Here on Gutsy, RT kernel runs fine but after suspend my screen is totally black, and I need to reboot. Otherwise, no problems.

---

