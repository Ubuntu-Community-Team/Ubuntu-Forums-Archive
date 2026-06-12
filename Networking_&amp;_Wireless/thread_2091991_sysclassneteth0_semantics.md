---
title: "sys/class/net/eth0 semantics"
date: 2012-12-06
forum: Networking &amp; Wireless
---

### Post by don1000 on 2012-12-06
There appears,to me at least, an awful amount of confusing information around about
the meaning of the /sys/class/net/eth0 values.

For example, when unplugging ethernet cable I get 
carrier = 0
operstate = down.

Plugging ethernet back in
carrier = 1
operstate = up

After rebooting system.
carrier = 1
operstate = unknown.

However many claim that they always only see operstate = 'unknown' and the fact that
it is never given as 'up' is a Debian bug. They make no mention of it being given as 'down'.

But it seems to me that a change in state from 'up' to 'down' is only
given if it changes during a session, which might possibly be the intent.

It is also frequently stated that when carrier value is'0 'it 
definitely indicates a broken physical link and that this is possible
even when operstate is given as 'up'.

But in all of this no one refers to an authority or prinmary source
for what is stated. Yet somewhere within the Linux documentation 
the semantics of sys/class entries must surely exist, but so far
I haven't been able to track it down.

Any help or guidance would be most appreciated.

---

### Post by don1000 on 2012-12-07
Missed out the obvious source.

Found all I needed in the Kernel Documentation and other docs to which it refers.

Appears that most of the confusion arises from a failure to distinguish between administrative and operational states

---

### Post by charles75 on 2013-06-26
Could you please give us the links to the documentation that you found?

Thanks

---

