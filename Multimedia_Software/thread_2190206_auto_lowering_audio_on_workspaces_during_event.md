---
title: "auto lowering audio on workspaces during event"
date: 2013-11-26
forum: Multimedia Software
---

### Post by steelrain89 on 2013-11-26
I looked over Google and the forums and I'm not sure if it's the way I'm asking or if it can even be done, with auto lowering audio when one workspace has a notification sound etc anything audio begin. I'm using Openbox as well, it's a laptop while it can handle what I throw at it, I prefer it being a little faster so I did a full install and then put Openbox on.

Anyway let's say I'm on workspace 0 or 3 and a notification comes up on workspace 2 (specifically that workspace the rest they can stay the same notifications or not). At the same time I'm using Banshee on workspace 1 listening to some music, while the notification is coming on workspace 2 I'd like to have the volume drop by half (on all workspaces but workspace 2) so it grabs my attention and then returns to normal volume setting.

Is this possible? Or is this one of those things were while it's a good idea going to require more work then it would be worth?

Thanks in advance everyone.

---

### Post by tgalati4 on 2013-11-26
I don't know of a way to do it.  I would think that you need a plug-in for Banshee that watches the system (dbus, notify-send, etc) and if a notification gets launched, then lower the volume for a few seconds.  This could be CPU intensive, because you have to keep watching for such events and play music at the same time.

An alternative is to set the application on Workspace Two to appear on all workspaces, (Right-Click on top of window bar, "Visible on all Workspaces"), then minimize it.  So if that application gets a notification, it should appear on all workspaces.  Not what you want, but a possible work-around.

---

