---
title: "HDMI and a resolution of 1366x768..."
date: 2012-02-28
forum: Multimedia Software
---

### Post by tjazar on 2012-02-28
Okay, here's the setup: Dell Inspiron 14z, with Intel integrated graphics. The TV I'm trying to output to is an Olevia 232V (they're long since bankrupt, so support from them is not happening). I'm using Xubuntu 11.10.

When I plug in HDMI, my TV says "Invalid format." Indeed, the only format is seems to care for is 640x480 @ 60Hz, no more and no less. Even at that resolution, the right side of the display is cut off by about 15-20%. Xrandr says the preferred resolution for the TV is 1360x768 @ 60Hz, but that still gets me the "Invalid format" notification.

Now what really frustrates me is the Windows 7 actually DOES work. Using Intel's graphics properties app (I forget the name of it), I can set a custom resolution of 1366x768. Windows will tell me that's not the preferred resolution, but it works anyway. In fact, it's the only resolution that works: 640x480 yields nothing but "Invalid format," as does 1360x768.

So, how can I force Xubuntu to use the non-standard resolution of 1366x768 on HDMI? I'd love to not have to dual boot with Windows just to use my lappy as an HTPC. Any ideas on how I can get rid of this problem?

---

