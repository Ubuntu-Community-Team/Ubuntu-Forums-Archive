---
title: "gpg problem, host not found error"
date: 2012-09-01
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2012-09-01
I'm running Kubuntu 12.04 and trying to update it. I've again been hit by a problem I had a year ago that's never been solved and seems to involve some obscure issues about proxy servers.  It is illustrated by this:

Code:

```
pwa@pwa-K60IJ:~/Documents$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys A8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
The problem is not with the choice of keyserver; I've tried several, all with the same behavior. I've opened port 11371, which some people thought might be the problem. And I can link to any of the keyservers, so the "Host not found" message is bogus. The command I used works for most people but not for others (like me).  In fact, it works for me too in an older 10.04 Kubuntu system.

Apparently behavior like this can arise if you're behind a proxy server, but I'm not. System Settings verifies this. But perhaps there's something in my environment that makes it *appear* as though I'm behind a proxy server.

I'm not expecting help with the gpg issues in this forum, but the "Host not found" message does seem to be a networking issue.  I'm running wicd, if that's relevant.  If I could see the messages going back and forth just before that message, I might get some idea of where the fault lies, but I don't know how to capture them.

---

### Post by pwabrahams on 2012-09-01
I just had an inspiration.  I replaced the hostname by its IP address, and the retrieval worked.  Of course, that should not be necessary.  A bug lurks here!!

---

