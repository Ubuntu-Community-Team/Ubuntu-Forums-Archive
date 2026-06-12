---
title: "SSH form coffee shop open network"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by rafaelperrone on 2011-10-20
I have a Ubuntu 11.04 desktop at home with a verified working SSH server (I can ssh to it form my android phone using 3G).

But there is this cafe place that I frequently go to and I can't ssh to it from the cafe (open) wifi hotspot. I'm sure it's not a server issue because at the same time I can ssh using ConnectBot on my android phone. Also, I can ssh using my phone connection on my Macbook.

I receive the following message with -v (replaced some values to keep privacy):

```
ssh -p 50022 -v myuser@mystatic.dyndns.org
OpenSSH_5.6p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for *
debug1: Connecting to mystatic.dyndns.org [some.ip.im.using] port 50022.
debug1: Connection established.
debug1: identity file /Users/myuser/.ssh/id_rsa type 1
debug1: identity file /Users/myuser/.ssh/id_rsa-cert type -1
debug1: identity file /Users/myuser/.ssh/id_dsa type -1
debug1: identity file /Users/myuser/.ssh/id_dsa-cert type -1
ssh_exchange_identification: read: Connection reset by peer
```

I have several questions.

First, why it doesn't work? My guess is that cafe network router is blocking connections on port 50022.

BUT if my guess is correct, why can I still start communication with the ssh server at home? (as the line "connection established" says.)

ANYWAY, if my guess is correct, would it work if I change ssh port on server to 22? I know it depends on cafe router config but is it usual to leave 22 port open?

Well, any help will be appreciable.

---

### Post by Murukesh on 2011-10-22
I don't use ssh much, so I don't know for sure, but is the identity file type being -1 okay?

---

