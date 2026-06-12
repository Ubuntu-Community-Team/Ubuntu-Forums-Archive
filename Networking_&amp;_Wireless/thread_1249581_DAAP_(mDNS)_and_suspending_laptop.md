---
title: "DAAP (mDNS) and suspending laptop"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by Boondoklife on 2009-08-25
Here is a relatively wierd problem that I am having. When I suspend my laptop and then bring it back online, it is no longer able to detect a firefly, daap server in any of the media players.

I did a little looking and have not been able to find out why this is happening.

I have tried all of the following:
  1) disable firewall
  2) restart connection

Some looking found me this command, which is able to detect the servers too and give you some information on them. When I first boot up the command runs fine and I can see the server, along with in bashee etc. However, when I suspend and then come back online it is not able to see the server just like the media apps.

```
mono /usr/lib/mono-zeroconf/MZClient.exe -v -r -t _daap._tcp
```Any ideas or help would be appreciated.

---

### Post by Boondoklife on 2009-09-03
Any takers on this, I can not seem to resolve the problem.

This seems to be an issue that is not related to the media player app as it happens in both rhythmbox and banshee. Where should I file this as a bug?

---

