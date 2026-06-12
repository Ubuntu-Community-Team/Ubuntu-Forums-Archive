---
title: "Linksys WUSB600N rev 1 should &quot;just work&quot; with 11.04"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by amiliv on 2011-05-04
I see a bunch of posts about WUSB600N, often telling folks to download and compile proprietary drivers from ralink's website.  With Ubuntu 11.04, getting WUSB600N to work might be as simple as disabling rt2870sta (for rev1).  If you have rev 2 card, driver to disable is I believe rt3572sta.

Even if you need to recompile drivers by hand, the right thing to do is to first try nightly build of rt2x00 drivers from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download), and fall back to ralink provided drivers only if things do not work out with rt2x00 drivers.  I saw recent updates on rt2x00 mailing list for rt3572 chip, give it a try if you have rev 2 card.

WUSB600N rev 1 (rt2870 chip) should "just work" with rt2x00 driver included with 2.6.38 kernel in Ubuntu 11.04.  At least it works for me.  You may need to blacklist rt2870sta driver from staging directory so that it does not load and interfere with rt2x00 drivers.

There's one small annoying issue with power save mode on rt2870 chip when rt2x00 is in use, which seems to have just been fixed upstream.  Most users will never notice it, but if you do notice card re-connecting to AP every 10-20 minutes or so, simply disable power saving, and all will be smooth (iwconfig wlan0 power off).

If you have an older Ubuntu release (kernel 2.6.35) and rev 1 card, you should be able to download nightly build of rt2x00 driver from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download).  It worked for me just fine with previous Ubuntu releases.

---

### Post by kittkatt on 2011-05-05
> If you have rev 2 card, driver to disable is I believe rt3572sta.

I tried this and it did not work

---

