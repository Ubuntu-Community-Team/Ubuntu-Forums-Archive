---
title: "External TV tuner"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by ep3w on 2007-09-03
I am looking for an external tv tuner that is compatible with ubuntu/myth tv and windows.  Is there one that is capable of being stand alone at the same time?  Or are all of them capable?  I have seen tv tuners that are specifically stand alone, but I would also like the option of recording tv etc. Basically are normal ones capable of being run stand alone too, assuming just watching TV, not recording or anything like that? I have an extra LCD monitor that came free with my laptop that I want to use, that uses dvi or vga input. I am trying to go fairly cheap.  I don't need HD or anything like that.  Any suggestions on tuners I should check out?  If it is compatible with ubuntu, i am more likely to not mind if it isnt stand alone...Any suggestions for something reasonably priced?

---

### Post by simonn on 2007-09-03
I have two of the following [http://www.twinhan.com/product_terrestrial_7.asp](http://www.twinhan.com/product_terrestrial_7.asp) (basically because they also work with OSX), so I can play and/or record two programs at once. 

Ubuntu does not come with the firmware they need, but google on dvb-usb-vp7045-01.fw and place the file in /lib/firmware and it will be recognized and loaded by the kernel.

I do no know how well they work with myth as I only use mplayer/mencoder with which they work flawlessly. I only have the one monitor also, but find placing a small mplayer window in the bottom right had corner and always on top works fine for me. Recording the raw stream, i.e. no transcoding, uses hardly any system resources other than disk space of ~1.5Gb/hour. Playing uses some, but with little system impact.

---

### Post by ep3w on 2007-09-04
I am guessing you can not use that as a standalone since it is usb powered? I'd prefer one I could use as standalone, too...if it even exists that is.

---

