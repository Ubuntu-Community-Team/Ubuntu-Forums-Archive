---
title: "How to keep gnome resolution with a KVM switch"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by Peepsalot on 2006-05-30
I have two computers at home connected to a KVM switch.  I would like to be able to power on my ubuntu machine, and wait for bootup while the KVM is still on the other machine.  The problem is when I do this, I guess X is detecting that no monitor is attached, so it decides to set resolution to 640x480.  I normally use 1280x1024.  It resets the resolution correctly if I restart gnome with Ctrl-Alt-Backspace, but I'd like to do without that if possible.
Is there some way I can tell it to force into 1280x1024 no matter if there is a monitor connected?

I also have wake-on-lan set up which this would be good for.

---

### Post by jazzmuzik on 2006-05-30
Same problem here. The non-active computer on the kvm switch boots up at 640x480. I have to ctrl-alt-backspace to restart the xorg server. I'm also interested in a solution.

---

### Post by rex_drecor on 2006-06-06
I'm not posting to help, coz I have the same problem.

But I didn't know about the Ctrl+Alt+Backspace, so I'm glad I stumbled across your posts. ;)

---

