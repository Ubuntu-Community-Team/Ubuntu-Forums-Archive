---
title: "Nvidia GeForce 6200 same as 6600?"
date: 2008-10-12
forum: Multimedia Software
---

### Post by jdcnosse on 2008-10-12
So I've read on the internet that some of the GeForce 6200's have the same core as the 6600's, but they just have half of the pipelines masked.

I've also read that you can use RivaTuner on Windows to unlock those extra pipelines, but I was wondering what program would I have to use to unlock the masked pipelines on ubuntu?

---

### Post by manimal347 on 2008-10-12
Yes, I think I've heard the same: that some 6-series cards had some of the pipes disabled so they could create a cheap product that wouldn't threaten the better ones. Depending on your 6200, this might be a possibility for you- Nvidia quicky changed the dies, but initially just used binned chips (so I heard). First, you should enable coolbits in your xorg.conf.

/etc/x11/xorg.conf
Add the line:

Option "coolbits" "1"

below the "Device" header in your xorg.conf. Then, save the file. This enables Nvidia's CoolBits tuning, letting you overclock your card. Given the nature of your question, I thought you might want to do that. It also unlocks extra features in the tool you'll use. 

nvidia-setting (file name as called from terminal) is the offical Nvidia card tuner. Naturally, no hacks of this gravity available for it, but you should still know about it.

NVclock is THE unofficial tool, akin to Rivatuner in purpose.
[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)
(it should be in Ubuntu respositories, too)
[http://linux.die.net/man/1/nvclock](http://linux.die.net/man/1/nvclock)
(a man page)

It should have command line switches to enable extra shaders and or pipelines as your hardware allows. Oh, and just typing nvclock from the terminal launches it. 

You should be able to take it from here, but if not, I'm sure somebody who's done this can help.

---

