---
title: "One key doesn't work on remote with ir-keytable"
date: 2018-12-01
forum: Multimedia Software
---

### Post by philled on 2018-12-01
I have successfully got my Harmony 650 remote control working with MythBuntu 16.04. I don't have lirc installed, I've purged all traces of it from my machine, I'm using ir-keytable. Unfortunately one key o my Harmony 650 remote isn't working - the Exit key, so it's quite an important and often used one. When I say it's not working, I mean it's not sending any scancodes to irkeytable -t. Does anyone know how I can make the Exit key send a scancode?

My Harmony 650 config has it as a "Microsoft MCE-1039" device.

---

### Post by philled on 2018-12-02
I've worked it out. The reason why the Exit button wasn't sending a scancode was because it wasn't configured properly in the My Harmony software. After configuring the Exit to be # in the My Harmony software it now sends a scancode which I can map to something useful for ir-keytable.

---

