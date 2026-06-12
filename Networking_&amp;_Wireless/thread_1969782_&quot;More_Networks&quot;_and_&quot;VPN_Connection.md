---
title: "&quot;More Networks&quot; and &quot;VPN Connections&quot; stop working over time."
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by greggreg on 2012-04-30
Hey all, sorry for the large pic heavy post. Also I'm not sure if this is the correct forum as it's more a UI issue than a networking issue though it is directly networking related.

I've been having some difficulty with the ubuntu network utility.  After a while, it seems no not be able to load the list of more networks or vpn connections. Logging in and out fixes it some times, restarting always fixes it, but other than that I can't get it to work again. This seems to happen every time ubuntu is on for over a day or so, weather it's on continuously or with me putting it to sleep intermittently.  Below are some screen shots illustrating this. I am running an up to date(as of this post) ubuntu 12.04.

My normal list of "More Networks":
[IMG]http://i.imgur.com/sOph3.png[/IMG]


My normal list of "VPN Connections":
[IMG]http://i.imgur.com/TY0SH.png[/IMG]

Broken list of "More Networks":
[IMG]http://i.imgur.com/spAwG.png[/IMG]

Broken list of "VPN Connections":
[IMG]http://i.imgur.com/Bg9Op.png[/IMG]

Any thoughts?

---

### Post by kingmesal on 2012-05-17
I have had this problem for a long time... I wrote a script to rectify it when it happens... this restarts the applet, which means this has no impact on your actual networking...

#!/bin/bash

KEY="nm-applet"
PID=`ps ax | grep "${KEY}" | grep -v grep |  awk '{ print $1 }'`

kill -9 $PID

sleep 1

nohup sh -c "exec $KEY 2>&1" >/dev/null &

sleep 2

---

### Post by tomanizer on 2012-12-13
Are there any plans to fix this issue?

It does not only affect the wireless menu but all Ubuntu apps that use sub-menus.

---

