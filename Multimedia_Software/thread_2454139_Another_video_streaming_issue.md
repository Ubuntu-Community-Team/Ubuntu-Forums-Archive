---
title: "Another video streaming issue"
date: 2020-11-23
forum: Multimedia Software
---

### Post by moto1860 on 2020-11-23
Hi all, I'm having exactly the same issue reported here: [https://ubuntuforums.org/showthread.php?t=2388488](https://ubuntuforums.org/showthread.php?t=2388488)
but with a trusted streaming service this time (Eurosport Player), command top has Chromium in the 120ish% usage during such streamings.

[COLOR=#5F6368][FONT=Roboto]Version 87.0.4280.66 (Official Build) snap (64-bit)[/FONT][/COLOR]
Ubuntu 20.04.1 LTS

---

### Post by CelticWarrior on 2020-11-23
> **moto1860 said:**
> 

but with a trusted streaming service this time (Eurosport Player), command top has Chrome in the 120ish% usage during such streamings.

[COLOR=#5F6368][FONT=Roboto]Version 87.0.4280.66 (Official Build) snap (64-bit)[/FONT][/COLOR]
Ubuntu 20.04.1 LTS

Why do you think that's an "issue"?
And for the record you're using Chromium.

---

### Post by moto1860 on 2020-11-23
> **CelticWarrior said:**
> Why do you think that's an "issue"?

Higher quality streamings don't trigger my cpu as much making it impossible to do other tasks and cause excessive heating, so assumed there might be a problem with my settings or possibly Flash cause this was the case with past episodes. That is if I understood your question.

---

### Post by CelticWarrior on 2020-11-23
For sure I won't be paying a subscription just to test it but I very much doubt Eurosport is streaming in Flash. Flash is a dead technology, even more so than two years ago. Actually we're a couple of months or less from Adobe shutting down its support completely.
120% CPU usage means you have at least two cores an one is being fully used. It's not typical just for video streaming (but not that much either) unless in very old and/or under-powered hardware and/or missing drivers/codecs.

Please post your hardware specifications to avoid wrong assumptions.

---

### Post by moto1860 on 2020-11-24
> **CelticWarrior said:**
> For sure I won't be paying a subscription just to test it but I very much doubt Eurosport is streaming in Flash. Flash is a dead technology, even more so than two years ago. Actually we're a couple of months or less from Adobe shutting down its support completely.
120% CPU usage means you have at least two cores an one is being fully used. It's not typical just for video streaming (but not that much either) unless in very old and/or under-powered hardware and/or missing drivers/codecs.

Please post your hardware specifications to avoid wrong assumptions.
Yup I've had the same thoughts on it being a Flash stream.

[https://ibb.co/NTskd29](https://ibb.co/NTskd29)
[https://i.ibb.co/2ZyL13v/ubuntu.png](https://i.ibb.co/2ZyL13v/ubuntu.png)

---

### Post by CelticWarrior on 2020-11-24
An i5-3320M CPU is an 8 years old CPU and coupled with an even older integrated graphics.
It's also a 2 cores / 4 threads CPU which means that top and similar considers the maximum CPU usage as 400%. So, ~120% isn't that bad for hardware of that vintage.
Besides that, browsers in Linux don't use hardware (GPU) acceleration except the development branch of Chromium. That means the CPU is taxed even more.
Using Wayland instead of X11 my decrease the CPU usage (or may not).

If your laptop becomes hot and noisy it probably, almost certainly, needs cleaning and/or new thermal paste.

---

### Post by moto1860 on 2020-11-24
Thanks for the reply, yes it's an old piece that needs maintenance, wanted to make sure there was no possible conflicts triggering cpu that match. Firefox seems to handle it slightly better.
 Appreciate it.

---

### Post by DuckHook on 2020-11-24
Hello moto1860.

Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. It is also unnecessary to post whole screenshots in most cases. Terminal output can be highlighted with the mouse, copied with a right click and pasted into the posting box between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the button in the *Adv Reply* toolbar.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

---

### Post by Yellow Pasque on 2020-11-27
Once chromium 88 rolls out, GPU accelerated decoding should be available:
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1894433](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1894433)

But your GPU is a bit older and will only accelerate H.264, so it depends on what formats the streaming service offers.

---

