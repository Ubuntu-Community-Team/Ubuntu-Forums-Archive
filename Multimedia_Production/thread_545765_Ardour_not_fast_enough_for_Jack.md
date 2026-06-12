---
title: "Ardour not fast enough for Jack"
date: 2007-09-08
forum: Multimedia Production
---

### Post by GregoryMA on 2007-09-08
I keep getting this error:
JACK has either been shutdown or it disconnected Ardour because Ardour was not fast enough.  You can save the session and/or try to reconnect to JACK.

I think this is a simple problem to fix but I have not been able to get anywhere with it and it is very frustrating as it basically renders Ardour useless.  Any help would be very appreciated.

---

### Post by krissovo on 2007-09-08
I had that, mine was fixed by configuring jack correctly as the latency was to low for my system

---

### Post by GregoryMA on 2007-09-08
That did it.  Thanks a lot.

---

### Post by Nerdriot on 2008-02-04
I'm not exactly sure how to fix the latency issue... how do you know what to set the input and output latency in Jackd to?

Thanks! :)

---

