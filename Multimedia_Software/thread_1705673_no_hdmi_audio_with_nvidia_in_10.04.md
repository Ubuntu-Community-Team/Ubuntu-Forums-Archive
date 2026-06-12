---
title: "no hdmi audio with nvidia in 10.04"
date: 2011-03-12
forum: Multimedia Software
---

### Post by jim.hitch on 2011-03-12
Hi

Because of some kind of mismatch between the latest X-server and nvidia drivers which crashes recent versions of the xserver, I've downgraded with a clean install of mythbuntu 10.04.

Trouble is, now I'm getting no sound through the hdmi to the tv.

When I try aplay -l I get info for sound card 0 (HDA Intel), but nothing is showing for soundcard 1e

So it's not seeing the card, so I can't configure it.

How can I fix this? Any help much appreciated.

---

### Post by jim.hitch on 2011-03-12
I don't know what happened, but a reboot solved it.

---

