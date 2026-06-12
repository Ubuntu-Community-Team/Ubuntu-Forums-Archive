---
title: "Internet works randomly (frequent &quot;Server not found messages&quot;)"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by Martificiam on 2012-11-24
The internet works flawlessly on the Windows partition. It's not the case on ubuntu though. 

The strange thing is that the internet sometimes works and sometimes it doesn't - I keep pressing the F5 button over and over and then after about 20 keypresses it would load a webpage. Sometimes it just works.

Tried different browsers, same result.

Trying to run sudo apt-get update or installing any program USUALLY ends up with a "Could not fetch..." error. What should I do to solve this?

What console output should I post?

---

### Post by steeldriver on 2012-11-24
Do you get the same behavior both wired and wireless (assuming you have both)? If so I would suspect an MTU discovery / fragmentation issue

If it's only one or the other then I'd start by looking at your network hardware / drivers

It would be useful to know what your network setup is (router? modem? DSL? cable? other devices on the LAN?)

---

