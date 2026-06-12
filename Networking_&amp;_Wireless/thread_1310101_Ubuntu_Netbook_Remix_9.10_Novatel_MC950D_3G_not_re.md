---
title: "Ubuntu Netbook Remix 9.10 Novatel MC950D 3G not recognized"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by eeexcellent on 2009-11-01
Just installed UNR 9.10 on my EEEPC701 4G and everything works except Novatel MC950D 3G (Rogers Internet Stick).

It worked ok with previous Xubuntu 9.04 (plug stick in, NVTL_AICD mounts, then unmount it manually and then the Network Manager picked it up)

Now with UNR 9.10 the NVTL_AICD does not mount when I plug the stick in, so there is no way to unmount it manually.

The device works when I plug it into my Mac, and it worked with 9.04, so the problem must be UNR 9.10.

Help! This is an important feature that I need. I tested everything else with a Unetbootin USB version before installing... except the 3G stick.  Silly me ;)

-d

---

### Post by pdc on 2009-11-02
there seems to be a problem with 9.10 and if you can you might be best to go back to 9.04 whilst the developers work hard to resolve the issues

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/)

---

### Post by eeexcellent on 2009-11-02
Thanks @pdc, good to hear that this is a common problem and not operator error.

Today I discovered that if I boot up with the 3G modem (MC950D) inserted, Ubuntu UNR 9.10 recognizes it by mounting the CD (NVTL_AICD). I just eject the "CD" and then Network Manager recognizes it as a 3G connection and I'm online.

So for now I just restart my laptop with the device plugged in when I want to use it.  Good thing that shutdown and reboot is very fast with this version of Ubuntu!

Going back to 9.04 is not an option because of the time invested in installing and tweaking this version of the OS to my needs. I agree with the thread that you pointed me to that this should have been taken care of before the release of 9.10, especially the Netbook edition, since I assume a good number of Netbooks run 3G modems...  Looking forward to a patch showing up in my Update Manager very soon!  (Otherwise 9.10 is *darn near perfect* as far as I'm concerned)

-d:)

---

