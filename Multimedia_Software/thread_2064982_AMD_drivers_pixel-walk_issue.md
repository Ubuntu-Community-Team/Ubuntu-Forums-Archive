---
title: "AMD drivers pixel-walk issue"
date: 2012-09-30
forum: Multimedia Software
---

### Post by guzzard on 2012-09-30
Hi Everyone,

I have what seem to be a quite unique issue? Have at least not seen anyone else discuss about it anywhere..

My problem is that when I use the AMD propitiatory drivers I get "pixel-walk" in the gray colors on my monitor. It doesn't happen when using the open source drivers, but it does happen with the propitiatory drivers that I prefer to use due to the higher performance in games etc.

The only fix I have found is to open up the Catalyst Control Center every time I start my computer, and change some setting, for example brightness +1, -1 to enable the Apply button. After clicking the Apply button the pixel-walk disappear.

I have made a video to show the issue using this test page: [http://www.lagom.nl/lcd-test/inversion.php](http://www.lagom.nl/lcd-test/inversion.php)

Video here, watch in 1080p: [http://www.youtube.com/watch?v=vX9B2CHcgnY](http://www.youtube.com/watch?v=vX9B2CHcgnY)

My computer setup:
Graphics card: Radeon HD 5750
Monitor: LG W3000H
OS: Ubuntu 12.04 (64-bit)
Kernel: 3.5.4
GNOME Shell 3.4.1
AMD drivers: 12.9 beta (9/26/2012)

This issue was present on 12.8, 12.6, and probably earlier drivers as well.
Earlier kernels 3.5.0, 3.2.x ect makes no difference either.
I have also tested in Ubuntu 12.10 beta, Mint,  and a couple of other distributions, but they all have the same issue.

One thing to note is that in openSUSE 12.2 GNOME (openSUSE-12.2-GNOME-LiveCD-x86_64.iso) with same drivers 12.9 beta (9/26/2012), there is no issue with pixel-walk. Which I find quite strange..

If anyone knows about this issue, or where I should start looking i would really appreciate your help! Thanks!

---

