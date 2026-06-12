---
title: "Copy mythbuntu from one HDD to another"
date: 2009-09-12
forum: Mythbuntu
---

### Post by se99paj on 2009-09-12
So I after my last mythtv box died I have gone out a purchased a new system using components that are a bit more uptodate.

I now have a whopping 1TB drive instead of my previous 250GB drive, I could go through and reinstall a fresh mythbuntu OS on the new 1TB drive but my old setup was heavily customised and to be honest it would take me ages to find out how I had it setup before.

But I still have the old HDD from my old setup, so I thought why not just drop that HDD drive into my new system. Unfortunately this didn't work I seem to be getting an error that I cannot resolve. So I was thinking is there a way to copy the OS from one HDD to the other so that I can use the 1TB drive to store the OS?

---

### Post by klc5555 on 2009-09-12
> **se99paj said:**
> So I after my last mythtv box died I have gone out a purchased a new system using components that are a bit more uptodate.

I now have a whopping 1TB drive instead of my previous 250GB drive, I could go through and reinstall a fresh mythbuntu OS on the new 1TB drive but my old setup was heavily customised and to be honest it would take me ages to find out how I had it setup before.

But I still have the old HDD from my old setup, so I thought why not just drop that HDD drive into my new system. Unfortunately this didn't work I seem to be getting an error that I cannot resolve. So I was thinking is there a way to copy the OS from one HDD to the other so that I can use the 1TB drive to store the OS?

The first idea was better, and use the 1TB drive just for recordings storage. You should be able to drop the old drive in and direct Grub to boot it (by booting from the install CD and running Grub). If the old OS install really can't  boot from its original drive (because of some unlikely incompatibility with the new hardware or file corruption) it certainly should still not be able to boot when copied to a different drive. So what was the unresolvable error?

---

### Post by se99paj on 2009-09-13
It looked like my original problem has now been resolved, I'm sure it wasn't working yesterday.

Anyway I now have the 250GB drive with the OS installed running and the 1TB drive is also available. I'd still like to move the OS off the 250GB drive but I'd like to move it to a 500GB drive that i have so the setup would be:

500GB (PATA) - With OS installed, it will also allow me to use 500GB to store recordings.
1TB (SATA) - Used to store my archived recordings as videos.

This will allow me to get rid of the 250GB drive, I'm keen to do this as its the oldest drive that I've got. Also by moving to 500GB it gives me more room to store the recordings.

I've found some information on how to clone hard drives so I'll try and follow these and let you know how I get on.

---

