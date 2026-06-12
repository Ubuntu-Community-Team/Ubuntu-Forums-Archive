---
title: "ATI Rage 128 Ubuntu Slow"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by ART_Adventures on 2006-09-04
Dear People,

I have just installed Ubuntu on an older machine of mine. I've not used Linux before and I think there might be a problem relating to my graphics card (ATI RAGE 128). Everything is running slow. It takes a long time for things to load and to redraw themselves.

I took a look at this page:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But it doesn't seem to mention ATI Rage; only Radeon.
I'm not really sure what I'm supposed to do in order to get this working so it can run faster and smoother and generally become usable.

Can anybody help me?

Kind regards.

---

### Post by shdgrao on 2006-09-04
Did you take a look in the ati web page?? Maybe there you have the drivers for your graphics card for linux.

What is for sure is that if you have just installed ubuntu you don't have 3d aceleration until you install your graphics cards drivers.

---

### Post by ART_Adventures on 2006-09-04
Ok. thanks, I didn't know that. I thought perhaps since the ATI Rage 128 was an old card that the OS might ship with some drivers for it, especially since Windows XP didn't have this problem when installed on the system before.

I've checked the ati.com site but cannot seem to find linux drivers for a rage 128. Does anybody know how I install these drivers for linux, keeping in mind that I've not installed anything on Linux before.

Thanks.

---

### Post by sp4rd on 2006-09-04
Ati rage 128 with 3d acceleration(dri) should be supported out of the box with ubuntu/xorg.  First make sure your card is properly seated in it's agp/pci slot.  I've had a few instances where this has happened to me where it seems really slow, then I check my cards and discover that it's sort of sitting cockeyed in the slot.  If they seem alright next look in your /var/log/Xorg.0.log to see if the right driver(ati) is being loaded and is picking up your card.  Somewhere at the bottom of the log should tell you if direct rendering is being activated.  Some r128 cards only have 8mb on board so sometimes the driver will fall back to indirect rendering which is alot slower.Try 800x600 then 640x480 screen sizes if you have one with 8mb to get direct rendering.  You may have to set the max screen resolution in your /etc/X11/xorg.conf to 800x600 and restart your xserver, also select the depth 16 in your xorg.conf .You can also run the command glxinfo in a terminal and that should also tell you if direct enabling is enabled.

---

### Post by ART_Adventures on 2006-09-05
Ok. I will try this and post back if there's a problem. I don't know what it means, or it's relevant, but during the install of ubuntu it said:

"Loading hardware drivers...

shpchp : SHPC_init cannot reserve MMIO region

base address not set - upgrade BIOS or use force_addr=0xaddr"

Thanks.

---

