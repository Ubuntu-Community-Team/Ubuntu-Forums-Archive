---
title: "flash + firefox = crash"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by fissionmailed on 2007-10-19
Ok, this is my story,  I didn't have sound.  But I installed Flash any way so I could as least view it.  I get the sound to work using OSS, Then the sound on the flash doesn't work.  I try something, it doesn't work, so I undid it, but I also install alsa-oss hoping it would work.  Then some one say something about libflash-mozplugin and I  installed it.  The sound works but then Firefox crashes two seconds later.......

Now if I could get the sound on flash to work and the wireless WPA I could really use this laptop. >_<

Thanks again guys.

---

### Post by fissionmailed on 2007-10-19
about:plugins

returns

Shockwave Flash

    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/futuresplash 	Future Splash 	spl 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes



I think some how I've got two running but I don't know how to turn one off. :o

---

### Post by FredB on 2007-10-20
If you install gplflash with synaptic, just remove it using synaptic ;)

I think both are in war, and this is why you're seeing crash.

---

### Post by fissionmailed on 2007-10-20
> **FredB said:**
> If you install gplflash with synaptic, just remove it using synaptic ;)

I think both are in war, and this is why you're seeing crash.

No, I installed it through Macromedia.  I'll fiddle around with it and see what I can do.

Edit: I uninstalled libflash-mozplugin and it works now, but I still have no sound.  Basically the one from Macromedia has no sound and IIRC the one in Synaptic has sound and all but isn't the latest one?  Am I close? I just need to uninstall the the one from Macromedia and then install the other one for sound.

---

### Post by FredB on 2007-10-20
> **fissionmailed said:**
> No, I installed it through Macromedia.  I'll fiddle around with it and see what I can do.

Edit: I uninstalled libflash-mozplugin and it works now, but I still have no sound.  Basically the one from Macromedia has no sound and IIRC the one in Synaptic has sound and all but isn't the latest one?  Am I close? I just need to uninstall the the one from Macromedia and then install the other one for sound.

I will say yes, you're close the solution. I see you're using feisty. Gutsy has a younger flash working version ;)

Anyway, if it works, don't fix it, I mean, if you're ok with feisty, don't upgrade to gutsy if you don't need it :)

---

### Post by fissionmailed on 2007-10-20
> **FredB said:**
> I will say yes, you're close the solution. I see you're using feisty. Gutsy has a younger flash working version ;)

Anyway, if it works, don't fix it, I mean, if you're ok with feisty, don't upgrade to gutsy if you don't need it :)

The thing is, I'm using a 10 year old laptop. -_-  So I don't want an OS that stresses the system too much.  I dunno I might.

---

