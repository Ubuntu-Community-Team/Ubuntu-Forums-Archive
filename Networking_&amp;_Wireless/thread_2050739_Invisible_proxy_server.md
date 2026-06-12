---
title: "Invisible proxy server?"
date: 2012-08-31
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2012-08-31
I've been trying to import some keys, with the following result:
```
root@pwa-K60IJ:/etc/apt# apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.p9j5hkBcgz --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
This might at first not seem to be a networking problem.  (The server at **keyserver.ubuntu.com** is alive and well; in any event the choice of keyserver makes no difference.) But the symptoms are just what I would be getting if I was trying to retrieve the key through a misconfigured proxy server.  In fact, a number of people have seen this error when they were using proxy servers.  And for many people, the command works correctly.

But in my case I'm not using a proxy server.  I never set one up, and Systems Settings verifies that there isn't one.  However, I'm wondering if there's something in my environment that makes it *appear* to **gpg** as though I'm using a proxy server.

---

