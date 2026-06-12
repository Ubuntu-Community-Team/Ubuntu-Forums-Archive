---
title: "HD channels on UK Freeview"
date: 2012-05-06
forum: Mythbuntu
---

### Post by NautiusMaximus on 2012-05-06
I've just realised that in theory I could watch HD channels over Freeview (I'm in the London area and my nearest transmitter is the Crystal Palace one) if I were to buy a DVB-T2 tuner card and fit it to my system.

Just wondering if anyone has done this and how successful it was? Any dos or don'ts I should be aware of?

Is it likely that I'll plug in the tuner card and it will just work, or do I need to take a week off work to frig about with it getting it configured right? That sort of thing.

Thanks
NM

---

### Post by Chris Musampa on 2012-05-06
Was pretty plain sailing for me, I bought a quad tuner TBS card, they do a dual version also.

[http://ubuntuforums.org/showthread.php?t=1949102](http://ubuntuforums.org/showthread.php?t=1949102)

Edit: I'm still on 11.10, haven't got around to trying 12.04 yet.

---

### Post by jksj on 2012-05-07
The PCTV DVB-T2 Nanostick tuner works out of the box in Myth 0.24.1 and 0.25 on Ubuntu 11.10 and 12.04.
You can recieve all the HD channels simultaneously from the single mux using one stick. With Myth 0.24, I got the occasional missed recording when multiple streams were recording and a channel change occurred. Extending all three timeouts on the tuner page mitigated this (& setting quick tune). Note I am running on an Atom single core so processing power is limited.
I achieved 100% reliability on 0.24 by using two PCTV nonosticks with only one recording allowed per device.
0.25 performs much better than 0.24 so the extended timeouts may not be necessary but I have not tried returning these to default.

---

