---
title: "Issues With 6 Monitors on 3 nVidia Graphics Cards"
date: 2012-07-02
forum: Multimedia Software
---

### Post by awells527 on 2012-07-02
I continue to struggle with my unusual display setup.  There doesn't seem to be much documentation out there with > 2 monitors spanned across multiple video cards.

This is my hardware setup:

2x EVGA GeForce GTS 450 (01G-P3-1450-TR)
1x XFX GeForce 8600 GTS

I have a total of 6 monitors, two on each card.  On Ubuntu 11.04, I had one card in TwinView, and all others in a separate X session.  It sucked not being able to move windows around, but I dealt with it because there was really no other way I could get it to work with 3D rendering.

I upgraded to 12.04 a few weeks ago, and I have not been able to get my displays working as I had before.  I use the nvidia-settings utility to generate my xorg.conf file.  On 12.04, display 0 loads without issue, but X sessions 1+ bomb with a (EE) log entry in the X logs.

I can post the logs if that would help, but what I'm really looking for are any general guides that are up to date for 12.04.  The nvidia driver (and Ubuntu for that matter) have changed significantly over the last couple years, and a lot of the old threads out there are not of much use anymore.

This is one example thread that I followed for some time: [http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

Any help would be greatly appreciated :)

---

### Post by BicyclerBoy on 2012-07-02
FWIW The latest nVidia 30x drivers series has made changes to multi-monitor xinerama etc..
These changes could have fixed xinerama (so openGL works).
I believe twinview now supports >2 monitors.
That could be "basemosaic"

Annoyingly Mosaic was available for quadro cards.

I have avoided upgrades to this 30x. versions because of the changes..

You can get this driver from xorg-edgers BUT beware that they have also kernel 3.5 (for 12.04). I removed the kernel.

---

