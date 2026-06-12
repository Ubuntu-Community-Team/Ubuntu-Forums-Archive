---
title: "How to reset wired network settings (iptables, etc.) to default"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by srjsbhdi on 2008-12-31
Hi,

I am using the Kubuntu Hardy Heron distro.

I few months ago I was trying to setup internet connection sharing. I had my laptop connected to a WIRED (eth0) modem and wanted to use the built in WIRELESS card (ath0) as a "virtual" wireless router of sorts. This involved fiddling about with the eth0 iptables and what not.

Long story short I ended up destroying my WIRED connection and eventually just purchased a wireless router. My WIRED connection no longer works. I want to have it functional again (without an OS reinstall).

Is there a way to run the original network setup wizard that the UBUNTU installer first used to setup my wired connection? i.e. when I first installed the OS. I want those settings back.

Thanks in advance.

Srj.

---

### Post by teodormircea on 2008-12-31
iptables -F

---

### Post by srjsbhdi on 2009-01-02
Thanks teodormircea,  I'll give that another try ... I don't remember it working last time, but my memory of the event is somewhat foggy.

Srj.

---

### Post by superprash2003 on 2009-01-03
you probably would have messed up iptables.. so you could try flushing iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

