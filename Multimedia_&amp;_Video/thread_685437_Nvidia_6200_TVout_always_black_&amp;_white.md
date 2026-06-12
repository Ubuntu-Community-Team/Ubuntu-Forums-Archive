---
title: "Nvidia 6200 TVout always black &amp; white"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by lid2000 on 2008-02-02
I'm going mental trying to figure this out, and have checked pretty much every site on the Internet for anything that could work, but no matter what, I can't get my 6200 to spit out a colour TV signal.

When the computer is booting, it'll do the POST screen in colour (the Energy logo etc), the Ubuntu boot splash screen is in colour, but as soon as X loads, it's all black and white. I'm running the latest driviers, installed with Envy.

If I run X with the vesa driver, I get colour on the TV. If I run it with the nv one, I get garbled pink and blue flashing lines.

I've tried using the newb setup guide here, and got black and white. Then I used the nvidia-settings thing to try and configure it, same result. I messed aroung with the hue setting in nvidia-settings in the hope it was just something stupid like that, but alas, nope. I can't get to the computer at the moment, but I'll post my xorg.conf file as soon as I can. In the meantime, has anyone got any ideas that I could have overlooked? There doesn't seem to be any errors in the X log.

It's a Gigabyte Geforce 6200, has 1xDVI and 1xSvideo on it. I'm using an adaptor to convert from Svideo to composite. Tried the different TvOutputFormat options, no difference. I'm totally lost. This is the second card I've attempted to get TV out working in with this installation now (previously an ATI 9200SE), and I'm really at my wits end.

---

### Post by nuclearwasted on 2008-02-24
Just a thought, Try using a regular svideo cable. I've seen svideo->composite cables that do only b/w when plugged in backwards (and by backwards I mean svideo into the computer and composite into the tv) 

I'm getting garbled pink/blue lines with mythtv (xv) and my screensavers (possibly also xv) and a nvidia 6200, but my tvout is in color.



'every site on the internet' ????? holy cow!

---

