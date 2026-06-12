---
title: "Why is everything pink?"
date: 2009-01-28
forum: Multimedia Software
---

### Post by Gedje on 2009-01-28
When I boot my computer and Ubuntu starts, my desktop and all the windows are pink (or various shades of purple). Also, many pixels are dancing around, like an old tv. I usually have to reboot between three and six times before the normal colors return.

This all started when I installed Kubuntu 8.10 a couple of months ago, but it has stayed with me now that I have moved back to Ubuntu 8.10. Strange, no? Even stranger: I can't take a screenshot to show you what I mean, because it will have the normal colors once I am able to view it normally. And finally, the splash screen always is yellow, orange and red, like it's supposed to be.

I'm not sure what kind of specs you might need to help me with this. My laptop has 128MB of shared graphic memory, and I suppose you may want this: ```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

I hope someone can help me!

---

### Post by squaregoldfish on 2009-01-28
Sounds to me like a hardware issue. In a standard VGA monitor setup, if you don't have a proper connection with one of the pins in the plug, this is the effect you see.

I suspect you've got a damaged connection to your laptop screen. If it's loose, then occasionally the connection will be made and you have a normal screen again.

Steve.

---

### Post by Gedje on 2009-01-28
Thanks for the quick response, Steve.

I thought about a damaged wire inside my laptop too. But I don't touch anything else when I'm restarting, just the power button, so I'm not sure that that would give the wire the nudge it needs. 

I get the impression all the wiring is still good, because once my screen returns to normal colors, I can close and open the screen all day long, but it won't turn pink again.

Then again, I don't know much about hardware. Any additional thoughts?

---

### Post by beroduar on 2009-01-28
Hi - I personally think this problem is related to embedded graphics and quite high demands of Ubuntu's dafault Compiz Fusion. I've got the same (or even worse) if I activate blur feature in windows or even titlebars (Vista-Aero's -like feature).
What's happening if you change compositing manager to Metacity ( metacity --replace ) ?

---

### Post by squaregoldfish on 2009-01-28
I'm not much of a hardware guru either. My only thought is that it might be a heat expansion/contraction issue. If you switch on the laptop from cold and just leave it, will the screen eventually fix itself?

One other thing to try: if you can get hold of an external monitor, plug that into your laptop. If the external monitor's OK but the laptop screen is still pink, you've definitely got a hardware issue.

Either way, I still I think it's hardware - I've never seen a mis-coloured monitor as you describe through a driver fault. (Always a first time though!)

Steve.

---

### Post by 3rdalbum on 2009-01-28
I've seen the pink-screen effect; I looked for an hour in Windows settings and in the settings for the TV that my customer was using as a monitor - eventually I found that it was the VGA cable.

---

### Post by Gedje on 2009-01-28
> **beroduar said:**
> Hi - I personally think this problem is related to embedded graphics and quite high demands of Ubuntu's dafault Compiz Fusion. (...) What's happening if you change compositing manager to Metacity ( metacity --replace ) ?

I wish I could run compiz and stuff like that, but I can't even enable desktop effects.

> **squaregoldfish said:**
> If you can get hold of an external monitor, plug that into your laptop. If the external monitor's OK but the laptop screen is still pink, you've definitely got a hardware issue.

Excellent suggestion, I'll try that!

---

