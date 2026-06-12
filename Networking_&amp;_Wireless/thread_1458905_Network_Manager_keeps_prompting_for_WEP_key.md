---
title: "Network Manager keeps prompting for WEP key"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by perpetualn00b on 2010-04-20
I've been fiddling with Ubuntu for the first time ever today and eventually managed to get the drivers for the network adapter installed. Now, I'm trying to get the computer running it onto my home network; I set it up to connect automatically, entered the WEP key, and hit apply, marveling at how convenient it was.

...So far it's still caused me less trouble than some of the the bizarre problems I've had trying to get a Windows computer on a network, but...it just won't connect. At all. It says it is connecting, eventually prompts me for the key again, says it is connecting again, etc, repeat on infinite loop. Except for the occasional times that it stops trying and then, oddly enough, proceeds to state that it is not connected to *name of neighbor's network*, which it wasn't trying to connect to in the first place.

What I've read thus far suggests removing the network manager, which, er, I don't exactly understand how to do but could probably figure out with the help of Google. Is this the best course of action, or am I missing something?

---

### Post by spiky001 on 2010-04-20
it is proberbly asking for keyring password which you created

---

### Post by perpetualn00b on 2010-04-20
...I'm probably not going to end up posting a whole lot because, embarrassingly, I managed to solve the problem myself in a very simple way. All I had to do was restart it and delete all of the entries for automatically trying to get on the network, then let it create one on its own. (Am fuzzy-brained from a long day, not sure how to explain what I figured out.) But it had nothing to do with the keyring thing. Thanks, though!

---

