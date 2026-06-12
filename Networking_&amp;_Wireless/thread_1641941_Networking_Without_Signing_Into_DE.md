---
title: "Networking Without Signing Into DE?"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by clevertomato on 2010-12-09
I have an old laptop (AMD 64-bit CPU) computer that has an LCD going bad. Jaunty & Maverick are installed. SSH server is also installed. The problem is, I have no network connectivity unless I'm logged into the DE. Then Network Manager activates and there is connectivity.

How can I have network connectivity (wireless and/or wired) on bootup, not only when I'm logged into the DE?

---

### Post by CharlesA on 2010-12-09
Does it have to connect to a wireless network or something?

I'd just remove network manager, but that's just me.

I'm running 10.04 Desktop and it just sits at the login screen. I can SSH in without any problems.

---

### Post by clevertomato on 2010-12-09
Yes, since it's a laptop PC, it doesn't always sit in the same place. When it's home (which is most of the time), it connects to my WPA/ WPA 2 Personal wireless network. I can plug it into ethernet, but many times it's not convenient.

I've never removed Network Manager, and I understand it is considered part of the "main" Ubuntu package. I am certainly familiar with "sudo aptitude remove package-name" but besides that, I would need more specifics on how to get this working.

---

### Post by CharlesA on 2010-12-09
Ok. I'm not sure if you can do it if it's set for wireless access.

However, in network manager, is wireless set to "all users" ?

---

### Post by clevertomato on 2010-12-09
Yes, wireless is set to all users.

---

### Post by CharlesA on 2010-12-09
Hmm ok.

You can try setting it so that you aren't using network manager.

See here:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by clevertomato on 2010-12-09
Thanks. I was looking for that thread.

---

### Post by CharlesA on 2010-12-09
Hope it works for you. :)

IMHO: Use wired for a server, as wireless can add a bit of complexity to your setup.

---

