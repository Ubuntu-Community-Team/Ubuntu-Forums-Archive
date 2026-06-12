---
title: "xcalib only inverts primary screen of dual head"
date: 2010-05-14
forum: Multimedia Software
---

### Post by richardh9936 on 2010-05-14
Hi *,
I use Ubuntu Netbook Remix, and I've installed Lucid over Karmic.  (Not an upgrade process, because I didn't have enough space on my primary drive.)  I have an Acer AL1511 LCD screen attached as a second screen - ie dual head.  All that works fine.   However....

I rely on xcalib from Stefan Doehla to invert my screen gamma ramps, ie turn them to white text on black backgrounds.  This worked perfectly, just using

xcalib   -i    -alter

but now, xcalib only inverts the netbook screen.  The second screen remains stubbornly unaffected.

Since xcalib has not changed, and it works on one screen, maybe something changed between Karmic and Lucid.

Could someone please tell me how to overcome this problem?

---

### Post by artoonie on 2011-05-23
I'm having this issue too..

---

### Post by richardh9936 on 2011-05-24
i no longer rely on xcalib.  i use the Negative option in Accessibility, and  Compiz now works on my relatively underpowered laptop.  (i'm also using Ubuntu 11.04)

---

### Post by wlarsong on 2011-12-16
I ran across this.

Installed native nvidia drivers so I could do Inversion via Desktop Effects.

I was using xcalib but it wouldn't work for both screens and Desktop Effects would not work for Xinerama. I wanted to do text inverison on both displays. It would only change the primary

When I ran:

xcalib -s 1 -i -a

it altered the other screen. Hope this helps.

---

