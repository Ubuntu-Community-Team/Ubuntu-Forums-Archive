---
title: "MythWelcome countdown issue (but it does shutdown)"
date: 2012-07-21
forum: Mythbuntu
---

### Post by Leechpool on 2012-07-21
Hi,
Since I've been using mythbuntu 12.04, the mythwelcome countdown nolonger shows 10s increments. I've set the period to 120s. It starts at 120s and stays there for a minute until 60s is shown, then a minute later 0s, waits a bit and then shuts down. It used to show 10s increments. Occasionally it shows 90s (no 60s) then 30s before shutting down. Its like there is a resolution setting somewhere set to 60s not 10s anymore. Can anyone help? I've tried googling but can't find any report of a similar failure.
Thanks.

---

### Post by alien878 on 2012-07-23
I've noticed the same thing.  It seems that mythwelcome now uses a 60s poll of the backend which is quite annoying for me as I have a 30s delay to shutdown.

I couldn't find a way to change it either.  I expect it is hardcoded.

---

### Post by samihs72 on 2012-07-27
Hi! Have you made bug report about this? This is bug indeed... Here is Mythbuntu launchpad link: [https://bugs.launchpad.net/mythbuntu](https://bugs.launchpad.net/mythbuntu)

---

### Post by Leechpool on 2012-07-27
[https://bugs.launchpad.net/mythbuntu/+bug/1029916]("https://bugs.launchpad.net/mythbuntu/+bug/1029916")

My first bug report!

---

