---
title: "audio key bindings"
date: 2010-05-08
forum: Multimedia Software
---

### Post by shapes on 2010-05-08
Since the upgrade to 10.04, the audio key bindings have been working weirdly... I can raise/lower the volume using the normal key combinations, only, any key I hit after changing the volume, repeats the volume operations done before. 

To make an example: I raise the volume by pressing twice the key combination. After that I press the bar space, then the volume will be raised again twice. This is the ```
xev
``` output of the previous operation:

```
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0
keycode 65 = (keysym 0x20, space), state = 0x0
keycode 65 = (keysym 0x20, space), state = 0x0

```

The first four times of the AudioRaiseVolume was done by me, the other four plus the space, where done when I pressed the space bar. I couldn't find anything that could help solving me the problem, anybody knows how to fix this?

thanks

---

### Post by shapes on 2010-05-09
bumping... sorry guys, any ideas? the problem is not terrible but it's really annoying...

---

