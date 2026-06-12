---
title: "ath9k Question"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2010-01-31
I'm looking into changing some of the settings for my Atheros AR9285 Wireless Network Adapter (PCI-Express); how would I even go about *starting* to do this? Any help would be *very* appreciated!

Oh, and, if anyone can explain to me why iwconfig would show me a bitrate of 0mbs almost all the time, even when I'm on the Internet and downloading things at blazing speeds, I'd appreciate it.

---

### Post by sirjasonr on 2010-02-10
hello :)
I can direct you to info about the second part of your post as I've been researching this just recently. Check out this: [http://bugzilla.kernel.org/show_bug.cgi?id=12943](http://bugzilla.kernel.org/show_bug.cgi?id=12943)
Apparently it's just a limitation of the wireless extensions and having briefly read over what they've had to say, it seems like you pretty much can't get a reliable link speed reading (correct me if I'm wrong).

As for the first part of your question, I'm not all that sure myself. But it may help others who know more about this sort of thing if you describe what kind of settings you want to change. When it comes to fiddling with 802.11n settings, I think your best bet would be to check out this page: [http://linuxwireless.org/en/users/Documentation/iw](http://linuxwireless.org/en/users/Documentation/iw)
If you don't have iw installed on your system, you can get it from synaptic or by typing sudo apt-get install iw into the terminal.

Hope that helps a bit!

Jason

---

### Post by moore.bryan on 2010-02-10
Thanks for the response, Jason; I thought this thread had fallen into the abyss like so many others! Unfortunately, the kernel bugzilla thread says its "been resolved" when obviously it hasn't, but that's not a surprise; I often see bugs marked as "resolved" when they are far from it.

iw looks like what I'm looking for, but now early-onset senility makes me unable to remember what I wanted to set and why... ;-)

---

