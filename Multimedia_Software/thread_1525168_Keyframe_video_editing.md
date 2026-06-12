---
title: "Keyframe video editing"
date: 2010-07-06
forum: Multimedia Software
---

### Post by hellocatfood on 2010-07-06
I want to change the speed of a video using keyframes. The effect that I want to achieve is to gradually and smoothly increase the speed of a video over time.

The problem that I'm having is that i can't find any software that can do this. I've tried openshot, kdenlive and looked briefly at cincelerra with no luck. I've also looked at Blender but so far [this thread](http://blenderartists.org/forum/showthread.php?t=180196) is the only one that mentions it, but it doesn't work

Is there any software that can do this?

---

### Post by hellocatfood on 2010-12-17
*bump*

---

### Post by hellocatfood on 2011-03-04
Many months later and I've finally come across a way to do this. It can be done in Blender 2.48 but this describes hwo to do it in Blender 2.56

[http://blenderartists.org/forum/showthread.php?t=180196&p=1790756&viewfull=1#post1790756](http://blenderartists.org/forum/showthread.php?t=180196&p=1790756&viewfull=1#post1790756)

It doesn't seem to work with audio, so you'll probably need to use something else for that.

Audacity can achieve this using the [Time Track](http://audacity.sourceforge.net/onlinehelp-1.2/track_time.htm) function and Ardour can do this using [automation](http://en.flossmanuals.net/Ardour/UsingAutomation)

Keyframes for effects has been a feature request in many Linux video editors:

**Openshot**
[Bug 524364](https://bugs.launchpad.net/openshot/+bug/524364)
[Bug 506096](https://bugs.launchpad.net/openshot/+bug/506096)

**Kdenlive**
[Bug 336](http://www.kdenlive.org/mantis/view.php?id=336)
[Bug 397](http://www.kdenlive.org/mantis/view.php?id=397)
[Bug 289](http://www.kdenlive.org/mantis/view.php?id=289)

**VLMC**
[Bug 205](http://trac.videolan.org/vlmc/ticket/205)

**Novacut**
[Bug 680865](https://bugs.launchpad.net/novacut/+bug/680865)

If you have the skill to implement this I'm sure the developers would be greatful.

If you find any one video editor that does both audio and video keyframe editing please share your findings!

---

### Post by prokoudine on 2011-03-04
> **hellocatfood said:**
> Keyframes for effects has been a feature request in many Linux video editors... If you find any one video editor that does both audio and video keyframe editing please share your findings!

Er, in Kdenlive making an effect keyframeable is a matter of using a correct attribute of an XML tag. I was going to fix my effects XML descriptions anyway, so if sox stretch is MLT based, I can fix it in a flash. I'll have a look over the weekend.

---

### Post by hellocatfood on 2011-03-23
Did you ever get speed keyframes working in kdenlive?

---

