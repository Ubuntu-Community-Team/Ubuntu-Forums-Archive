---
title: "My Compay Presario M2000 keeps losing the WIFI signal after installing Maverick"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by pbajoswb on 2010-10-11
I have a Compaq Presario M2000 (2010US) laptop that I've installed Maverik on.
I added the "Broadcom B43 Wireless driver" when prompted after the installation. Six months ago I found the webpage....
[URL="http://answers.yahoo.com/question/index?qid=20090203073637AAf3oyr"]
http://answers.yahoo.com/question/index?qid=20090203073637AAf3oyr[/URL]

and with a little searching on Google, I figured out creating the line

SUSPEND_MODULES="b43" in the "/etc/pm/config.d/madwifi" file.

So, with that my computer finds and connects to my wifi hub pretty much instantly when I boot or return from a suspend.

However, with the new install I'm having considerable holding onto my wifi signal. Its varying all over the place and my laptop is now frequently losing the connection entirely. In one session it was lost several times in just ten minutes. In another I was sitting almost literally on top of my hub and still lost the signal. I've also tried it with a different router.

It wouldn't be so bad if it reconnected automatically, but no such luck. The network manager just continually searches; after a few minutes it brings up the dialog to reconfirm my password; after three or so tries with that, it gives up.

However, as I said above, if I reboot or suspend and return, it reconnects immediately.

I've never had this problem before with previous releases. Does anyone know whats causing this and how I can fix it?

---

