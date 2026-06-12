---
title: "Using xvidtune?"
date: 2008-06-02
forum: Multimedia Software
---

### Post by fizban9 on 2008-06-02
I'm trying to adjust my screen so that it fits properly on my HDTV.  I think I can do it using xvidtune but everytime I try and change something it says:

> Sorry:  Yoy have requested a mode-line
That is not possible, or not supported by your
hardware configuration

I'm running Gutsy Gibbon on an AppleTV.  Everything runs fine, I just need to adjust the screen, it goes of all the edges.  

Thanks for the help.

---

### Post by fizban9 on 2008-06-02
If no one knows how to make xvidtune work, can anyone point me to a guide on modelines?  I think I can tweak those to make my screen fit but I don't want to mess with it until I know what I'm doing.

Thanks for the help.

---

### Post by fizban9 on 2008-06-03
Ok, I found a website that gets really down and dirty with modelines, but it doesn't really talk about it in a utilitarian way.  It says what they mean, but not what changing them would do.  It has you generate them in xvidtune (which doesn't work for me)

[http://howto-pages.org/ModeLines/](http://howto-pages.org/ModeLines/)

What I can gather, and someone here tell me if I'm wrong, is that on a modeline:

> Modeline "1024"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

hdisp		1024
hsyncstart	1080
hsyncend	1184
htotal		1344


Hdisp is how many pixles is sends out.  Hsyncstart is when it sends out a signal that means "end of line."  Hsyncend is when it stops sending that singal and htotal is when it starts over.

Sooooooooooooo, the 24 millions dollar question that I'm too tired to try tonight is........................If I adjust hsyncstart will that mean it ends the line sooner and thus,make it smaller?  

Sorry if my writing is getting weird, it's late and i've been working on this issue for many hours over several days.

Hopefully someone out there can make sense of it all.

---

### Post by aeiah on 2008-06-03
when i was digging around sorting out my overscanning issue i came across something that explained it, but it involves calculating each value listed in the modeline and stuff like that, and you need to know a bit about your tv too i think. 

like i said in another post, the easiest thing to do really is to plug a windows box into the tv via hdmi and use powerstrip. its easy to sort out overscan with the nvidia control panel in windows. im assuming it isnt too hard with ati either or intel onboard

---

### Post by fizban9 on 2008-06-03
> **aeiah said:**
> when i was digging around sorting out my overscanning issue i came across something that explained it, but it involves calculating each value listed in the modeline and stuff like that, and you need to know a bit about your tv too i think. 

like i said in another post, the easiest thing to do really is to plug a windows box into the tv via hdmi and use powerstrip. its easy to sort out overscan with the nvidia control panel in windows. im assuming it isnt too hard with ati either or intel onboard

Unfortunately I don't have a windows box with an HDMI plug on it.  Also, I don't know what this "powerstrip" thing is you're talking about.

---

### Post by unutbu on 2008-06-03
Run xvidtune and press the Wider and/or Narrower buttons. You'll see that it is the HTotal which changes, while HSyncStart and HSyncEnd remain the same.

So my guess is, you should try changing HTotal. Wider corresponds with decreasing HTotal. Narrower corresponds with increasing HTotal.

Also, do you know about gtf? It can create modelines for you, given the hres, vres and refresh rate:
```
% gtf 1680 1050 59

  # 1680x1050 @ 59.00 Hz (GTF) hsync: 64.07 kHz; pclk: 144.55 MHz
  Modeline "1680x1050_59.00"  144.55  1680 1784 1968 2256  1050 1051 1054 1086  -HSync +Vsync
```

As you change the refresh rate, the HSyncStart, HSyncEnd and HTotal all change. Perhaps you can not change them independently. Maybe it is better to use gtf.

Higher refresh rate corresponds with higher HTotal, therefore higher refresh rate also corresponds with a narrower image.

Lower refresh rate therefore corresponds with a wider image.

---

