---
title: "How can you adjust video color saturation levels?"
date: 2009-11-26
forum: Multimedia Software
---

### Post by TeaSwigger on 2009-11-26
My DVD player is toast and there's more and more video online. The problem with PC playback of videos for me is that they all appear oversaturated, like the "vivid" switch on a newer television were on. The world in Neon, everyone flushed to the point of a stroke. Needs to be dialed down. Pictures are fine: _videos_ are saturated. How in the world do I permanently adjust saturation for just videos?

Done the following -
- Searched the forums. One post also asking and he went unanswered:
[http://ubuntuforums.org/showthread.php?t=811919](http://ubuntuforums.org/showthread.php?t=811919)
- I've made sure the monitor is not on some weird setting for bleeding color. There is no adjustment for saturation, only gamma. 
- Checked nvidia's settings GUI. There is no adjustment for saturation, only gamma. 
- I've checked the players (MPlayer etc) for some adjustment, no joy. Besides I'd like it dialed in system wide.

System - 
- Kubuntu 9.10, Fluxbox wm
- Dell 19" LCD monitor (but then, same story for other monitors over the years).
- NVidia GX5200 128mb AGP graphics card, 3-D is enabled and working fine.
- Old PIII PC, 512 mb - yes HDTV is out, but it plays standard videos incl. DVD nicely. All I want is the color in check...

So: where's the color knob on this thing eh?

---

### Post by andrew.46 on 2009-11-26
Hi TeaSwigger,

> **TeaSwigger said:**
> - I've checked the players (MPlayer etc) for some adjustment, no joy. Besides I'd like it dialed in system wide.

It is not the system setting you are after but MPlayer has a pretty reasonable equaliser that might at least get you started. Screenshot attached.

Andrew

---

### Post by TeaSwigger on 2009-11-26
Andrew,

Thank you very much indeed, that might tide me over until a permanent method. :)

Chris

---

### Post by TeaSwigger on 2009-11-27
> **andrew.46 said:**
> It is not the system setting you are after but MPlayer has a pretty reasonable equaliser that might at least get you started. Screenshot attached.

...It doesn't work. Settings have no effect.

---

### Post by andrew.46 on 2009-11-27
Hi Tea,

> **TeaSwigger said:**
> ...It doesn't work. Settings have no effect.

Hmmm.... works well on my system so I am not sure what to suggest for your system. Apologies!

Andrew

---

### Post by TeaSwigger on 2009-12-17
Follow up in case anyone else has an issue: I did get the "video equalizer" to work; under options (this in SMPlayer, may be same for standard MPlayer I don't know), Video, I had to opt for "Use software video equalizer." This probably isn't preferable but may be the only option in certain cases depending on hardware, driver etc. Seems to do a fair job for anything MPlayer runs, although it's not the system wide overall adjustments hoped for.

Thanks again to Andrew for the suggestion. :)

---

### Post by coogur on 2010-11-17
Running fresh install of Ubuntu 10.10 Maverick.

Had the same issue, purple-gray-green colors all over the video stream, .. went into my NVIDIA driver settings in System - Administration - NVIDIA XServer Settings and in X Server XVideo Settings, selected Reset Hardware Defaults, up the saturation to 4096 which is half way up the scale and all natural colors came back.  Hope this helps or inspires you to get back on the road jack.  Not aware of any XServer.conf file settings to match this, check your XServer video driver section.  man is your best friend.

---

