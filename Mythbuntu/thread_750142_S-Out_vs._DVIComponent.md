---
title: "S-Out vs. DVI/Component"
date: 2008-04-09
forum: Mythbuntu
---

### Post by dsbw on 2008-04-09
OK, Mythbuntu-dudes,

   I've got a GeForce 7300 GS and I've been  using the S-Video out.

   If I plug in the S-Out cable to the TV, the nVidia driver detects the TV, which is groovy. Looks good.

   But I'd like to use the card's DVI-I interface. I've got a DVI->Component cable. When I plug *that* in, nVidia insists on callng the TV a generic SVGA CRT.  I can't set proper resolutions or frequencies.

   I do get an image, but it's a portion of the screen (if I've got a monitor hooked up as well), the colors are distorted and the picture waves and rolls and otherwise looks ooky.

   Time to hack xorg.conf?:popcorn:

---

### Post by volkswagner on 2008-04-09
Your post caught my eye.  My lcd tv needs component input to get full 1080i resolution.  After researching dvi>component cables, it seems you may need a converter.  Did the cable come with your video card?  It may need software to work properly.

---

### Post by newlinux on 2008-04-09
You only need a converter if your video card is DVI-D out. DVI-I supports digital and analog (component) so it shouldn't need a converter. Is your TV a standard definition TV? If so, why do you want to use the DVI-I? You will probably need to set a custom resolution as the driver doesn't seem to recognize your TV's capabilities through component.

---

### Post by volkswagner on 2008-04-09
DSBW,

Can you post information on the adapter/cable you are using.  I can not seem to find any for Nvidia cards.

---

### Post by dsbw on 2008-04-09
> **newlinux said:**
> You only need a converter if your video card is DVI-D out. DVI-I supports digital and analog (component) so it shouldn't need a converter. Is your TV a standard definition TV? If so, why do you want to use the DVI-I? You will probably need to set a custom resolution as the driver doesn't seem to recognize your TV's capabilities through component.

It is DVD-I. I have a 1080i HD TV, however. 

I guess it's old, though, by today's standards, maybe six years old. No digital input. CRT. 

Custom resolution?

---

### Post by dsbw on 2008-04-09
> **volkswagner said:**
> Can you post information on the adapter/cable you are using.  I can not seem to find any for Nvidia cards.

There's nothing special about it, AFAIK. 

I beleve this is the one I got:

[http://www.colordrives.com/dvi-to-3-rca-component-cable-6-foot.html]("http://www.colordrives.com/dvi-to-3-rca-component-cable-6-foot.html")

---

### Post by newlinux on 2008-04-09
> **dsbw said:**
> It is DVD-I. I have a 1080i HD TV, however. 

I guess it's old, though, by today's standards, maybe six years old. No digital input. CRT. 

Custom resolution?

Yeah, I know you said it was DVI-I, I was referring to volks' comment about needing a converter.

By custom resolution I mean possible forcing a modeline in xorg.conf. What resolutions have you set it to output via component?

---

### Post by dsbw on 2008-04-09
> **newlinux said:**
> Yeah, I know you said it was DVI-I, I was referring to volks' comment about needing a converter.

Ah. Right.

> **newlinux said:**
> By custom resolution I mean possible forcing a modeline in xorg.conf. What resolutions have you set it to output via component?

Nothing, yet. Not sure where to begin. I'm reading up but wouldn't mind a pointer or two.

(Also, tangentially, I was reading somewhere around here that you had a wireless setup that worked in Ubuntu. Have you written that up anywhere?)

---

### Post by Trimble Epic on 2008-04-13
I also have an older 1080i compatible TV without any digital inputs.

On an unrelated side note, you may find it interesting to google(or ebay) "visionfc3" or "visionfc4"

---

