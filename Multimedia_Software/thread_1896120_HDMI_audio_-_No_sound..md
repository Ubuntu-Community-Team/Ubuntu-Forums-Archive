---
title: "HDMI audio - No sound."
date: 2011-12-16
forum: Multimedia Software
---

### Post by Darknote on 2011-12-16
Hi everyone.
Finally after weeks of research on the web I gave in and decided to post a question.

How can I get HDMI audio to work?

I've browsed through the web and found so many suggestions, some which have caused me massive problems as well, and some which don't work at all, and some which are just outdated. Nothing I've found has worked so far. The first most obvious thing I tried was to enable HDMI output in System Settings. That didn't work. And then when I had found some info on the web and made some changes I went back to Settings and enabled HDMI output and tried and it never worked.

I've got the Acer Timeline X with AMD/ATI Radeon HD 5600 series. Something I never would have bought in the first place if I'd known the trouble it would have brought me when working with Linux. But the sucker was bought and it was not exactly cheap either so I have to live with it for at east a few more years and try to make it work properly.

It's amazing to see how many are having trouble with the HDMI audio issue. One would have thought that when a problem is so widely spread that it would be fixed properly. I mean, HDMI isn't going away.

Can anyone please help me?
I've re-installed my system way too many times for this s**t. I'm trying to be productive, but instead I'm just always stuck in some configurational mess which never seems to end.

Thank you,
Villi.

---

### Post by BicyclerBoy on 2011-12-16
I believe this laptop uses the AMD version of optimus..
You need to know the full model number/name..

The hybrid AMD graphics seems to be better supported in linux by AMD Catalyst driver.

Don't blame linux for not supporting this h/w mess, optimus was designed/implemented as windows only. There is no financial incentive to make it work with linux drivers while people continue to buy windows hardware with a windows licence..

You have 3 choices:
- BIOS option to force iCPU **or** AMD discrete GPU
- try using Catalyst to control GPU..
- acpi switching vgaswitcharoo

[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

HDMI audio will not work thru' the AMD GPU without running the AMD catalyst driver.
HDMI audio could work in intel iCPU only mode.

For intel SNA you need kernel 3.x & recent open source intel driver i915/i965.

---

