---
title: "Enable wireless card on a thinpad x200"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by zomgneeks on 2009-05-13
How do I enable my wireless card on a thinkpad x200? It's running Ubuntu 9.04.

I was on the internet, running on battery power, when it stopped. The card came up as disabled when I typed lshw. However, after restarting when I enter lshw the card is not shown.

I'm a beginer if you haven't already noticed.

---

### Post by mojo on 2009-05-25
Hi mate, it could be a bug, or it could be the module is removed somehow. try type in the Terminal

sudo modprobe ath5k

Wait for few seconds and you should see network-manager picks up the signal.

---

### Post by superprash2003 on 2009-05-26
post output of lshw -C network

---

