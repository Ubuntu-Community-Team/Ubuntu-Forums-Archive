---
title: "Nvidia GT520 or GT430"
date: 2012-03-06
forum: Multimedia Software
---

### Post by EaPendergast on 2012-03-06
Hi all. 
I'm trying to decide which of these video cards is better for Ubuntu 11.10.

Apparently, the GT430 is better not only for the higher price but for its 128 bits bus so, it has to be better.

But no. Mostly because it has some known problems with vdpau and it's not as stable as the GT520. But the GT520 has less features.

Any of you using the GT430? Do you watch mkv's without problems? Perhaps, with the new nvidia drivers, the GT430 is totally supported.

If I'd prefer going for sure, the GT520 has no problems at all, but I think it's a pity to buy a inferior card only for its stability.

What do you think?
Thanks in advance for any answer

---

### Post by BicyclerBoy on 2012-03-06
In the most basic terms...
The video cards performance with VDPAU depends on (2) separate components.
Bit stream decoder & shaders.

The container (mkv, mpeg2-ts, mpeg4 etc) is not the issue, it is the correct/standardised use of the video encoder.
Then your media player has to be able to push the data into the h/w decoder.
Feature set C added mpeg4-asp.
Feature set D cards include GT520.

The GT520 has the better/best decoder as it can decode (2) H264 HD streams (or 4K ?).
The GT240 & GT430 have better shader performance.
The GT430 is smaller card with similar performance (bit slower) than GT240.

The shaders are used for post decode processing like scaling, denoise, sharpen, colorspace, & most importantly VA de-interlacing.
There are 3 types of VDPAU de-interlacing; VectorAdaptive is most demanding.
Not all these shader features are needed for the same material.
i.e. you don't need hqscaling for HD but do for SD DVDs.

There has been recent discussions on mythtv forums that indicate that GT430 can not maintain scaling & VA de-interlacing at all times.
Summary:
So all depends on your source material.
OTA broadcast HD needs VA deinterlacing.
DVD & other SD needs hqscaling & little sharpening & VA de-interlacing.
BD VC1 24p should be no problem on GT520
BD H264 i50/i60 very rare.

If you want to wait then the best card would probably be the OEM GT540 or the new Kepler GT640.
Right now I would buy another GT240 as the current offerings are not good enough (520)/not available (OEM 530/535/540).

---

### Post by EaPendergast on 2012-03-06
great information!!! thanks a lot.

I forgot to mention that I need the card to be low profile and I can extract from your words that the GT520 is right now the best choice.

Thanks again, you've helped me a lot

---

### Post by Yellow Pasque on 2012-03-06
Interesting article/discussion here: [http://phoronix.com/forums/showthread.php?57123-NVIDIA-GeForce-GT-520](http://phoronix.com/forums/showthread.php?57123-NVIDIA-GeForce-GT-520)

---

### Post by BicyclerBoy on 2012-03-07
The GT520 may be okay for some users...

It is not recommended for broadcast TV (interlaced) especially i60.
After using VA deinterlacing & hq scaling (DVD etc) on the GT240 there is no way I would buy a GT520..

But the GT520 is very low power & cheap..it has a more powerful decoder (futureproof).
It is a shame the GT535/540 is only OEM mobile.

The GT520 is so cheap that if you have to replace it with a GT630/640 in one year, so what..

The playback problems with GT430 could to be related to the desktop manager settings (unity & compiz) redirection.
Redirection causes VDPAU to use blitter for video presentation.

---

