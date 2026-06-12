---
title: "[ati/graphics/14.04/gnome]Large area of graphical 'sticking' only on desktop"
date: 2014-07-24
forum: Multimedia Software
---

### Post by mtotho on 2014-07-24
Hello,

I recently changed my desktop from windows to linux (I had already primarily been using linux on the laptop). I've been having a lot of annoying issues with getting my display issues sorted out.
 
I have 3 monitors. 2 Hooked up to a HD 6850 and the other hooked up to the motherboard's intel. Upon first boot everything worked well. No graphical issues. Then after rebooting I encounter the following issue.. there is a square of area on my central monitor (attached to ati card) where the display elements get stuck. Here is a screen shot [http://i.imgur.com/gVvUsm0.png?1](http://i.imgur.com/gVvUsm0.png?1)
 
interestingly, it is only when elements pass over my desktop do they get stuck. This does not happen if I drag one smaller chrome window over a full screen one, for example [http://i.imgur.com/aQqdq5Y.png?1](http://i.imgur.com/aQqdq5Y.png?1)

I have tried installing the fglrx through command line, which also worked well on first boot but only for the 2 displays attached to the ATI card. However upon rebooted I also had weird graphical issues. I reverted back to the open source drivers because I wanted the third monitor but now I am stuck with the aforementioned issue. 

Attached here is the result of running dmesg | egrep 'drm|radeon'
[ATTACH]254989[/ATTACH]

intel z68 motherboard with a corei5 quad core and radeon hd6850 graphics
ubuntu gnome 14.04

Thanks if anyone has any ideas.


EDIT: SOLVED: After hours of purging and trying various drivers.. the issue turns out to be my Desktop environment. I was running gnome as equipped by Ubuntu Gnome version. I simply installed cinnamon, mate, or any other desktop environment and this issue goes away. werid

---

