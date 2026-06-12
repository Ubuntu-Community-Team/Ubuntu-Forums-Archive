---
title: "Nvidia Quatro on 8.04 only showing max resolution 1600 x 1200"
date: 2009-11-08
forum: Multimedia Software
---

### Post by timZZ on 2009-11-08
Version: 8.04 LTS Hardy Heron (64 bit)
Desktop: Gnome
Graphics Card: nVidia Quadro FX 1400

Problem: My monitor + graphics card is capitable of reaching higher resolution then the app in System >> Preferences >> Screen Resolution is allowing. Which is (1600 x 1200)

My monitor should be running at least 1900 x 1200.

**Would it cause any damage if I altered my X config to allow for this new resolution?**

**Has anyone ran into this problem before?**

---

### Post by xc3RnbFO8P on 2009-11-08
**gksu displayconfig-gtk**
Choose Generic (if you cannt find your monitor)
and resolution that your monitor supports

---

### Post by timZZ on 2009-11-08
Thank you.

I have found the correct monitor.

I think the problem is with the graphics card.

In which the system thinks it's maximum output is 1600 x 1200.
[B]
Is there a method of proving if this assumption is true or not?[/B]

---

### Post by xc3RnbFO8P on 2009-11-08
Are you sure your cable is OK?
> Maximum resolution 
Dual DVI-I output - drives dual digital displays at resolutions up to 1920x1200 @ 60Hz
Internal 400MHz RAMDACs - drives dual analog displays up to 2048x1536 @ 85Hz each

---

### Post by timZZ on 2009-11-08
Ah ok this is where my knowledge is limited.

**What type of conditions are possible where I can receive a working display signal at 1600 x 1200 but prevents 1920 x 1200?**

I am using the cable right now as we speak @ 1600 x 1200.

**Literally my situation is System >> Preferences >> Screen Resolution.  The highest option available for me to select is 1600 x 1200.**

---

### Post by xc3RnbFO8P on 2009-11-08
Check this:[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/f/fb/DVI_Connector_Types.svg/181px-DVI_Connector_Types.svg.png[/IMG]
**Remember to turn of the computer before you disconnect the cable**

---

### Post by timZZ on 2010-02-04
Thank you ...

I thought I would place a reply to this just in case anyone searches this.

I actually looked the cable / monitor / graphics card and all supported the higher resolution.

I simply altered the xconfig and this corrected the problem.

I would not recommend this unless people research everything throughly

---

