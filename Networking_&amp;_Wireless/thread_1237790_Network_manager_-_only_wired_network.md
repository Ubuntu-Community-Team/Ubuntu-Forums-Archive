---
title: "Network manager - only wired network"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Zaelle on 2009-08-11
Hi,
I just got an eeepc T91 and I put Ubuntu Netbook Remix on it. I tried to connect to the wifi but network manager only proposes me the wired network, and I have no option to ''scan'' if I find my wifi network. The little LED that signals that wifi is on is on, but it seems like my wifi card isn't activated, it's very strange. (I'm kind of still a newbie about linux and so but my bf knows more about it and he doesn't know what to do, and the problem is like so stupid that we don't really know what to type on gogle to try to find an answer).

I hope it's something basic we missed. We would find ourselves stupid for a moment, but at least it would be simple to fix.

Thanks in advance for your answers

---

### Post by Iowan on 2009-08-12
Wireless seems to be a perpetual challenge... Check results of **ifconfig -a** and **iwconfig**. **lshw -C network** might also reveal some information.

---

### Post by Zaelle on 2009-08-13
Thanks for your answer, but already tried. Not a problem that I can't connect to wifi (maybe it'll come later), it's just that I don't find the checkbox to activate it in networkmanager.... it only tells me that I'm disconnected from the wired network... nothing about wireless

---

### Post by superprash2003 on 2009-08-13
do you get any error like " device not managed" ?

---

### Post by Iowan on 2009-08-13
> **Zaelle said:**
> ...
 Not a problem that I can't connect to wifi (maybe it'll come later), it's just that I don't find the checkbox to activate it in networkmanager.... I guess I'm a li'l thick-headed... Are you trying to connect via wired, or wireless? You won't ahve the option to connect via wireless if the system can't find your wireless card.  **lshw -C network ** will tell if the system knows about your wireless card. If it's configured in */etc/network/interfaces*, Network Manager won't touch it - calling it "unmanaged".

---

