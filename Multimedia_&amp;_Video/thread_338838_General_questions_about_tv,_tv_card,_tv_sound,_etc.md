---
title: "General questions about tv, tv card, tv sound, etc."
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by Colonel Forbin on 2007-01-15
So, I moved to Ubuntu Dapper Drake 64 bit last week. I feel like I'm doing pretty well. I got all three of my monitors working, figured out how to get write ability for two external NTFS drives, did some command line apt-get stuff, made permanent mount points for the externals. 

But, I can't get a few things going, and I can't seem to find threads to answer the few questions I have left.

First, I got my tv card going for video signal, but can't get sound. I have sound otherwise. It is a norwood micro. the chipset is  saa7134. Video works under card=3. However, the only app that works is tvtime. I can't get zapping to see any channels, and kdetv hangs at 99% when scanning channels under composite, and hangs if I try to switch to television before the scan. Are there any other tv viewing programs available, free or non-free?

And, I can't seem to get my zen vision M recognized. It charges off of the usb, but doesn't show up anywhere. I want to add stuff to it. What app can I use for this. GNomad2 doesn't seem to work.

Any and all help is greatly appreciated.

And I must say that while it has not been easy to move to Ubuntu, it does seem to be worth it. I am glad to be rid of the Red(mond) Menace.

Nick:-D

---

### Post by Jussi Kukkonen on 2007-01-15
HI,
General advice on DVB cards: visit linuxtv.org. In your case [http://linuxtv.org/v4lwiki/index.php/Saa713x_devices](http://linuxtv.org/v4lwiki/index.php/Saa713x_devices). They may have advice for you and as development on this field is pretty rapid, you may also want to get newer drivers from there  (alternatively you can also wait for the drivers to appear in Ubuntu kernels). 

About the Zen vision: run  ```
tail -f -n0 /var/log/messages
```, plug in the device and post the output here.

---

