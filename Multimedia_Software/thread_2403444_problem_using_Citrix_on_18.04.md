---
title: "problem using Citrix on 18.04"
date: 2018-10-11
forum: Multimedia Software
---

### Post by trintadosete on 2018-10-11
Hey Guys,

I am trying to use Citrix to connect to a computer at my university. Everything works fine when I connect from a windows machine. However, it is not working on Ubuntu.

I tried Citrix 13.3, 13.6 and 13.10 but none have worked.
I installed the clients, got the certificates from firefox and re-hashed them. When I try to log in, I get the following message:

> Your account cannot be added using this server address. Make sure you entered it correctly.
An unexpected error occurred. The AuthManager log or trace files may contain information about the error

When I run the config wizard on command line (/opt/Citrix/ICAClient/util/configmgr &), I get a different error on konsole:

> Error adding store:Email address lookup failed (either missing "dig" or no entry exists)[65275]

Any idea on what could be happening?

---

