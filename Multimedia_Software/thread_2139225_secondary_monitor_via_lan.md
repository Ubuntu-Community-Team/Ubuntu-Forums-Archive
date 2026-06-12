---
title: "secondary monitor via lan"
date: 2013-04-26
forum: Multimedia Software
---

### Post by Sersys on 2013-04-26
Hi, I have a pc and a laptop and I'm looking for a solution to use my laptop as a secondary monitor for the pc with lan connection. Is there any software for this for linux, like maxivista for windows or screenrecycler for mac?

---

### Post by tgalati4 on 2013-04-26
You could log in to the first PC using X-forwarding:

```
ssh -2 -Y username@pcname
```

Then use *synergy* to move the mouse and keyboard focus.

tgalati4@Mint14-Extensa ~ $ apt-cache search synergy
quicksynergy - GUI for easy configuration of Synergy
synergy - Share mouse, keyboard and clipboard over the network

---

### Post by Sersys on 2013-04-26
So will this method let me extend my pc's desktop on my laptop's monitor?
I don't want to see the laptop's desktop.  I need to see part of my pc's desktop on the laptop's monitor.

---

