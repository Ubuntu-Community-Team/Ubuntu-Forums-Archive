---
title: "How to turn a laptop with Kubuntu in an access point?"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by NBPX on 2012-07-10
I have a laptop with Kubuntu. Depending on where I am, if there are some walls between me and the router, I can get the wifi signal relatively well with the laptop, but not with the smartphone.

I was wondering if is possible to transform the laptop into an access point and how. Preferably without the command line.

---

### Post by ciri on 2012-07-10
You can set your network card in [ad-hoc mode]("https://help.ubuntu.com/community/WifiDocs/Adhoc") which will turn it into a host for wireless connections. You'll need two network cards though (since one will be used for the connection to your AP and one to your smartphone). I haven't done this myself on (K)ubuntu yet so I can't help you with the exact configuration, but that is how I would approach your problem.

---

