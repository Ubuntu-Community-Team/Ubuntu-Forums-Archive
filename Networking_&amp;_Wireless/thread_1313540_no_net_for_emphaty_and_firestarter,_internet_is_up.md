---
title: "no_net for emphaty and firestarter, internet is up"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by wurm on 2009-11-03
i just tried to create an account for empathy and get an error:
NewGoogleTalk; network error.
i did a bit of google and installed firestarter, it gives me the same error-message:
device eth0 is not ready, please check your device settings and make sure your internet-connection is running.

my internet connection is running. whats wrong?

> auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

---

### Post by wurm on 2009-11-05
no one has got an idea or is experiencing this?

---

### Post by wurm on 2009-11-06
come on, give me a hand.
plueeeze.

---

