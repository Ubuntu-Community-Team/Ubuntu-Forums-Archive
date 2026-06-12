---
title: "MoBlock not starting in 9.10"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by sbussy89 on 2010-02-06
I can't start MoBlock under Ubuntu 9.10. I cleared my blockcontrol.log file so I would know everything in it was from the most recent attempt to start, so here is the entire file:

```

2010-02-06 20:42:03 EST Begin: blockcontrol start
Inserting iptables ...
iptables: Chain already exists.
^M^[[74G[^[[31mfail^[[39;49m]

```

Here is my blockcontrol.conf file:

```

# blockcontrol.conf - configuration file for blockcontrol

# This file is sourced by a shell script. Any line which starts with a # (hash)
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used.

# Refer to blockcontrol.defaults (/usr/lib/blockcontrol/blockcontrol.defaults)
# for the complete set of possible configuration variables with comments.

# Do a "blockcontrol restart" (sometimes even "reload" is enough) when you have
# edited this file.

WHITE_TCP_OUT="http https ssh 5900 ftp"
WHITE_TCP_IN="http https 5900 ssh ftp"
WHITE_TCP_FORWARD="http https 5900 ssh ftp"
WHITE_LOCAL="0"

```

For the record I'm not sure what "WHITE_TC_FORWARD" is for, so I just filled in everything I use to be safe.

Any help? I am running this on a school PC, so the network probably has firewalls out there somewhere, but nothing I am in control of. If it means anything, I have been running PeerBlock under Windows Server 2003 for a few months with no problems. Thanks in advance for any help!

---

