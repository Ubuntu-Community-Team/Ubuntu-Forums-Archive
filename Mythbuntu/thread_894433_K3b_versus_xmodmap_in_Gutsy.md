---
title: "K3b versus xmodmap in Gutsy"
date: 2008-08-19
forum: Mythbuntu
---

### Post by klc5555 on 2008-08-19
Okay, here's a weird one I just want to document.

Last year, when I first installed 7.10, I set up the machine that it was on with a Snapstream Firefly mini remote operating through the USB port. I used xmodmap to load the keycodes for most of the special keys (as described in the Firefly mini page in the Mythtv wiki). Later, after installing K3b (and its dependencies through apt-get) I noticed the remote mute and volume controls no longer worked. That was several Gutsy installs ago; none of the intervening ones used K3b.

This week, on a clean install, I added K3b (and its dependencies) and the behavior repeated. 

Upon investigating, it seems that the installation of K3b and dependencies disables keycodes 160, 174, 176, and 144, which the Firefly mini uses by default for mute, vol. down, vol. up, and previous. You can still assign these keycodes through xmodmap; they just won't do anything.

Now from a practical standpoint, it was perfectly easy to re-assign the F9, F10, and F11 Mythtv keyboard shortcuts to alternate keycodes on the Firefly mini, e.g. 153, 158, and 164, which are all still functional.

But I've never had an app nuke keycodes before, which I thought were reserved for hardware. Is this normal? Anybody else experienced anything like this with K3b on their Myth boxes?

Cheers!:)

---

