---
title: "Remote only works after stopping and starting lirc"
date: 2010-02-27
forum: Mythbuntu
---

### Post by JohnReid on 2010-02-27
I've had some problems setting up lirc. However I've got it to a state where it sort of works. The only problem is that when I boot up, I need to do

```

sudo service lirc stop
sudo service lirc start

```

and restart the frontend before the remote works. Anybody got any clues as to how I can debug this?

Thanks!
John.

---

### Post by ian dobson on 2010-02-27
Hi,

Sound as if lirc is starting too late/after mythfrontend is up and running.

Can you try getting lirc to start earlier by moving S51lirc to maybe S20lirc

This will get lirc to start abit earlier in the boot sequence.

What tuner/remote are you using? What remote have you configured in lirc?

Regards
Ian Dobson

---

### Post by JohnReid on 2010-02-27
Thanks. I'll try runlevel 2 and let you know how it goes. I have S19lirc though not S51lirc

I've got one of these:
[http://www.amazon.co.uk/Company-MediaGate-GP-IR02BK-Windows-Ultimate/dp/B000W5GK5C](http://www.amazon.co.uk/Company-MediaGate-GP-IR02BK-Windows-Ultimate/dp/B000W5GK5C)

I don't think the tuner is relevant as it didn't come with that. When I test lirc with irw, I get mceusb messages.

---

### Post by JohnReid on 2010-02-27
> **ian dobson said:**
> Can you try getting lirc to start earlier by moving S51lirc to maybe S20lirc

This will get lirc to start abit earlier in the boot sequence.

Actually moving it later from S19lirc to S51lirc fixed the problem.

Thanks,
John.

---

### Post by ian dobson on 2010-02-27
Hi,

Strange I thought S51lirc was the default.
but glad to hear it's working.

Regards
Ian Dobson

---

