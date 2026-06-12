---
title: "gmpc disconnect from mpd"
date: 2009-04-17
forum: Multimedia Software
---

### Post by quackeroni_pizza on 2009-04-17
I am running Ubuntu Intrepid on a client machine running gmpc and Debian 32-bit on a server running mpd. 

Every single time I try to play a music file in gmpc I get disconnected from mpd and nothing plays. I tried increasing timeout times but I still keep disconnecting. However, if I reconnect immediately after the disconnect, the reconnect succeeds and the song starts playing immediately.

The disconnect happens EACH time. Any ideas what could be wrong?

---

### Post by qball on 2009-04-17
try upgrading to latest mpd. 

[https://edge.launchpad.net/~gmpc-trunk/+archive/mpd-trunk](https://edge.launchpad.net/~gmpc-trunk/+archive/mpd-trunk)

And maybe latest gmpc. 

[https://edge.launchpad.net/~gmpc-trunk/+archive/ppa](https://edge.launchpad.net/~gmpc-trunk/+archive/ppa)

I never heard about this problem before.

---

### Post by quackeroni_pizza on 2009-04-19
Yup! That seems to have fixed it... Thanks :P

---

