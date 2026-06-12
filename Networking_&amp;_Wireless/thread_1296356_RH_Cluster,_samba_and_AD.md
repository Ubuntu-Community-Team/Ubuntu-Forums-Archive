---
title: "RH Cluster, samba and AD"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by dimothy10 on 2009-10-20
Dear All,

I know this is using Red Hat but my scours of the internet have come up blank and people are pretty good round here with all things linux so I thought I would give it a bash.

A colleague of mine has been struggling with our samba shares.  Through much tweaking we have managaged to get a single linux test server to connect to our 2008 domain and authenticate users connecting to samba shares via AD (using winbind).  This was a step in the right direction as we could not get our previous samba shares to show up in 2008 AD at all and it refused to join the domain.

The next step was to try it on our cluster of Red Hat servers (4 nodes).  All seemed to be going well but we cannot get winbind to get a proper list of users and groups etc.  Red Hat support stated that as winbind was a legacy program it was not really supported and left it at that.  Our musings so far have been to possibly use OpenLDAP (my thinking was to get it to sync with AD so that samba could lookup users in LDAP, as you can tell I am somewhat out of my depth here lol).

I suppose the question is has anyone been able to successfully get a cluster with a samba resource to authenticate against AD?  I have found many guides and examples to do so for standalone single servers but nothing much for a clustered set of servers.  All help welcome!!

Tim

---

### Post by Dr_Hugh on 2009-10-20
Dimothy10

Have you looked at the documentation on the Samba web site?
There are some worked examples of bigger sites.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

