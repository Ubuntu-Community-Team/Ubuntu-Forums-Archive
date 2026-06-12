---
title: "Color problem with ATI xrandr Svideo out"
date: 2008-08-01
forum: Multimedia Software
---

### Post by leeko on 2008-08-01
Hi all,
I'm trying to output my ubuntu/xfce desktop (and eventually mythtv) to my TV-set, but I'm having some difficulties.

I have an ATI radeon 7500 gfx card with S-vhs out. I ran a Svhs-to-composite cable to the front input of my tv (an old RCA model with no other input except composite and aerial). 

I used xrandr to add the 800x600 resolution and set output to the svideo. This worked, and I get a picture on the TV. I set the mode to ntsc, and used xvattr to set video overlay to the svideo/TV. 

All good so far, but - the TV picture is horrible. The text is barely legible, and white text has splotches of red all over it. Colors look all wrong, and any video I try to play looks crazy over-saturated. There are faint nonmoving horizontal lines all over the display, giving the appearance of a "torn" image.

I know that TV-output from consumer video cards is not great, but I'm pretty sure it's supposed to look better than this!

In short, I don't think the TV is happy with the settings used by the video card, but I'm not sure what to try and change next. 

If anyone can provide help, I'd be very grateful.

Thanks in advance, 

Lee

---

### Post by leeko on 2008-08-15
Hi,

bumping this thread, in the hope that someone can help!

Lee

---

### Post by rmtebbot on 2009-04-27
Hi, 

Did you ever sort this? I have the same issue...

---

### Post by leeko on 2009-04-28
I don't remember if I got it working with ATI or not, but I had a similar problem after I switched to nvidia. It turned out to be a wrong s-video cable/connector (wrong number of pins). Switching the cable sorted it out. 

Cheers,

L

---

