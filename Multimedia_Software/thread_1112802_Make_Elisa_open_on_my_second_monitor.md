---
title: "Make Elisa open on my second monitor"
date: 2009-04-01
forum: Multimedia Software
---

### Post by Warpnow on 2009-04-01
My second monitor, IE, my projector, is what I watch movies on, yet Elisa always opens on my primary...is there a way to change that? I can't seem to move it either as its fullscreen.

---

### Post by xc3RnbFO8P on 2009-04-01
> I can't seem to move it either as its fullscreen
You can change it in /home/**.elisa-.?** (hidden folder) elisa-.?.conf
**sudo gedit /home/your folder/.elisa-0.?/elisa_0_?_?.conf**
> **start_fullscreen = '1'**  to  **start_fullscreen = '0'**

---

