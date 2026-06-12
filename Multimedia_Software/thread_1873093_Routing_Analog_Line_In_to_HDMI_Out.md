---
title: "Routing Analog Line In to HDMI Out"
date: 2011-10-31
forum: Multimedia Software
---

### Post by enkay009 on 2011-10-31
So here's my situation.

I've got my PC connected to my TV via HDMI and I have HDMI audio enabled. All works. No problems here.

Recently I found my old walkman. I wanna take trip down memory lane... listen to my old mixtapes. I don't have an amazing sound setup for my TV but I like it and I wanna use it to listen to my tapes.

So I connected my walkman to my PC through the line-in jack. When I hit play on my walkman, Ubuntu registers sound (i.e. the meter in the input sound panel moves). However that sound is not being routed through HDMI.

Anyone have any idea how to get analog line-in/mic-in routed through HDMI out?

EDIT: Nevermind everyone, figured it out. Just needed to load the loopback module. Weird that it isn't loaded by default though...

```
pactl load-module module-loopback
```

---

