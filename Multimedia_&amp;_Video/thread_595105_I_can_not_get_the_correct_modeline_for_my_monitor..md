---
title: "I can not get the correct modeline for my monitor. How do I find  auto runs at?"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by boast on 2007-10-28
As the title says, I've tried tons of modelines, but none of them seem to work. Xorg still shows it auto-testing every modeline till it finds one that works. So, to keep it from autotesting each boot up, I just want to put the modeline it auto-selects. But I do not know what it is....

[color=blue]Is there a program I can run and it will tell me the modeline it is running in?[/color]


thanks.

---

### Post by sloggerkhan on 2007-10-31
Here's what I'd do:
One monitor at a time look at 
```

xrandr --query output. 

```
See if it lists all most, resolutions, and refresh rates you'd like to use.
If it does, there ought to be a way to autoconfigure it. But if not, no worries.

To create or find out a modeline, use the gtf tool.
To use gtf, type 
```
gtf  <xresolution> <yresolution> <refresh rate Hz>
```
It will give you a modeline. Example:
```
$ gtf 1680 1050 60

  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

```

That modeline should be directly usable by xorg.conf

---

