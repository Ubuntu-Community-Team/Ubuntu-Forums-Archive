---
title: "ATI restricted driver + Compiz + Dual Monitors"
date: 2008-04-24
forum: Multimedia Software
---

### Post by leach on 2008-04-24
I've had trouble finding a definitive answer to this every time I decide to try and enable dual monitors. 
Is it possible using any method to have dual monitors (with different resolutions) running from one ATI card using the restricted driver and still be able to use compiz?  I'm using Hardy Release Candidate and an ATI X1950pro. Thanks in advanced.

---

### Post by leach on 2008-04-24
bump

---

### Post by tlepes on 2008-04-24
bump +1

---

### Post by kraftmayo on 2008-04-26
From what I can tell, still no....

Not to hijack your thread, but I'd love to know how to get dual monitors sans compiz - I cant even seem to do that with Hardy.

I installed the restricted driver, and it caused artifacting all over my desktop - not unusable, just very annoying and un-pretty.  So now I'm back to the standard driver.

---

### Post by deathsushi on 2008-05-28
I have managed to accomplish this in the past by stacking the monitors vertically, rather than horizontally. This will allow a resolution of 1280x1024 on both monitors, and maintain the use of the cool 3D effects.

Alas, I'm trying to figure out how to reenable this functionality right now, as I've had to reinstall :(.  Will try to keep you informed of any luck I have.

---

### Post by adz_c on 2009-07-12
You can't run them side by side because the ATI card will only support a maximum composite resolution of 2048 x 2048 over all screens. That's how deathsushi managed to run them vertically. I think people are getting better results with Nvidia cards but I haven't yet tried and I don't know their limitations. All I know is there is a guy on youtube with 6 monitors all running compiz, and I want it!

I ran into this issue a while back. You can't even run one monitor with compiz and one without because you won't be able to drag between screens. This is frustrating as I am not too bothered about compiz but notice most docks require compositing and I really want to use a nice dock.

---

### Post by markbuntu on 2009-07-14
Well, that particular card may have that problem but I sort of doubt it and my HD3650 does not. Currently I have 24 and 22 inch monitors running a big desktop with compiz on Hardy Heron. 

Note:If you are using one of the latest drivers (9.4 or later) you need to disable randr to use CCC for a big desktop or to use xinerama.

---

