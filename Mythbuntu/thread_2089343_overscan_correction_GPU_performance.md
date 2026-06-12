---
title: "overscan correction GPU performance"
date: 2012-11-29
forum: Mythbuntu
---

### Post by jonnybignote on 2012-11-29
Hey all

My new frontend Zotac Zbox id41 is running Mythbuntu 12.04 on a Sony Bravia 55".

I'm losing all of the top toolbar.  I spied the overscan correction slider in the Nvidia setup utility which took care of it.  

The nagging feeling I have though is that the GPU on the ZBox (which is already taxed even with VDPAU) is doing all the heavy lifting with this correction.  Am I totally wrong?  Am I right and there is another way to do it?

If anyone could shed some light on it for me that would be great.

Thanks

---

### Post by jksj on 2012-11-29
If your TV thinks it is connected to a TV source like a set top box it will assume 16:9 aspect ratio and chop off all the picture edges. Thats what overscan means. There is normally a 'ratio' control on the TV remote which allows you to select 1:1 aspect ratio where all the pixels will be displayed.
I get this problem frequently but not all the time with an HDMI connection to a LG TV. I have not found away to set 1:1 mode permanently.

---

### Post by jonnybignote on 2012-11-29
hnmmm

I seem to get offered 16:9, 4:3 or 'wide' as the only option.  Overscan correction fixes it in nvidia settings, but I'm just not sure if that puts extra demand on GPU

---

### Post by jksj on 2012-11-29
Look for something like digital overscan  .. turn off.
& 'Full pixel' mode in the settings .. turn on.

---

### Post by nickrout on 2012-11-29
> **jksj said:**
> Look for something like digital overscan  .. turn off.
& 'Full pixel' mode in the settings .. turn on.Precisely:

[http://forums.whirlpool.net.au/archive/1113758](http://forums.whirlpool.net.au/archive/1113758)

---

### Post by jonnybignote on 2012-11-29
Thanks all for the help - had to hunt for it a little

under 'Auto Display Area' and turn it off, then select 'Full Pixel'.  Now I'm good to go and it looks a little sharper I think.

Thanks

---

### Post by nickrout on 2012-11-29
> **jonnybignote said:**
> Thanks all for the help - had to hunt for it a little

under 'Auto Display Area' and turn it off, then select 'Full Pixel'.  Now I'm good to go and it looks a little sharper I think.

ThanksThe ability to do "full pixel" (also called various other things by other manfacturers - "just scan" is one - is a prime thing I look for in buying a TV.

Most recentish ones seem to be OK, earlier LCD Panasonics for example don't.

See also [http://pixelmapping.wikispaces.com/Pixel+mapping+explained](http://pixelmapping.wikispaces.com/Pixel+mapping+explained)

---

### Post by Lester_Burnham on 2012-12-01
On my Toshiba, it needs to be in "game" mode.

---

