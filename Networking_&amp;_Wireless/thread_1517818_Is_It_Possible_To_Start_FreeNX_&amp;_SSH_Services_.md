---
title: "Is It Possible To Start FreeNX &amp; SSH Services Without Starting Session?"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by hayhursm on 2010-06-25
[FONT=Arial][SIZE=2]When I restart my Lucid machine remotely via NoMachine then I am not able to reconnect to SSH (via Putty) or the FreeNX server again.  I’m assuming because a session must begin in order for the SSH and FreeNX services to start.  Is there a workaround for this?  Is it possible for these services to start without a session running?  The thing I liked about Window’s RDP is that I could remotely wake up my PC and then log in without a session already running.  This was very convenient if I powered down my PC and then needed to wake it up sometime later.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by CharlesA on 2010-06-25
Those services should be running whenever the machine is booted up, regardless if you are logged into an X session or not.

Maybe networking isn't coming up until after you login?

---

### Post by hayhursm on 2010-06-26
> **CharlesA said:**
> Those services should be running whenever the machine is booted up, regardless if you are logged into an X session or not.

Maybe networking isn't coming up until after you login?

Yes, you pointed me in the right direction.  I went to System>Preferences>Network Connections and checked "Available to all users" under my Wireless Connection.  That seems to have done the trick.  Also, would you by chance know how to setup FreeNX so that when I leave a session open at the host I can log into that session instead of a different one?


Thanks for the help!!

---

### Post by CharlesA on 2010-06-26
> **hayhursm said:**
> Yes, you pointed me in the right direction.  I went to System>Preferences>Network Connections and checked "Available to all users" under my Wireless Connection.  That seems to have done the trick.  Also, would you by chance know how to setup FreeNX so that when I leave a session open at the host I can log into that session instead of a different one?


Thanks for the help!!

I don't know, since I've never actually gotten FreeNX to work for me. :( From what I heard, it keep the session alive, but I don't know for sure.

---

### Post by hayhursm on 2010-06-28
> **CharlesA said:**
> I don't know, since I've never actually gotten FreeNX to work for me. :( From what I heard, it keep the session alive, but I don't know for sure.

It took me a lot of trial and error attempts to get FreeNX working so I would be more than happy to help you if you need it?  I think it took me so long because I am still a noob and not familiar with the Linux structure.

---

