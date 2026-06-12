---
title: "UHD/4k tv set connected to Ubuntu PC"
date: 2013-11-12
forum: Multimedia Software
---

### Post by zouzoudude on 2013-11-12
I have a PC with an Intel Core i3 4330 processor connected to a UHD tv set.

This PC runs Ubuntu 13.04 and has the following items installed:
- mplayer with vaapi support
- Intel Graphics drivers (for vaapi)

The UHD/4k resolution wasn't detected by Ubuntu so I had to add a modeline (2160p24) via xrandr. This works great and I'm able to playback UHD/4k content on my tv set. I also created a small script which adds the modeline and sets the UHD mode at startup so the PC always starts up in UHD.

But I'm running into some issues when using this setup:
1) whenever I change source on my tv set and switch back to the PC, the PC automatically reverts to Full HD output instead of the UHD output I left it at. The same goes for unplugging and replugging the HDMI cable.
2) I consider the next one "nice to have". Ideally it would be great if I could connect the PC to a Full HD tv set and have Full HD output, and after that I could connect it to a UHD tv set and have UHD output without having to manually change the resolution.

So in short, I was wondering if anyone knows if it is possible to have this kind of behaviour in Ubuntu? I'd be already happy to find a solution for the source switching issue.

Small note, when using Windows, the maximum resolution allowed is UHD so the tv set is detected correctly there.

EDIT: in case anyone is interested in how to have 2160p24 (or 25/30) on an Intel Haswell CPU, just let me know and I'd be happy to share, it took me long enough to find out :)

---

### Post by henrik.morch.ander on 2013-12-03
I am very interested in knowing how you got 2160p out of the Haswell using Ubuntu.

I have an Intel NUC D54250DYK with an Intel Haswell Core i5-4250U featuring HD 5000 graphic which I am trying to connect to a 4K TV.
So far I have not managed to get anything above FHD on the TV.
I have tried to define a new format using xrandr command, but when changing to the new format it just jumps back to FHD again.

So any help is welcome :-)

---

### Post by zouzoudude on 2013-12-03
On your problem with the new mode you defined. Maybe it's a mode your TV doesn't support and that's why it reverts to Full HD?

Anyway, below is a small guide on how I managed to have 2160p output. I'm using this PC to playback UHD/4k material via the onboard GPU (using Intel Linux drivers and VA-API).

The modeline I add with xrandr is this: 
xrandr --newmode "3840x2160" 296.998 3840 5116 5204 5500 2160 2168 2178 2250 +HSync +VSync

Note this is for 2160p24, it's the only one I'm using for now although it's also possible to output 2160p25 and 2160p30. 

After that I just add this mode to my HDMI2 output:
xrandr --addmode HDMI2 "3840x2160"

I don't know which outputs you have, but I assume it's name will be similar (could be HDMI1,...).

I hope this works for you :) Also, if anybody knows where to find more UHD/4k content (real content, not the upscaled clips or "YouTube 4k") then please share! It's really hard to find decent content :D

---

