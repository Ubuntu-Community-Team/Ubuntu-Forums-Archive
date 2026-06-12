---
title: "Old-style update notifications"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by frankbooth on 2011-04-11
Has anyone been able to configure update-notify to act like it used to back in the days? (Icon pops up in the systray when updates are available)
I've been playing with the whitelist (for systray) but haven't been able to get it right.

**Solved!**

**HOW TO:**

For old style notifications:
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```
BUT! Systray icons are blacklisted in 11.04.

To see the current whitelist:
```

gsettings get com.canonical.Unity.Panel systray-whitelist

```

The output should look something like this:
```

['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray']

```

So we add update-manager & update-notifier (adding both just in case) to the whitelist:
```

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'update-notifier', 'update-manager']"

```

(more info regarding whitelist @ [http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/) )

You should now be able to see the updates in the systray like this:
[img]http://data.fuskbugg.se/skalman02/systray.png[/img]

---

### Post by dino99 on 2011-04-11
it have not worked for ages, but i dont really care about it (some kind of useless)

---

### Post by KegHead on 2011-04-11
Hi!

Try:

Control center...startup applications.

KegHead

---

### Post by frankbooth on 2011-04-11
> **dino99 said:**
> it have not worked for ages, but i dont really care about it (some kind of useless)

It works in 10.10 by a simple change in gconf...

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

I tried adding update-notifier and update-manager in the whitelist (see: [http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/) for more info) but it didn't work.

---

### Post by KegHead on 2011-04-11
Hi!

Great!

Please mark your thread as solved.

KegHead

---

### Post by frankbooth on 2011-04-11
> **KegHead said:**
> Hi!

Great!

Please mark your thread as solved.

KegHead

Are your responses automated? They make no sense...

---

### Post by uRock on 2011-04-11
> **frankbooth said:**
> Are your responses automated? They make no sense...

He/she is saying that you should mark your thread as solved if it is solved, which makes perfect sense.:p

---

### Post by KegHead on 2011-04-11
Hi!

Absolutely not!

Use thread tools!

KegHead

---

### Post by frankbooth on 2011-04-11
> **uRock said:**
> He/she is saying that you should mark your thread as solved if it is solved, which makes perfect sense.:p

Funny :) nothing has been solved though. Spamming threads with "Mark solved if solved" seems rather pointless. The thread is far off-topic as it is...

---

### Post by uRock on 2011-04-11
You've listed how to fix your problem in 10.10 and that it is broken in 11.04, which makes me wonder which version you are using.

Have you tried KegHead's advice given in post #3?

---

### Post by frankbooth on 2011-04-11
> **uRock said:**
> and that it is broken in 11.04

This is based on what a friend told me. I can't find any report on launchpad, so I think it's fair to call it shenanigans.
Removed the comment from the post to make sure nobody can misinterpret it.
First post has been edited as well to make it more clear.

---

### Post by MightyMouse on 2011-04-11
On Natty (11.04) from what I see the update-notifier is listed in start-up applications and when you try 'update-notifier' in a terminal it also says that the notifier is running. 

I have bee running this version fro two days now but have to confirm I never saw an update notification.

---

### Post by dino99 on 2011-04-11
the same issue also when automatic download is checked into synaptic, it never work

bug #740761
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/740761](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/740761)

---

### Post by Harry33 on 2011-04-11
This obviously does not solve anything, but indeed the exceptations are ceased.
I have uninstalled long time ago these packages:
- update-manager
- update-manager-core
- update-notifier
- update-notifier-common
And yes, also several meta-packages, like ubuntu-desktop, -standard and -minimal.

---

