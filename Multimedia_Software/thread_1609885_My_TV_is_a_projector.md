---
title: "My TV is a projector???"
date: 2010-10-30
forum: Multimedia Software
---

### Post by marknu1 on 2010-10-30
Hi All,

I am setting up a HTPC and hoping to use 10.10 of either Ubuntu or Kubuntu on it.  I've run into a problem in both of the aforementioned versions, that might keeping from doing that.

I have an ATI HD5550.  With the default drivers the desktop extends beyond the edges of my TV screen, which, by the way, is a Panasonic plasma TH-37PX60U.  If I install the proprietary drivers the desktop is too small and leaves gray borders of about 1" on the sides, and maybe 5/8" on the top and bottom.

No problem, I thought; I'll just use the overscan adjustment and expand the desktop to fill my screen.  The problem is, Catalyst Control Center(CCC) shows my TV as a projector, and doesn't offer overscan as an adjustment (this probably makes sense, technically; I know nothing about projectors).

So I don't have overscan adjustment, and I'm not sure how to 'tell' CCC that my TV is...A TV!  With this same hardware, if I install Windows 7, CCC has no problem detecting my TV and provides the appropriate HDTV options.  I'd rather not use Windows.

My motherboard has on-board Nvidia graphics.  I don't really want to use the embedded graphics, but for grins I tried switching to them and installed the Nvidia proprietary drivers.  In that setup the Nvidia control panel correctly identifies my TV and gives me the overscan option.

In my testing, I thought perhaps this might be a 10.10 issue, so I installed Ubuntu 10.4; same behavior with the ATI card.

I happen to have an ATI HD4350 in one of my PCs, so I gave that a shot in the HTPC; same problem.

In my Googling, I've yet to find anyone having the same issue, but it may be that I'm not providing the correct search criteria.  So here I am.  Does anyone have any ideas?  Thanks in advance for any help.

---

### Post by wilee-nilee on 2010-10-30
If you break up that paragraph it will be easier to read.;)

---

### Post by marknu1 on 2010-10-30
You're right.  I _had_ thought about that before I submitted the post.  Anyway, I've edited the original post, in hopes that it will be a tad easier to read ;-)

---

### Post by slikar on 2010-11-03
Same problem - the missing underscan/overscan slider and my tv recognized as a projector.
With the open source driver everything works fine though.

Is there a way of resetting the Catalyst driver underscan value to zero from the terminal (considering that CCC is being useless is this case)?

Cheers.

---

