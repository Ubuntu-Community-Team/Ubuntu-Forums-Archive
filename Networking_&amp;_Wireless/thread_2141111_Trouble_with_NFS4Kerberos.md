---
title: "Trouble with NFS4/Kerberos"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by Caerostris on 2013-05-01
Hey gus,

I'm trying to set up nfs4 with kerberos authentication but for some reason the client is unable to connect.
When I replace gss/krb5 with an IP address, everything works fine but with gss/krb5 I'm getting "access denied" errors when mounting.
The problem seems to be related to the warnings in /var/log/syslog:
Eos is my server, agon the client.
[https://gist.github.com/Caerostris/0c1e9f326e5e2a71fdfa](https://gist.github.com/Caerostris/0c1e9f326e5e2a71fdfa)

I triple-checked that rpc.svcgssd is running, the KDC daemon is started and I have a valid ticket.

Some people report missing service tickets, but ```
[COLOR=#000000]klist /tmp/krb5cc_machine_MYREALM.TLD[/COLOR]
``` says I'm not missing those service tickets. (Find the output of the command attached in the gist as well)
Everything that might be important should be included the gist, did I miss anything?

I hope you guys can help me, this is driving me nuts! 

Many thanks in advance! :)

---

