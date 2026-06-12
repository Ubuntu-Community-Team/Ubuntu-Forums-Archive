---
title: "How to find out who is tunneled using ssh?"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by ourAri on 2009-06-23
Hi,

I have a few users who use their accounts only to tunnel an ssh link for secure web surfing. I have limited their shell to be restricted shell, so that they do not have access to files on the system.

The problem is if they close their shell window (but still  connected through the ssh tunnel), I cannot find out if they are connected to the system or not, i.e., the following commands don't show if their are logged in: who, finger, last, lastb.

Any help? How can I find out who is active on an ssh  tunnel?

Thanks.

More details: My users use the Tunnelier program ([http://www.bitvise.com/tunnelier](http://www.bitvise.com/tunnelier)) on windows in order to establish the tunnel

---

### Post by Brandon Williams on 2009-06-23
You can view the process table. Run 'ps -fC sshd' to get a listing of all sshd processes. There will be two, one owned by root that is labeled private ('[priv]') and one owned by the user. Both will indicate the user who is logged in.

---

### Post by ourAri on 2009-06-24
> **Brandon Williams said:**
> You can view the process table. Run 'ps -fC sshd' to get a listing of all sshd processes. There will be two, one owned by root that is labeled private ('[priv]') and one owned by the user. Both will indicate the user who is logged in.


Thanks! That's what i wanted :D

---

### Post by ourAri on 2009-07-09
> **Brandon Williams said:**
> You can view the process table. Run 'ps -fC sshd' to get a listing of all sshd processes. There will be two, one owned by root that is labeled private ('[priv]') and one owned by the user. Both will indicate the user who is logged in.

I use this command and I'm able to find out who is currently in, but how can I find out the history of users loging in? "last" command works only for users using a terminal, not for tunnel only users. Please help!

---

### Post by ericab on 2009-07-09
hey can you shoot a pm my way with a link to your site ? i may be interested in signing up for your ssh tunnel service.

---

### Post by Brandon Williams on 2009-07-10
The only thing I can think of for tracking login history for tunnel-only connections is to scrape the details from /var/log/auth.log. I think it will show you when each individual session starts and stops, but it will be a bit of a pain.

Start with 'sudo grep sshd /var/log/auth.log' to get a sense of how the relevant records in the log are formatted.

---

