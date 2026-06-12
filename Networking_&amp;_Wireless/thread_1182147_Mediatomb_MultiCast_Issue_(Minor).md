---
title: "Mediatomb MultiCast Issue (Minor)"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by dob99 on 2009-06-08
I recently switched from Ubuntu 8.04 Desktop to Ubuntu 9.04 Server - it was a completely new machine build too. I have MediaTomb running on the server (the desktop is now gone) and the issue is that it can take up to about a minute for MediaTomb to show up on the media player (a Philips SLM5500). I didn't have this issue with the older machine and the Azureus Media Server (running on a separate Kubuntu 9.04 desktop machine) always shows up immediately. I have also verified the behaviour using Cidero on the Kubuntu desktop.

This is really just a minor annoyance, but I am curious as to the cause and if there is a setting I have missed. Any ideas anyone?

---

### Post by dob99 on 2009-09-22
Ideas anyone?

---

### Post by dob99 on 2009-11-22
OK. It seems that setting "allmulti" on the ethernet interface (sudo ifconfig eth0 allmulti) does the trick.

However, my desktop machine does not have this option enabled (according to ifconfig) and it doesn't suffer from the same problem (with Azureus *or* MediaTomb). Anyone any ideas why this is different between the desktop and server editions? (I suppose it could simply be a difference in the network drivers, but I have no idea how to find out.)

---

### Post by Niksss on 2010-06-01
[SIZE=3]Hey...
  Mediatomb is workin fine on my system.. but cidero is not detecting it... wat are the other media controllers that work fine with mediatomb..?

mediatomb and the cidero are runnin on the same system.. So in the ip settings wat changes shud i make..? sorry for soundin such a newbie..:(

Thanks in advance[/SIZE]

---

