---
title: "CSF Firewall Help :: Missing IPTables Modules"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by own3mall on 2013-07-18
Hi Guys,

When I test to see if CSF Firewall will work on my system, I get this output:

```

Testing ip_tables/iptable_filter...OK
Testing ipt_LOG...FAILED [FATAL Error: iptables: No chain/target/match by that name.] - Required for csf to function
Testing ipt_multiport/xt_multiport...FAILED [FATAL Error: iptables: No chain/target/match by that name.] - Required for csf to function
Testing ipt_REJECT...OK
Testing ipt_state/xt_state...FAILED [FATAL Error: iptables: No chain/target/match by that name.] - Required for csf to function
Testing ipt_limit/xt_limit...FAILED [FATAL Error: iptables: No chain/target/match by that name.] - Required for csf to function
Testing ipt_recent...OK
Testing xt_connlimit...FAILED [Error: iptables: Protocol wrong type for socket.] - Required for CONNLIMIT feature
Testing ipt_owner/xt_owner...FAILED [Error: iptables: No chain/target/match by that name.] - Required for SMTP_BLOCK and UID/GID blocking features
Testing iptable_nat/ipt_REDIRECT...OK
Testing iptable_nat/ipt_DNAT...OK

RESULT: csf will not function on this server due to FATAL errors from missing modules [4]

```

I'm running Ubuntu 10.04 on kernel 3.10.1.  Anyone know how to fix these issues?  I've used modprobe for each of these modules, but it doesn't work.

```

sudo modprobe xt_connlimit

```

```

@:~/Downloads/csf/csf$ sudo modprobe ipt_LOG
FATAL: Module ipt_LOG not found.

```

modprobe ipt_LOG is not found though.  How do I enable / get / install these modules?

---

