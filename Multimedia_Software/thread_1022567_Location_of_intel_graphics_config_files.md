---
title: "Location of intel graphics config files"
date: 2008-12-26
forum: Multimedia Software
---

### Post by inanutshellus on 2008-12-26
I have two laptops, one with an ATI video card, and one with an Intel video card. When I recently upgraded both to Ubuntu 8.10 all I had to do to get dual monitor support working again on the ATI was to copy two things:

/etc/X11/xorg.conf

and

/etc/ati/

So I installed 8.10 on my other laptop and ... it has an intel video card, so it doesn't have a "/etc/ati" directory, but obviously there's more settings than what's in the xorg.conf because my dual monitor setup doesn't work with just it copied from the old partition.

So where does Intel store its config information for its video drivers?

---

