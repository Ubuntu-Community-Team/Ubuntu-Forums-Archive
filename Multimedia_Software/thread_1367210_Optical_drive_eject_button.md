---
title: "Optical drive eject button"
date: 2009-12-29
forum: Multimedia Software
---

### Post by matt_garman on 2009-12-29
Whenever I use the physical eject button on my optical drive, the disc tray ejects, then immediately goes back in.  The second time I press eject, it stays open.  This happens at least with DVDs (not sure about CDs).

Does anyone have any idea what causes this?  When I press eject, I'd prefer the drive to just stay open.

This is for Ubuntu 9.10/Karmic Koala, but also existed with 9.4/Jaunty Jackalope.

---

### Post by VertexPusher on 2009-12-29
Most optical drives close the tray if you push it. If the drive is old and its tray mechanism is broken, it may register a false push and close the tray all by itself. I've seen this happen on DVD players. It's definitely not an operating system issue.

---

### Post by matt_garman on 2009-12-29
> **VertexPusher said:**
> Most optical drives close the tray if you push it. If the drive is old and its tray mechanism is broken, it may register a false push and close the tray all by itself. I've seen this happen on DVD players. It's definitely not an operating system issue.

Well, I actually have three optical drives, two of which are different models.  This problem exists with all three drives.  I switched to Ubuntu from Gentoo less than a year ago, and never experienced this prior.  I doubt all three drives became semi-broken exactly at the same time I switched distributions.  :)

My hunch is that there is some module/daemon/process that takes control of the drive when the disc is initially loaded into the drive.  And that the "proper" way to eject the disc is through said program.  But I prefer a more "low level" experience, and would rather no automatic process touched the drive.

---

### Post by VertexPusher on 2009-12-29
> **matt_garman said:**
> I doubt all three drives became semi-broken exactly at the same time I switched distributions.  :)
I agree. :)

> My hunch is that there is some module/daemon/process that takes control of the drive when the disc is initially loaded into the drive.  And that the "proper" way to eject the disc is through said program.  But I prefer a more "low level" experience, and would rather no automatic process touched the drive.
As far as I know, Ubuntu takes control of the eject button anyway, i.e. when you press it, the drive does not open the tray but instead signals the event to the operating system which then unmounts the drive and triggers the actual eject. This is why in some cases the eject button doesn't work at all, e.g. during installation or when the system is running from a live CD.

If you use the software method to eject the disc, e.g. right-click-eject or the CLI eject program, does the problem occur as well?

---

### Post by blueridgedog on 2009-12-30
My optical drives ejected with the button in 8.10, but stopped in 9.10.  I miss the simplicity of it.  I hope there is a fix.

---

### Post by LowSky on 2010-01-03
> **blueridgedog said:**
> My optical drives ejected with the button in 8.10, but stopped in 9.10.  I miss the simplicity of it.  I hope there is a fix.

It's really annoying and dumb that the OS is controlling the eject button the way it is. I dont like having to use the OS to eject a CD, I liked the simplicity of using the button on the drive. Luckily for now I have a key on my keyboard (technically a combo of keys (FN + F8), but it isn't the way I want it to work. Sure this "setting" is great for people who might have button pushers surrounding them but for the normal 'Joe' its takes away control of a simple task.

---

### Post by blueridgedog on 2010-01-03
How did you set that up?  I have never messed with custom key bindings.

---

