---
title: "Yahoo Sports Audio broadcast does not work"
date: 2009-03-12
forum: Multimedia Software
---

### Post by khm on 2009-03-12
[http://rivals.yahoo.com/ncaa/basketball/collegebroadcast](http://rivals.yahoo.com/ncaa/basketball/collegebroadcast)

I cannot get the audio to play at all.  The flash all loads fine, but the audio never starts.  The Play button is grayed out, also.

Any ideas?

---

### Post by khm on 2009-03-12
Or I could use this stream:
[http://stream.hostinteractive.com/links/sec/2009/2009_bkm_tourney.asx](http://stream.hostinteractive.com/links/sec/2009/2009_bkm_tourney.asx)

I tried VLC and got:
```
[00000410] access_http access error: cannot connect to stream.hostinteractive.com:80
[00000410] access_mms access error: cannot connect to stream.hostinteractive.com:80
[00000408] main input error: open of `http://stream.hostinteractive.com/links/sec/2009/2009_bkm_tourney.asx' failed: could not create access

```

Tried mplayer and got:
```
Playing http://stream.hostinteractive.com/links/sec/2009/2009_bkm_tourney.asx.
Resolving stream.hostinteractive.com for AF_INET6...
Couldn't resolve name for AF_INET6: stream.hostinteractive.com
Resolving stream.hostinteractive.com for AF_INET...
Connecting to server stream.hostinteractive.com[64.191.144.223]: 80...
connection timeout

```

---

### Post by wolfen69 on 2009-03-12
works for me. doesn't sound like an ubuntu problem, but for some reason the network is not letting you access it. are you using a firewall? do you live in the US?

---

### Post by khm on 2009-03-12
> **wolfen69 said:**
> works for me. doesn't sound like an ubuntu problem, but for some reason the network is not letting you access it. are you using a firewall? do you live in the US?

Yes, live in the US.  

I'm behind a proxy, but I have my http proxy setup already in System>Preferences>Network Proxy.

It works for everything else... (and yes, it is using port 80)

I also have the system variable http_proxy set properly.

---

