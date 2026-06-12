---
title: "Bug with wireless, how do I fix it?"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by iTails on 2011-07-24
There is a bug in Ubuntu 11.04 that's really been tweaking me. Let's say that when I go to connect to a network and I cancel right in the middle of it and connect to another network, it won't connect to any network after that, at all. I've restarted, I've disabled and re-enabled networking. I KNOW the driver for the wireless works because I used it right out of the package. This always happens when I connect to a new network. Anyone else have/had issues with this? Is there any way to fix it?

My network card: Atheros AR9285 WNA

---

### Post by iTails on 2011-07-25
Nevermind, I had a friend who helped me fix it. But for future reference, I am going to post how I did it and hopefully this will be fixed in Ubuntu 11.10 or an update for 11.04

First you are going to want to disconnect from any networks you are trying to connect to and disable Networking from the networking icon in the panel.

Next you are going to want to go to "Edit Connections" at the bottom; as seen in the picture below.
[img]http://i54.tinypic.com/3469pqg.png[/img]

Now go to the wireless tab and select the wireless connections and delete them.
[img]http://i52.tinypic.com/xku6ao.png[/img]

A logout, or to be even more sure, a restart is required for the settings to take effect. Now you should be able to connect and put in your WEP key.

I hope this helps anyone who had the same problem I had.

---

