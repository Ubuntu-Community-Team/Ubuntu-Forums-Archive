---
title: "Proxim WD-8470 external antenna"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by mickwombat on 2010-10-20
Hi,

I have an internal wireless card, BCW43xx, on my laptop which works fine, but I also have a Proxim WD-8470 with external antenna.

Every works fine, but was wondering how I can tell that it is actually using the attached antenna, cause I can't see any difference in signal strength when it is attached.

```
iwpriv
``` returns no additional options for this or any interface.

Is there a special driver to use for this card so that I can have the specialised options?

Also, I try to disable the internal wireless, wlan0, by doing the following, ```
ifconfig wlan0 down
``` in order to force it to use the Proxim card, but the damn thing keeps popping back up by itself.  How do I turn it off properly?

Thanks

---

### Post by ricky.t.n on 2010-10-20
Guys, 
       I'm trying to configure my wireless datacard.. But i tried a lot of things.. but it dint work still.. the modem details are:
                                     [Micromax MMX300C(click here for details of modem) ]("http://www.micromaxinfo.com/products/300c.html")
                                    Though the manufacturer says its not supported in linux.. can something be done for it to work on linux.. I've been using windows only for internet.. I can't use linux just because internet doesn't work in it.
Please help me out.
Sorry for posting this here. As I cant start a new thread..

---

### Post by mickwombat on 2010-10-20
Please don't hijack my thread.

---

