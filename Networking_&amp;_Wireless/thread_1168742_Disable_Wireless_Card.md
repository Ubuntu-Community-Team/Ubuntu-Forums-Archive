---
title: "Disable Wireless Card"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by Beacon11 on 2009-05-24
Hey all. I have a netbook (eeepc 901) with Ubuntu 9.04 Netbook Remix. It's a known issue that a few fn+ combos don't work correctly. However, I found this link ([https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)) and followed these steps:

I killed gnome-settings-daemon and gnome-power-manager, and ran

```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```

When I pressed the fn+F2 combo to disable the wireless card, it actually came up with XF86WLAN! I was expecting nothing to register, or at least an incorrect code. So... why isn't this working? I don't know much about this... I assume that since the key is correctly recognized, the script it's running doesn't work correctly. Can I write my own? How would I learn to do this?

---

