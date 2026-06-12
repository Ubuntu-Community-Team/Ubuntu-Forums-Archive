---
title: "Nvidia driver not working"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by kerss on 2007-05-18
I know there must be other posts about this, but none really seemed to be about the same...

Basically, I have a notebook with a Nvidia GeForce Go 6600, and would very much like to use the proper Nvidia drivers instead if nv, which doesn't seem all that. The Nvidia drivers worked flawlessly in 5.10, but I can't get it to work in 7.04.

I used the restricted driver manager, and everything seemed to be ok. But upon restart, X server appears with an error message, and after reading its logs, this seems to be the problem:

"can't open /dev/nvidia0"
"the nvidia kernel is not accepting interrupt signals from the device"

(more or less verbatim). Upon further research, /dev/nvidia0 seems to be 0 bytes, so I guess that's where the problem lies, but I have really no idea... The PCI address in xorg.conf is correct. 

I really hope someone can help, as some eye candy would be appreciated... :)

---

### Post by kerss on 2007-05-19
I'm still pulling my hair out over this...

I've even tried envy (that downloads from Nvidia, and compiles), but I still get the exact same thing. The short log file has a message saying that /dev/nvidia0 could not be opened, then  a message saying that the kernel isn't accepting interrupts from the nvidia device.

The long log file has a lot of stuff going on, apparently reading or writing stuff (like colour depth) from/into nvidia(0), which I guess might be /dev/nvidia0. Then it displays the same message as in the other log (about the kernel not accepting interrupts), and it unloads all the modules again.

As you can probably tell, I'm not exactly a Linux guru, so I would really appreciate help. The nvidia drivers worked flawlessly in 5.10, and there aren't any problems with neither card nor drivers in Windows. I really don't see why this shouldn't work!!!

---

### Post by psyke83 on 2007-05-19
kerss,

Unfortunately I've never seen this problem so I can't comment, but you may have more luck posting here: [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Your post will be seen by a nvidia linux developer there.

---

### Post by kerss on 2007-05-19
But is /dev/nvidia0 supposed to be 0 bytes? Could someone with the nvidia driver please check...? I guess it would have been too easy if one broken file was the problem, but a boy can dream :)

---

### Post by siucdude on 2007-05-21
I have been posting over this issue few times, and no luck I have laptop with nvidia go 6600 and no luck so far.  I did have it working under dapper but not since then.  let me know if you get anything.

Thanks

---

### Post by dabl on 2007-05-21
Did you try the Envy installer -- it is the easiest method I have found to install the proprietary Nvidia driver:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

;)

---

### Post by siucdude on 2007-05-21
Yep, tried, I don't think it works for the Geforce GO 6600,

---

