---
title: "Reboot computer and resolution got messed up (nvidia, ubuntu 9.10)"
date: 2010-04-14
forum: Multimedia Software
---

### Post by HyperFlexed on 2010-04-14
I'd like to clarify first of all that 2 days ago my monitor was working fine. nvidia-settings gave me the option for 1440x900, and everything was merry.

I reboot my system the other day, and now (after much hacking), I can finally get it up to 1152x864. This is not the native resolution of my monitor. Everything looks distorted as a result.

I'm not sure what is needed to solve this problem, so I'll post any information you require, but I'm wondering if anyone can help me through this issue. I'll be sure as heck to backup my xorg.conf once I get this figured out.

Where does nvidia-settings get its list of resolutions from? It would seem that when I reboot my machine (for some reason), this list got altered.

---

### Post by WinterRain on 2010-04-15
Did you use the nvidia-settings from system>administration? If so, you need to make changes by:
```
gksudo nvidia-settings
```
so that the settings will stick.

---

### Post by HyperFlexed on 2010-04-15
> **WinterRain said:**
> Did you use the nvidia-settings from system>administration? If so, you need to make changes by:
```
gksudo nvidia-settings
```
so that the settings will stick.

Yes, I have tried this. My issue is not that I can't get settings to stick, but that the option I want is not available. See screenshots below.

1440x900 isn't an option. (it was under a clean install, which is what's confusing me)

[IMG]http://imgur.com/mty5B.png[/IMG]
[IMG]http://imgur.com/jC1If.png[/IMG]

---

### Post by WinterRain on 2010-04-15
Which nvidia driver are you using?

---

### Post by bergfly on 2010-04-15
I'm interested in this thread as exactly the same issue has affected me, except I go down to 1024X768 (also from 1440X900)

I have spent a couple days on it now, with no resolution. Right now I can no longer get X to render. It runs, but the monitor gives me unsupported..

I have upgrade my driver via envyng without affect. The irritating thing is the bootsplash still renders at the correct resolution, but once X itself loads, it is gone.

---

### Post by HyperFlexed on 2010-04-15
> **WinterRain said:**
> Which nvidia driver are you using?

Version 185

---

### Post by HyperFlexed on 2010-04-15
Okay, so I solved my problem.

I was cleaning my room, so to vacuum under all the cables, I completely unplugged everything from my computer and plugged it back in again. When I booted up, I was back to the proper resolution.

Don't overlook this mysterious yet wonderful solution :P

---

### Post by HyperFlexed on 2010-06-27
And now months later, I resize my usr partition only to have the same damn thing happen all over again in 10.04. W.T.F.

Unplug solution isn't cutting it. I've checked EDID (which I believe to be the source of the problems), and my monitor isn't transmitting EDID data properly. *finds a noose and hangs self*

---

