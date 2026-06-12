---
title: "Flash randomly stops working in Firefox, Jaunty"
date: 2009-07-20
forum: Multimedia Software
---

### Post by Shekibobo on 2009-07-20
This is a pretty new problem, and it's happening more and more often.

Flash objects on websites will randomly stop loading in Firefox 3.0.11.  They might work for the first few minutes, maybe for the first few hours of running Firefox.  But after a while, flash applets just stop loading.  I get a blank area where the object should be, but nothing happens.  I need to restart Firefox in order for it to load.  

Sometimes this happens when I'm playing yahoo games such as Text Twist.  At some point, I'll hear a clicking noise, sometimes the sound stops working, and sometimes the 
flash object just disappears altogether.  It's getting annoying.  Is there any way to fix this?

**Shockwave Flash**

 File name:  npwrapper.libflashplayer.so 
Shockwave Flash 10.0 r22   
MIME Type Description Suffixes Enabled    
application/x-shockwave-flash Shockwave Flash swf Yes   
application/futuresplash FutureSplash Player spl Yes

---

### Post by deshao on 2009-07-21
I have the same issue:

Flash will work when I first open firefox but after some amount of time it will not display at all.  If I close and reopen Firefox, it works again.

---

### Post by psyke83 on 2009-07-22
The problem is libflashsupport - remove it from your system. For more information, see my PulseAudio guide and see the linked bug against libflashsupport.

---

### Post by Shekibobo on 2009-07-22
Also confirmed by Synaptic Package Manager (which doesn't even show an option for having libflashsupport installed).  Apparently it doesn't exist on my system.  Any other ideas?

```
$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not installed, so not removed
E: Couldn't find package flashplugin-nonfree-extrasound
```

---

### Post by elvisd on 2009-07-22
Same here on 64 bit sys

---

### Post by AKADAP on 2009-07-22
This problem was on 8.10 and is still on 9.04 for me. I also do not have libflashsupport installed on my 64 bit system.

---

### Post by elvisd on 2009-07-23
I have tried following an howto  for pulse and installing the plugin from the latest adobe flash 10 64bit release.

Now it seams a bit more stable, and finally sound works again.

check out [http://elvisd.blogspot.com](http://elvisd.blogspot.com) for links

---

