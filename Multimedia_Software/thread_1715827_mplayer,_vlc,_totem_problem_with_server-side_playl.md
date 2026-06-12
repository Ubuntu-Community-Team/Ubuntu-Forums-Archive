---
title: "mplayer, vlc, totem problem with server-side playlist (wsx)"
date: 2011-03-27
forum: Multimedia Software
---

### Post by dfacto on 2011-03-27
Wondering if anyone has a fix for this problem:

Cannot watch second, third, etc, streams from a server-side playlist (ie, .wsx on windows media service).  I have tried mplayer, vlc, totem, and xine.  Xine totally fails and the other three play only the first stream as described.  You can verify it works in wine by using Windows Mediaplayer v10 (`winetricks wmp10` on a clean wine prefix).

The particular example I am dealing with is not an ideal test-case as they dynamically mangle the stream's URL to prevent leeching.  You can test it by either visiting $URL (below) or from command line:

```

URL="http://desitvstreams.hotdnsplus.com/Indian/stargold.php"
MMS=$(wget "$URL" -qO- | sed -n '/src="mms/s/.*\(mms:[^"]*\).*/\1/p')
mplayer -v "$MMS"

```

My research has brought up only two or three random posts citing a similar problem.  All seem to be quite old (circa 2008).  The most relevant is:
[http://forums.techarena.in/mediacenter/894724.htm](http://forums.techarena.in/mediacenter/894724.htm)

I have attached the output from:
```

mplayer -msglevel all=9 "$MMS" &>mplayer.output

```
You will see that mplayer is seeing an EOF and terminating (perhaps the server is too slow so mplayer's timeout triggers EOF condition?).  I tired fooling with -vid/-aid flags to no avail.


Much obliged to anyone who can lend some useful advice.  (PLEASE don't tell me to use a different site.  You're not as funny/cute as you think you are!)

---

### Post by dfacto on 2011-07-26
Appears that it must have been server-side because now it works.

---

