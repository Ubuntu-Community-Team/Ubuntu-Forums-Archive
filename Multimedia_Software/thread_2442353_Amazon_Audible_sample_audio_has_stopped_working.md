---
title: "Amazon Audible sample audio has stopped working"
date: 2020-05-02
forum: Multimedia Software
---

### Post by ra7411 on 2020-05-02
Amazon Audible has sample clips you can listen to before buying.
That stopped working a couple months ago both in Chrome and Firefox.
As might be expected, asking for tech help resulted in nothing.

Clearing cookies did nothing.
Any ideas?

Thanks

---

### Post by CelticWarrior on 2020-05-02
Working perfectly on mine.

Do you have your system fully updated, namely the browsers?

---

### Post by ra7411 on 2020-05-02
Updated, yes.

---

### Post by CelticWarrior on 2020-05-02
Which Ubuntu release are you running?

---

### Post by ra7411 on 2020-05-02
It doesn't work, just a "loading" circle going around with:
1) Ryzen machine both 18.04 and 20.04 installs.
2) 5 yr old AMD machine 18.04

Does work on Win8 install on 5 yr old AMD machine.

---

### Post by CelticWarrior on 2020-05-02
Either 18.04 and 20.04 are supported.
Assuming they're really updated, i.e., running all the latest browser versions and security patches - just in case perhaps you could run 'sudo apt update && sudo apt full-upgrade' then the problem is on of this two:
[LIST=1]
[*]Some region-based limitation (although if that was the case it wouldn't work in Windows) and/or Amazon/Audible account limitation (I tested it without an Amazon account and a browser profile that never had one)
[*]Something in your user profile in both browsers, something that has been sync'ed everywhere except your Windows or something that installed that isn't standard but common for 18.04 and 20.04, likely codecs or lack thereof.
[/LIST]

---

### Post by DuckHook on 2020-05-02
I don't use Audible, but here are two things to try:

[LIST]
[*]Make sure your browsers are allowing DRM content. In FF at least, it is turned off by default.
[*]Make sure you have *ffmpeg* and *ubuntu-restricted-extras* installed.
[/LIST]

---

### Post by ra7411 on 2020-05-02
>[COLOR=#000000]and/or Amazon/Audible account limitation <

A month ago I described the situation to their tech support, presumably they would know if I was being blocked and would say so, I spend a fair amount of money with Amazon, so, I doubt they would block me.
It's no biggy - thanks all for the replies - I'll just get along without Audible.[/COLOR]

---

### Post by CelticWarrior on 2020-05-02
Why don't you try DuckHook's suggestions first?

---

### Post by ra7411 on 2020-05-02
>[COLOR=#000000]Why don't you try DuckHook's suggestions first?<
I did, and it remained the same problems.[/COLOR]

---

### Post by mc4man on 2020-05-04
I would create a test profile in firefox, launch it and see how things work there.
If you don't know how to create & switch profiles, ask.

---

