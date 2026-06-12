---
title: "Lucid Wireless disconnects for no reason and can't find password"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by deg12 on 2010-05-03
To whom it may concern ;)

When I installed Lucid I got temporary wifi connection. It disconnected for no reason. Then it was constantly trying to reconnect, telling me my password was wrong. Which wasn't wrong at all.

So I installed Lucid again from scratch and now everything seems to work fine. The only thing I didn't do was install the 'restricted drivers'. This was only one driver for me which had to do with my modem. Wifi works perfectly now. I hope it stays that way ;)

In short: reinstall Lucid and DO NOT install the 'restricted drivers' for your modem

---

### Post by Iowan on 2010-05-04
I should file this away in my "mental notes" folder. Although I'm sure some cards will require the 'restricted drivers', it might be worth installing without first - just to see.

---

### Post by smfoote on 2010-05-05
Thanks, I'll try that. Though, I don't remember having the option of installing without restricted drivers when I did install it. I guess we'll see.

---

### Post by fluxley on 2010-05-08
hi
got the same problem , have tried installing again from scratch with the boot cd
and tried upgrading from 9.10 twice now,
but didnt see any options  at all concerning 'restricted drivers'
am i missing something?

---

### Post by boutcher on 2010-05-25
Problem solved for my by:

```
sudo apt-get install linux-backports-modules-wireless-2.6.32-21-generic
```

---

