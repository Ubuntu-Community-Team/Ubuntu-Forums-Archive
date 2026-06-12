---
title: "nvidia/notebook: switch between internal/external"
date: 2008-12-30
forum: Multimedia Software
---

### Post by argo82 on 2008-12-30
Hi!
I have a notebook with nvidia 8400 GS. I figured out how to use my external tft with nvidia-settings, however it seems that
a) it either has the same (e.g. not native) resolution as my notebook display
or
b) it is running on native resolution, but things appear slightly awkward (application bar somewhere in the middle)

I realize there is no way around this because the display is cloned. However, when I use my tft, I don't use my laptop display and vice versa. Is there a way to switch between the displays, one running in its native resolution and the other one being disabled? I can disable the display in the nvidia-settings applet, but to enable it again it requires a restart of the x-server, so it's not very convenient. It'd be also enough if the x-server would display on my tft if it is connected at startup, and on the internal display otherwise. Usually I don't switch "on-the-fly" anyway.

Thanks for the help!
argo

---

### Post by argo82 on 2008-12-30
By chance I found out that even if the internal display is disabled, it uses it as fallback when there is no external display attached. So when I connect the tft before booting, it uses it, if not, it uses internal display. So question solved :-)

---

