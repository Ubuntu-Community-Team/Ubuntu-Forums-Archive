---
title: "[SOLVED] My laptop desktop &amp;quot;resolution&amp;quot; changes when with/without monitor"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by olmedilla on 2007-07-23
Hi, I have Lenovo T60 laptop with an ATI Radeon Mobility X1400 and Ubuntu Feisty running. The situation is that the display of my laptop has a different "resolution" depending on whether I start X with a monitor attached to my laptop or not. The thing is that without monitors, everything appears really big in my laptop display and I would like to have it always differently.

The reason why I put that this a resolution problem between quotes is that in both cases both the Xorg log and the gnome resolution tool shows that it is running on 1400x1050, but definitely the appearance of the whole desktop manager is really different (like if the resolutions were different).

I have read the xorg.conf man page and Googled for ages. I have tried most of solutions I found and even updated to the newest ATI drivers. I have also tried different combinations on my xorg.conf: with and without clone option, force monitors (equivalent to enablemonitor), add higher resolution modes (but in any case the EDID data says the maximum allowed is 1400x1050 for both my monitors and the laptop display), etc.

Any idea what is going on? Whenever I am not at work and therefore I don't have a monitor, I can don't work so well (e.g., only 2 tasks fit in my taskbar, instead of aroun 7 when I have a monitor attached).

I attach my xorg.conf and the two logs: normal is when no monitor is attached and goodRes when a monitor is attached.

Thank you in advance for your support,

       D.

---

### Post by olmedilla on 2007-07-26
Actually I get the impression that the problem is not the resolution (the content of some pages in firefox) or some other applications running under wine show everything small. They are only the gnome and kde applications I use the ones that show everything too big.

Can it have anything to do with the font size being changed depending on whether a monitor is attached or not? Anything similar?

Thank you,

      D.

---

### Post by olmedilla on 2007-07-26
ok, after quite some time, I discovered the error. The problem is that the DPI is determined automatically depending on the monitor selected. In order to solve that, you need to specify in the xorg.conf the dpi you want to have: There are two ways:

with the option

```

Option         "DPI" "96 x 96"
```

which does not work with the fglrx ati driver (it is ignored) or specifying the overall display size for your monitor. This is done dividing your resolution by the DPI you want to have and multiply by 25.4, that is

```
displaysize = (<pixelsize>/96)*25.4
```

and add it to the xorg.org file in the monitor section. For example, in my case I have a resolution of 1400x1050 and 96DPI so my xorg.org contains a line in the monitor section as follows

```
DisplaySize     370.4  277.8
```

Hope it helps,

      D.

---

