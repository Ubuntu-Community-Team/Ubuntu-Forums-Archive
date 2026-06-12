---
title: "Having trouble with speedtouch 510 v5"
date: 2005-12-23
forum: Networking &amp; Wireless
---

### Post by geearf on 2005-12-23
Hello,

I just got a new modem (well not that goof for what I need, but anyway ..) and I have a problem :

Under windows (sigh, I only use it now, cause it's the only os which have the net, but nothing else :( ) if I install the pppoe extension I can connect to my ADSL provider with the login / password.

Under Ubuntu I tried pppoeconf, but I got various errors (errors for changing the MTU / MRU, error for getting an chap-password, disconnecting the modem).

I also tried to setup the modem as a router and let it deal with the pppoe thing it self (like I did with my previous speedtouch home), but then it would not connect to the net anymore (I can see that from the led, or from the page connection on 10.0.0.138).

I run Kubuntu Breezy.

If you have any tips on this I'll be glad.

Thanks,

---

### Post by geearf on 2005-12-24
please.

---

### Post by geearf on 2005-12-25
I also tried with rp-pppoe, but still I get a timeout.
With pon dsl-provider, plog don't give me any error message now :(

---

### Post by mips on 2005-12-26
Why dont you let the router handle the PPPoE stuff, it is so much easier and way less of a hassle.

---

### Post by geearf on 2005-12-26
Hello,

well I've tried that too, but the router cannot connect : problem of authentication, and I don't know why. I have tried with another firmware but still the same ..

That is why I am looking directly at the pppoe bridge here.

I have gone a little further, it seems better with modules pppoe, ppp_async and ppp_synctty launched, but still no connection.

Pon just tells me "tcflush failed: Bad file descriptor" and nothing else much, rp-pppoe just gives me a timout.

Thanks

---

### Post by geearf on 2005-12-26
Well actually I got the router working, so everything is fine now :)

---

