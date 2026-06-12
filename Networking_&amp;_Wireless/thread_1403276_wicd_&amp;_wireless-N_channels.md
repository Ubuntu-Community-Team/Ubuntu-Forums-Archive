---
title: "wicd &amp; wireless-N channels?"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by chitowner2 on 2010-02-10
Anybody out there know why WICD losses wireless connection when the router's channel is changed- and how to recover it on the new channel?

I have WICD on karmic which I am using with an Addesso wireless keyboard. 

For some reason that makes no sense to me, the k/b gets flaky when WICD is linked via wireless-N on channel 6. I have another router that is set to channel 11 and when WICD is connected there, I don't see the k/b balkiness.

I tried changing the first router to channel 11, but after I do that, WICD can't find it. I find no way of selecting a wireless channel in WICD, but I doubt that's the problem, since it seems to detect all channels automatically.

The balkiness of the k/b makes no sense to me, since both routers are on all the time, so presumably both RF channels are also active, but only when WICD connects to a channel-6 router do I have problems with the wireless k/b.

Any useful comment is appreciated.
Thanks,
CT

---

### Post by chitowner2 on 2010-02-10
update

Talked to Adesso tech. They say there is no way to control channel selection with current model  (3000UB) but they are planning to have that option on a newer version.....

SO- back to: Why is WICD unable to find a router after I change it's wireless channel, and what can I do about it?

CT

---

### Post by chitowner2 on 2010-02-12
UPDATE

OK guys, I figgered it out. Have to make changes in router (I have dd-wrt on a Buffalo with wireless-N) with receiving WICD *offline*, THEN connect. Otherwise it apparently can not track the change. 

So I'm good. No more conflict with my nice Adesso wireless keyboard. No more cable and no need for line-of-sight nonsense either. Coooool!

Still have no idea why channel 6 was a problem and channel 11 is OK, but there ya go.   :P

CT

---

