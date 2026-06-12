---
title: "Gradients don't save correctly.  Colors acting strange."
date: 2009-07-09
forum: Multimedia Software
---

### Post by nyahkon on 2009-07-09
I switched to Ubuntu with this new laptop.  Specs are high, so that isn't the problem.

What's happening is that if I try to save any graphics as a JPG/GIF/PNG in GIMP -or- Photoshop which have a gradient, the resulting image's gradient is always choppy.  Also, certain colors simply won't save correctly unless I save at 100% image quality.  It's ridiculous.

I've been doing graphic design for over five years, so *I know how to save correctly*.  It's nothing I'm doing wrong.  I think there must be some sort of problem or setting in Ubuntu that is causing this, but I have no idea what.

Can anyone help me out?  I would really appreciate it.

Thanks.

---

### Post by graphius on 2009-07-09
I use Ubuntu for my photography, so I know it works well. I am guessing that your bit depth is too low, either when saving (which you say it isn't) or displaying. You need to set your display bit depth to at least 24 bit. I am using a proprietary nVidea card, so I am not sure how to change your settings. Maybe someone else can chip in.

You should also check your saved files on another computer, or save them as a tif, just to make sure I am right. If they still look poor on a properly set up system, then it is a setting during save. Maybe over compression, since jpg, and especially gif, are not necessarily "high quality" formats. PNG can be equivilant to tif, but it can also be compressed to cr**.

---

### Post by nyahkon on 2009-07-10
I checked on a Windows machine and the gradients look just fine. So it must be some setting with my computer. Any idea what? It's a brand new laptop with nice CPU, 4gb ram, etc.
 
I am using an nVidia GeForce 9600m GT 512MB video card with properly set drivers (from the nVidia website (though I may change back to the ones Ubuntu provides)) and the video card settings have it running at 24bit color, but perhaps there is a system setting somewhere that is restricting my colors? I **_really_** need some help with this. Graphic design is very important to what I do; I need to get this taken care of ASAP.
 
Thanks.

---

### Post by graphius on 2009-07-10
Hmm, It really sounds like a bit depth problem to me. I am using the nVidea restricted drivers for my, somewhat aged, GeForce FX 5200 with 128M. I don't do any 3D, but I am very fussy about my photography.
I found a how-to [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#seealso") that has a troubleshooting section.

What programs are you viewing the files in?
When you create the files in Photoshop (in wine?) or Gimp, do they look fine? How about viewing images on the web, through Firefox?
I have a simple image on my website [here]("http://klughammer.dnsalias.com/kg/gallery2/main.php?g2_itemId=496"),(klughammer.dnsalias.com) that has a smooth black to white gradient and basic colours.

---

