---
title: "Never a connection when I boot up"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by jonbey on 2009-11-19
Whenever I boot up my Ubuntu I have no internet connection. I just have to sudo dhclient (or something like that - will double check - I just up arrow now as it is always there!).

It has been like this for a while. I do not use my Ubuntu so much these days as I no longer serve websites from home, but I plan to start using it a bit more again soon for testing LAMP sites before putting them live.

Any suggestions? Searched the forums but failed to find anything.

---

### Post by Iowan on 2009-11-19
Boot-up or login? If you're using Network Manager, it's probably a login event. Check your connection information (probably Auto Eth0) to verify the "Connect..." checkbox is checked. I presume Network Manager is running...

If you actually want the connection to fire up at boot-up, it'll need to be configured in */etc/network/interfaces*.

Got Jaunty in mind... Karmic calls it something else, and might work differently.

---

### Post by jonbey on 2009-11-19
Well, both, as I always boot up, login and stayed logged in until I shutdown.

Maybe I will upgrade to Karmic (never had the problem before the current version I am using) to see if that fixes it. Otherwise I'll look at the auto connect thing.

Cheers

---

