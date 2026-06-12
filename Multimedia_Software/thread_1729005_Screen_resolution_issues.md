---
title: "Screen resolution issues"
date: 2011-04-14
forum: Multimedia Software
---

### Post by manymanymo on 2011-04-14
I'm having a problem setting the resolution on ubuntu 10.10 to the desired setting of 1920x1080 60hz maximum resolution available is 1200x800. Tried Mike Reed's article "Guerrilla Tactics to Force Screen Mode in Ubuntu" but when trying to set the resolution in XRandR or through preferences results in the error message "could not set configuration crtc 262" with no change in resolution.

Hardware is capable, It's an older matrox graphics card with DVI output to HDMI cable into a 42" display

Software does not detect display type

Can anyone help? or is there something i'm overlooking?

---

### Post by realzippy on 2011-04-14
**Edit:**
*which* matrox graphics card do run?If not sure,post output from:
```
lspci |grep VGA
```
Why are you sure your card is capable of HDMI ?

...and welcome to the forum!

---

### Post by manymanymo on 2011-04-19
Hi, thanks for getting back to me so quickly, Have been out of town.

The card is a Matrox P650 specced here: [http://www.matrox.com/graphics/en/products/legacy/p_series/p650/](http://www.matrox.com/graphics/en/products/legacy/p_series/p650/)

The monitor is a Toshiba Regza 42inch 42AV635DB specced here:
[http://www.soundandvision.co.uk/tv/lcd/toshiba-42av635db#_](http://www.soundandvision.co.uk/tv/lcd/toshiba-42av635db#_)

As mentioned DVI to HDMI cable in use, Picture fully visible but no display type shows as "unknown" presumably to do with HDMI compatibility with older DVI card.

1280 x 1024 max resolution

Thanks again

---

