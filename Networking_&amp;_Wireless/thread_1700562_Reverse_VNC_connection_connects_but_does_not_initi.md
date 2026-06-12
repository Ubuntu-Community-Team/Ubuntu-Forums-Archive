---
title: "Reverse VNC connection connects but does not initiate"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by Another Quixote on 2011-03-05
Hey guys,

Trying to set up reverse VNC connections from my laptop from Ubuntu 10.10 to family and friends using both Linux and Windows.  So far I've tried a few different VNC packages on both ends and I get the same result in all. For example, in xtightvncviewer I get:
```

$ xtightvncviewer -listen
xtightvncviewer -listen: Listening on port 5500
xtightvncviewer -listen: Command line errors are not reported until a connection comes in.

```

Then on the client machine (in this case another laptop running Ubuntu 10.10 on the same WLAN) the connecting client just hangs, and nothing happens on either end. At first I thought the was no connection but as soon as I stop the listening service, the client instantly reports that the connection was dropped unexpectedly or (depending on which VNC viewer I try to connect with) that the server has closed the connection.

Anyone know what I might be doing wrong?

Thanks in advance,

- Q

---

