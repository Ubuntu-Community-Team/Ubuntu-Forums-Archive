---
title: "Jack Xruns on Mac mini Intel running Ubun"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by ctignor on 2007-08-31
Hello,

I am using a mac mini intel core duo 1.6 GHz running Ubuntu 2.6.20-16-realtime (the real time patch).

When running just the Jack Control app with Realtime and Forced 16 Bit settings with the built in sound card I can't seem to be able to make Xruns go away despite changing all manner of frames,sample rate, periods or other parameters.  They remain fairly consistent b/w .01 and .02 seconds regardless.

Any advice?

Thanks,

C>T>

---

### Post by ctignor on 2007-08-31
Correction to my last post - changing the "Period" parameter to 3 (from 2) and then even to 4 does indeed seem to greatly reduce this problem. (xrun maybe once every 2 minutes at period=4).  Changing sample rate and frames really doesn't.  Likely this has to do with the not-so professional built in sound card?  Any other configuration tips on the Jack side?

thanks -

C>T>

---

