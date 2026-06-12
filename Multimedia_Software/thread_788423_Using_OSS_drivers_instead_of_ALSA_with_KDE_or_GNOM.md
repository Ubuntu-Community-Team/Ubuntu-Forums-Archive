---
title: "Using OSS drivers instead of ALSA with KDE or GNOME and Flash in Hardy"
date: 2008-05-09
forum: Multimedia Software
---

### Post by maggot_brain on 2008-05-09
Hi all,

I've just converted a relative to using the Ubuntu.  He has X86 Hardy installed.  Everything worked out of the box apart from the X-fi sound card.  Luckily the OSS driver from 4front appeared to do the trick.  I say appeared cos I logged into his machine over SSH to configure it for him. So I'll have to wait until he gets chance to get on his machine to test it.

I haven't used Ubuntu in a while having gone back to Debian.  Therefore I'm not familiar with the sound setup in Hardy.  Is Pulseaudio used by default in GNOME?  If so will it automatically use OSS output?  Also will KDE3/arts use OSS output by default?  There are no other soundcards available on his PC some I'm hoping the answer's yes!

One more question does flash work out of the box (including sound) with Hardy using Firefox on KDE or GNOME?

Thanks in advance, I'd probably be able to answer these questions myself but I don't currently have Ubuntu installed on any of my machines.

---

### Post by macaholic on 2008-05-09
Does changing the default outputs in the sound preferences help?

---

### Post by maggot_brain on 2008-05-09
> **macaholic said:**
> Does changing the default outputs in the sound preferences help?

Don't know it's not my machine and I don't have physical access to it.  I was kind of hoping somebody would know if OSS is automatically used as I'm not an Ubuntu user myself.

---

### Post by ewanmalone on 2008-05-10
ok so im now at my machine.
i have changed the outputs to oss however the sound icon in the top right corner has a red bit on it and i get the following error message

"No volume control GStreamer plugins and/or devices found."


as stated earlier im running an Xfi (or not running) and i hear these are a pain

---

