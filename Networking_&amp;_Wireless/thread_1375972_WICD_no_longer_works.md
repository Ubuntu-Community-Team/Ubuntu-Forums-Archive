---
title: "WICD no longer works"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by Lokidrakon on 2010-01-08
Hey there. I just updated my system to a new kernel with the update manager and now my WICD no longer obtains an IP address. Everytime I try it says "Connection Failed: Unable to get IP address".
It was working fine before and even when I reboot into an older kernel it still doesn't work.

I'm using a Belking Wireless G adapter.

I would have tried downloading another network manager but since I can't even access the internet I'm stuck with changing current settings and nothing seems to work.

I've been using Ubuntu for a couple years now but I am in no way a guru, so any help will be much obliged. ](*,)

---

### Post by Lokidrakon on 2010-01-08
Anyone?

---

### Post by teward on 2010-01-08
I dont have a solution, but might I make a note to you that this isn't like a chat room, you'll have to wait for responses, and they dont come all the time.

One thought I have though is to purge WICD
in terminal:
```
sudo apt-get purge wicd
```

and reinstall after a reboot
in terminal:
```
sudo apt-get install wicd
```

This will erase your settings though.

---

### Post by Lokidrakon on 2010-01-08
Trying it out now. Though if I can't access the internet at all am I going to be able to reinstall it via the apt-get install?

And sorry about the lack of patience. I'm just very "AHHH!!!" you know?

---

### Post by Lokidrakon on 2010-01-08
It works!!

I love you! Thank you!

---

