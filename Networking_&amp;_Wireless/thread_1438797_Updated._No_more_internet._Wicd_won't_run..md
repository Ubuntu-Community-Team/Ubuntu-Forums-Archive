---
title: "Updated. No more internet. Wicd won't run."
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by skeetwood-mac on 2010-03-25
Well it seems like every 5 min the update manager is barging in telling me to update so I did last night and then this morning I turn on my computer and a window pops up that says "wicd needs your password" or something to that effect so I put it in. Then I notice wicd is not running. So I click on it in the menu and it pops up in awn for a second then disappears. As I have said before I am fairly new to linux so Im  having trouble figuring this out. I don't know any commands i should run or where to start even. My computer is not much use to me without the internet so I would really like to get this fixed. Thanks!

---

### Post by skeetwood-mac on 2010-03-30
never mind i fixed it.

---

### Post by HobbitTR on 2010-04-10
> **skeetwood-mac said:**
> never mind i fixed it.
Why not tell the forum HOW you fixed it please? I had a similar problem with a dbus error. Running this solved it:
code:

sudo wicd -foe

revealed a parsing error in /etc/wicd/wired-settings.conf -- 
There will probably be a line with an empty "[]" on it, remove that line. 

Now, /etc/init.d/wicd start starts the daemon,
and wicd-client works fine as well, and I'm back online.

---

